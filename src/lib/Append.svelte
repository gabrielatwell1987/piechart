<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		d3.select('body').append('h1').style('color', '#ddd').text('SVGs are cool!');
	});
</script>
