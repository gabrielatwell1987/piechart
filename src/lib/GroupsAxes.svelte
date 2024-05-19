<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		let dataArray = [5, 40, 50, 60];
		var width = 500;
		var height = 500;

		var widthScale = d3.scaleLinear().domain([0, 60]).range([0, width]);
		var colorScale = d3.scaleLinear().domain([0, 60]).range(['#000', '#666']);

		var axis = d3.axisBottom(widthScale).ticks(5);

		let canvas = d3
			.select('body')
			.append('svg')
			.attr('width', width)
			.attr('height', height)
			.append('g')
			.attr('transform', 'translate(20, 0)');

		let bars = canvas
			.selectAll('rect')
			.data(dataArray)
			.enter()
			.append('rect')
			.attr('fill', function (d) {
				return colorScale(d);
			})
			.attr('width', function (d) {
				return widthScale(d);
			})
			.attr('height', 50)
			.attr('y', function (d, i) {
				return i * 100;
			});

		canvas.append('g').attr('transform', 'translate(0, 400)').call(axis);
	});
</script>
