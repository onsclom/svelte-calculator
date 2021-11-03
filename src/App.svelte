<script>
	import CalculatorButton from "./CalculatorButton.svelte"
	import CalculatorScreen from "./CalculatorScreen.svelte"
	import { evaluate } from "mathjs"
	
	// logic to handle calculator
	let cur = "0"
	function receivePress(event) {
		if (cur == "ERROR") {
			cur = ""
		}
		let button = event.detail.type
		if (cur=="0" && "123456789".includes(button)) {
			cur = button
		}
		else if (button == "AC") {
			cur = ""
		}
		else if (button == "=") {
			try {
				cur=+evaluate(cur)
			}
			catch {
				cur="ERROR"
			}
		} else {
			cur += button
		}
	}
</script>
<div class="calculator">
	<div class="button-holder">
		<CalculatorScreen text="{cur?cur:"0"}" ></CalculatorScreen>
	<!-- 	row1 -->
		<CalculatorButton name="AC" gridArea="AC" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="/" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="*" on:calcButtonPressed={receivePress}></CalculatorButton>
	<!-- 	row 2 -->
		<CalculatorButton name="7" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="8" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="9" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="-" on:calcButtonPressed={receivePress}></CalculatorButton>
	<!-- 	row 3 -->
		<CalculatorButton name="4" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="5" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="6" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="+" on:calcButtonPressed={receivePress}></CalculatorButton>
	<!-- row 3 -->
		<CalculatorButton name="1" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="2" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="3" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="=" gridArea="EQ" on:calcButtonPressed={receivePress}></CalculatorButton>
	<!-- 	row 4 -->


	<!-- 	<CalculatorButton name="=" gridArea="EQUAL"></CalculatorButton> -->
		<CalculatorButton name="0" gridArea="ZERO" on:calcButtonPressed={receivePress}></CalculatorButton>
		<CalculatorButton name="." on:calcButtonPressed={receivePress}></CalculatorButton>
	</div>
</div>


<style>
	
	.calculator {
		width: 100%;
		max-width: 30rem;
		margin: auto;
		padding: .5rem;
		border: 2px solid black;
		background: rgba(255, 255, 255, 0.726);
	}
	
	.button-holder {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr;
		gap: .5rem .5rem;

		grid-auto-flow: row;
		grid-template-areas:
			"HEADER HEADER HEADER HEADER"
			"AC AC . ."
			". . . ."
			". . . ."
			". . . EQ"
			"ZERO ZERO . EQ";
		aspect-ratio: 4/5;
	}
	
	div {
		font-family: monospace;
		font-size: 2rem;
	}

</style>