<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	export let name = ""
	export let gridArea = "auto"
	
	function calcButtonPressed() {
		dispatch('calcButtonPressed', {
			type: name
		});
	}

</script>

<div class="calc-button" style="grid-area: {gridArea}" on:click={calcButtonPressed}>
	<p>
		{name}
	</p>
</div>

<style>
	.calc-button {
		display: flex;
		text-align: center;
		border: 2px solid black;
		-webkit-box-shadow: 4px 4px 0px 0px #000000; 
		box-shadow: 4px 4px 0px 0px #000000;
		cursor: pointer;
		user-select: none;
		-moz-user-select: none;
		-khtml-user-select: none;
		-webkit-user-select: none;
		-o-user-select: none;
	}
	.calc-button p {
		margin: auto;
	}
	.calc-button:active {
		transform: translate(4px, 4px);
		-webkit-box-shadow: 0 0 0 0; 
		box-shadow: 0 0 0 0; 
	}
</style>