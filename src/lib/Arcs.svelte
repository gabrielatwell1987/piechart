<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	let width = 900;
	let height = 900;
	let r = 100;
	let p = Math.PI / 2;

	onMount(() => {
		document.body.style.marginLeft = '5%';
		document.body.style.marginTop = '5%';

		let canvas = d3.select('body').append('svg').attr('width', width).attr('height', height);

		let group = canvas.append('g').attr('transform', 'translate(100,100)');

		let arc = d3
			.arc()
			.innerRadius(r - 20)
			.outerRadius(r)
			.startAngle(0)
			.endAngle(p * 4);

		group.append('path').attr('d', arc);
	});
</script>
