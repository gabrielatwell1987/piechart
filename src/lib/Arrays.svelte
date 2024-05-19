<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	onMount(() => {
		const data = [10, 20, 30, 40, 50];

		d3.select('body')
			.selectAll('p')
			.data(data)
			.enter()
			.append('p')
			.text((d) => d);
	});
</script>
