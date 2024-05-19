<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		let canvas = d3.select('body').append('svg').attr('width', 700).attr('height', 800);

		// let circle = canvas
		// 	.append('circle')
		// 	.attr('cx', 250)
		// 	.attr('cy', 100)
		// 	.attr('r', 50)
		// 	.attr('fill', 'red');

		// let rect = canvas
		// 	.append('rect')
		// 	.attr('width', 200)
		// 	.attr('height', 75)
		// 	.attr('rx', 10)
		// 	.attr('ry', 10)
		// 	.attr('fill', 'lightblue');

		// let line = canvas
		// 	.append('line')
		// 	.attr('x1', 0)
		// 	.attr('y1', 300)
		// 	.attr('x2', 500)
		// 	.attr('y2', 500)
		// 	.attr('stroke', 'green')
		// 	.attr('stroke-width', 10);

		// let ellipse = canvas
		// 	.append('ellipse')
		// 	.attr('cx', 300)
		// 	.attr('cy', 300)
		// 	.attr('rx', 100)
		// 	.attr('ry', 50)
		// 	.attr('fill', 'yellow');

		let polygon = canvas
			.append('polygon')
			.attr('points', '0,30 50,0 100,30 75,75 25,75')
			.attr('fill', 'purple');

		// let polyline = canvas
		// 	.append('polyline')
		// 	.attr('points', '50,300 300,300 500,500 75,75 25,75')
		// 	.attr('fill', 'none')
		// 	.attr('stroke', '#ccc')
		// 	.attr('stroke-width', 15);

		let path = canvas
			.append('path')
			.attr('d', 'M 100 100 L 300 100 L 200 300 z')
			.attr('fill', 'none')
			.attr('stroke', '#1778AE')
			.attr('stroke-width', 5);

		let text = canvas
			.append('text')
			.text('Chelloskis!')
			.attr('x', 1)
			.attr('y', 400)
			.attr('font-family', 'san-serif')
			.attr('letter-spacing', 25)
			.attr('font-size', 50)
			.attr('font-weight', '900')
			.attr('fill', 'gray');
	});
</script>

<style></style>
