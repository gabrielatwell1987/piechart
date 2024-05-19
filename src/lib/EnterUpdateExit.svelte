<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		var data = [10];

		var canvas = d3.select('body').append('svg').attr('width', 500).attr('height', 500);

		var circle1 = canvas.append('circle').attr('cx', 125).attr('cy', 125).attr('r', 50);

		var circle2 = canvas.append('circle').attr('cx', 300).attr('cy', 300).attr('r', 50);

		var circles = canvas
			.selectAll('circle')
			.data(data)
			// .attr('fill', 'blue')
			// .enter()
			// .append('circle')
			// .attr('cx', 50)
			// .attr('cy', 50)
			// .attr('r', 25)
			// .attr('fill', 'red');
			.attr('fill', 'green')
			.exit()
			.attr('fill', 'blue');
	});
</script>
