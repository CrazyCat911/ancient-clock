<script lang="ts">
	import { onMount } from 'svelte';

	let totalslivers = $state(0),
		totalparts = $derived(Math.floor(totalslivers / 1296)),
		totalhours = $derived(Math.floor(totalparts / 144)),
		totaldays = $derived(Math.floor(totalhours / 16));

	onMount(() => {
		setInterval(() => {
			totalslivers += 1;
		}, 3125 / 108);
	});
</script>

<div class="clock">
	days : hours : parts : slivers <br />
	{totaldays}:{totalhours}:{totalparts}:{totalslivers}
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Major+Mono+Display&display=swap');

	.clock {
		font-family: 'Major Mono Display', monospace;
		font-size: 3rem;
		color: #333;
		text-align: center;
		margin-top: 10rem;
	}
</style>
