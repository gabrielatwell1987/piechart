<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		var data = {
			'0': {
				country: 'Brazil',
				titles: 5
			},
			'1': {
				country: 'Germany',
				titles: 4
			},
			'2': {
				country: 'Italy',
				titles: 4
			},
			'3': {
				country: 'Argentina',
				titles: 2
			},
			'4': {
				country: 'Uruguay',
				titles: 2
			},
			'5': {
				country: 'France',
				titles: 2
			},
			'6': {
				country: 'England',
				titles: 1
			},
			'7': {
				country: 'Spain',
				titles: 1
			}
		};
		data = Object.values(data);

		var containerWidth = +d3.select('#container').attr('width');
		var containerHeight = +d3.select('#container').attr('height');
		var margin = { top: 20, bottom: 20, left: 60, right: 10 };
		var width = containerWidth - margin.left - margin.right;
		var height = containerHeight - margin.top - margin.bottom;

		var x = d3.scaleLinear().range([0, width]);
		var y = d3.scaleBand().range([height, 0]).padding(0.1);

		var svg = d3
			.select('#container')
			.append('svg')
			.attr('id', 'svg')
			.attr('width', containerWidth)
			.attr('height', containerWidth);

		x.domain([
			0,
			d3.max(data, (d) => {
				return d.titles;
			})
		]);

		y.domain(
			data.map((d) => {
				return d.country;
			})
		);

		var bars = svg
			.append('g')
			.attr('id', 'barGroup')
			.attr('class', 'bars group')
			.attr('transform', `translate(${margin.left}, ${0})`);
		bars
			.selectAll('rect')
			.data(data)
			.enter()
			.append('rect')
			.attr('class', 'bar')
			.attr('x', x(0))
			.attr('y', function (d) {
				return y(d.country);
			})
			.attr('width', function (d) {
				return x(d.titles);
			})
			.attr('height', y.bandwidth())
			.attr('fill', '#A34343');

		var axisGroup = svg
			.append('g')
			.attr('id', 'axisGroup')
			.attr('transform', `translate(${margin.left}, ${0})`);
		var xAxisGroup = axisGroup
			.append('g')
			.attr('id', 'xAxisGroup')
			.attr('class', 'axis x axisGroup')
			.attr('transform', `translate(${0}, ${height})`);
		var yAxisGroup = axisGroup
			.append('g')
			.attr('id', 'yAxisGroup')
			.attr('class', 'axis y axisGroup');

		xAxisGroup.call(d3.axisBottom(x)).select('.domain').remove();
		yAxisGroup.call(d3.axisLeft(y));
	});
</script>

<svelte:head>
	<title>World Cup Winners</title>
</svelte:head>

<div id="container" width="800" height="500"></div>
