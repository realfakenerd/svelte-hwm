<script>
  import ProgressBar from "./ProgressBar.svelte";
  import {createEventDispatcher} from "svelte"

  const totalSeconds = 20;
  const dispatch = createEventDispatcher()
  let secondsLeft = totalSeconds;
  let isRunning = false;

  $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100;

  function startTimer() {
    isRunning = true;
    const timer = setInterval(() => {
      secondsLeft -= 1;
      if (secondsLeft == 0) {
        clearInterval(timer);
        isRunning = false;
        secondsLeft = totalSeconds;
        dispatch('end')
      }
    }, 1000);
  }
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsLeft}</h2>
</div>

<ProgressBar {progress} />

<div bp="grid">
  <button
    bp="offset-5@md 4@md 12@sm"
    class="start"
    disabled={isRunning}
    on:click={startTimer}>Start</button
  >
</div>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(226, 71, 71);
    margin: 10px 0;
    width: 100%;
    border-radius: 2em;
    padding: 5px;
    font-size: x-large;
  }
  .start[disabled] {
    background-color: #bdbdbd;
    cursor: not-allowed;
  }
  .start:hover {
    background-color: rgb(170, 39, 39);
  }
</style>
