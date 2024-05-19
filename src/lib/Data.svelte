<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		let dataArray = [20, 40, 50];

		let canvas = d3.select('body').append('svg').attr('width', 500).attr('height', 500);

		let bars = canvas
			.selectAll('rect')
			.data(dataArray)
			.enter()
			.append('rect')
			.attr('fill', '#222')
			.attr('width', function (d) {
				return d * 10;
			})
			.attr('height', 50)
			.attr('y', function (d, i) {
				return i * 100;
			});

		d3.json('data.json').then((data) => {
			Object.values(data).forEach((d) => {
				console.log(data);
			});
		});

		d3.csv('data.csv').then((data) => {
			console.log(data);
		});

		d3.tsv('data.tsv').then((data) => {
			data.forEach((d) => {
				console.log(d);
			});
		});

		d3.xml('data.xml').then((data) => {
			data.documentElement.querySelectorAll('row').forEach((d) => {
				console.log(d);
			});
		});
	});
</script>
