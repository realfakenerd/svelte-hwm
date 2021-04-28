<script>
	import Timer from "./Timer.svelte";
	import HowTo from "./HowTo.svelte";

	function timeEnded(e){
		console.log(e)
	}
</script>

<style>
	h1, h3{
		text-align: center;
	}
	
</style>

<h1>Handwashing Machine</h1>

<Timer on:end={timeEnded}/>

<HowTo />

<footer>
	<h3>
		<a href="https://who.int/gpsc/clean_hands_protection/en">Picture Source</a>
		<a href="https://freesound.org/people/metrostock99/sounds/345086/">Sound Source</a>
	</h3>
</footer>