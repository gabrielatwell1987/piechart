<script>
	import data from '../data/data.js';
	import { scaleLinear } from 'd3-scale';
	import { max } from 'd3-array';
	import AxisX from '$lib/AxisX.svelte';
	import AxisY from '$lib/AxisY.svelte';
	import Tooltip from '$lib/Tooltip.svelte';

	let width = 400;
	let height = 400;

	const margin = { top: 20, right: 40, left: 0, bottom: 20 };

	$: xScale = scaleLinear()
		.domain([0, 100])
		.range([0, width - margin.left - margin.right]);

	const yScale = scaleLinear()
		.domain([0, max(data, (d) => d.hours)])
		.range([height - margin.top - margin.bottom, 0]);

	let hoveredData;
	$: console.log(hoveredData);
</script>

<svelte:head>
	<title>Scatterplot Chart</title>
</svelte:head>

<h1>Random people who study..</h1>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
	class="chart-container"
	bind:clientWidth={width}
	on:mouseleave={() => {
		hoveredData = null;
	}}
>
	<svg {width} {height}>
		<AxisX {height} {xScale} {margin} />
		<AxisY {height} {width} {yScale} {margin} />
		<g class="circles" transform="translate({margin.left} {margin.top})">
			{#each data.sort((a, b) => a.grade - b.grade) as student}
				<circle
					cx={xScale(student.grade)}
					cy={yScale(student.hours)}
					r={hoveredData && hoveredData == student ? '20' : '10'}
					opacity={hoveredData ? (hoveredData == student ? '1' : '.3') : '1'}
					fill="darkred"
					stroke="black"
					on:mouseover={() => {
						hoveredData = student;
					}}
					on:focus={() => {
						hoveredData = student;
					}}
					tabIndex="0"
				/>
			{/each}
		</g>
	</svg>
	{#if hoveredData}
		<Tooltip data={hoveredData} {xScale} {yScale} />
	{/if}
</div>

<style>
	circle {
		transition:
			r 300ms ease,
			opacity 300ms ease;
		cursor: pointer;
	}

	circle:focus {
		outline: none;
	}

	h1 {
		font-size: 1.5rem;
		font-weight: 900;
		margin-bottom: 0.5rem;
		letter-spacing: 10px;
	}

	.chart-container {
		margin-top: 15%;
	}
</style>
