<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let width = 15000;
	let height = 15000;
	let data = [30, 30, 40];
	let r = 300;

	onMount(() => {
		document.body.style.marginLeft = '32.5%';
		document.body.style.marginTop = '5%';

		document.addEventListener('mouseenter', () => {
			let canvas = d3.select('body').append('svg').attr('width', width).attr('height', height);

			let group = canvas.append('g').attr('transform', 'translate(300, 300)');

			let arc = d3.arc().innerRadius(225).outerRadius(r);

			let pie = d3.pie().value((d) => d);

			let arcs = group.selectAll('.arc').data(pie(data)).enter().append('g').attr('class', 'arc');

			arcs
				.append('path')
				.attr('d', arc)
				.attr('fill', (d, i) => {
					let colors = ['#222', '#6A6D46', '#6D4646'];
					return colors[i];
				})
				.transition()
				.duration(2000)
				.attrTween('d', function (d) {
					let i = d3.interpolate(d.startAngle + 0.1, d.endAngle);
					return function (t) {
						d.endAngle = i(t);
						return arc(d);
					};
				});

			arcs
				.append('text')
				.attr('transform', (d) => `translate(${arc.centroid(d)})`)
				.attr('text-anchor', 'middle')
				.attr('font-size', '1.5rem')
				.attr('font-weight', 'bold')
				.attr('fill', 'white')
				.transition()
				.duration(2000)
				.attrTween('transform', function (d) {
					let i = d3.interpolate(d.startAngle + 0.1, d.endAngle);
					return function (t) {
						d.endAngle = i(t);
						return `translate(${arc.centroid(d)})`;
					};
				})
				.text((d) => d.data);
		});

		document.addEventListener('touchstart', () => {
			let canvas = d3.select('body').append('svg').attr('width', width).attr('height', height);

			let group = canvas.append('g').attr('transform', 'translate(300, 300)');

			let arc = d3.arc().innerRadius(225).outerRadius(r);

			let pie = d3.pie().value((d) => d);

			let arcs = group.selectAll('.arc').data(pie(data)).enter().append('g').attr('class', 'arc');

			arcs
				.append('path')
				.attr('d', arc)
				.attr('fill', (d, i) => {
					let colors = ['#222', '#6A6D46', '#6D4646'];
					return colors[i];
				})
				.transition()
				.duration(2000)
				.attrTween('d', function (d) {
					let i = d3.interpolate(d.startAngle + 0.1, d.endAngle);
					return function (t) {
						d.endAngle = i(t);
						return arc(d);
					};
				});

			arcs
				.append('text')
				.attr('transform', (d) => `translate(${arc.centroid(d)})`)
				.attr('text-anchor', 'middle')
				.attr('font-size', '1.5rem')
				.attr('font-weight', 'bold')
				.attr('fill', 'white')
				.transition()
				.duration(2000)
				.attrTween('transform', function (d) {
					let i = d3.interpolate(d.startAngle + 0.1, d.endAngle);
					return function (t) {
						d.endAngle = i(t);
						return `translate(${arc.centroid(d)})`;
					};
				})
				.text((d) => d.data);
		});

		document.addEventListener('mouseleave', () => {
			d3.selectAll('svg').remove();
		});
	});
</script>

<h1>Hover your mouse over</h1>
