<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	let data = [
		{ name: 'John', age: 30 },
		{ name: 'Jane', age: 25 },
		{ name: 'Jack', age: 20 }
	];

	onMount(() => {
		barGraph();
	});

	function barGraph() {
		var canvas = d3.select('body').append('svg').attr('width', 500).attr('height', 500);

		canvas
			.selectAll('rect')
			.data(data)
			.enter()
			.append('rect')
			.attr('width', function (d) {
				return d.age * 10;
			})
			.attr('height', 35)
			.attr('y', function (d, i) {
				return i * 50;
			})
			.attr('fill', 'lightblue');

		canvas
			.selectAll('text')
			.data(data)
			.enter()
			.append('text')
			.attr('fill', '#222')
			.attr('y', function (d, i) {
				return i * 50 + 22;
			})
			.attr('font-weight', 900)
			.text(function (d) {
				return d.name;
			});
	}
</script>

<h1>Bar Graph</h1>

<style>
	h1 {
		margin-bottom: 2rem;
	}
</style>
