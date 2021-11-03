<script>
	export let text = "0"
</script>

<div class="calc-button" style="grid-area: HEADER">
	<p>{text}</p>
</div>

<style>
	.calc-button {
		overflow: hidden;
		display: flex;
		text-align: center;
		border: 2px solid black;
	}
	.calc-button p {
		box-sizing: border-box;
		width: 100%;
		margin: auto 1rem;
		text-align: right;
	}
</style>