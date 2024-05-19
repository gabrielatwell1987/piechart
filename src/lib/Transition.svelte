<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		document.body.style.marginTop = '5%';

		var data = [10];

		var canvas = d3.select('body').append('svg').attr('width', 500).attr('height', 500);

		var circle = canvas.append('circle').attr('cx', 50).attr('cy', 50).attr('r', 25);

		circle
			.transition()
			.duration(2000)
			.attr('cx', 400)
			.transition()
			.attr('cy', 400)
			.transition()
			.attr('cx', 35)
			.transition()
			.attr('stroke', 'red')
			.attr('stroke-width', 5);
		// .each('end', function () {
		// 	d3.select(this).attr('fill', 'red');
		// });
	});
</script>
