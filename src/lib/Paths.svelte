<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	let width = 500;
	let height = 500;
	let data = [
		{ x: 3.00478, y: 4.96008 },
		{ x: 285.638, y: 2.49507 },
		{ x: 147.073, y: 248.843 },
		{ x: 3.00478, y: 4.96008 }
	];
	let line = d3
		.line()
		.x((d) => d.x)
		.y((d) => d.y);

	onMount(() => {
		let canvas = d3.select('body').append('svg').attr('width', width).attr('height', height);

		let group = canvas.append('g').attr('transform', 'translate(100,100)');

		group
			.selectAll('path')
			.data([data])
			.enter()
			.append('path')
			.attr('d', line)
			.attr('fill', '#ccc')
			.attr('stroke', 'black')
			.attr('stroke-width', 10);
	});
</script>

<h1>SVG Paths</h1>

<style>
	h1 {
		font-size: 3rem;
		text-align: center;
		font-weight: 800;
		letter-spacing: 10px;
	}
</style>
