<script>
  import { onDestroy } from "svelte";

  let progress = 0;

  function getProgressColor(progress) {
    var r = 255;
    var g = Math.round(255 * (1 - progress));
    var b = 0;
    console.log("rgb(" + r + "," + g + "," + b + ")");
    return "rgb(" + r + "," + g + "," + b + ")";
  }

  let intervalId = setInterval(() => {
    progress = (progress + 0.01) % 1;
  }, 10);

  onDestroy(() => clearInterval(intervalId));
  export let progressColor = getProgressColor(progress);
</script>

<div class="loading-bar-container">
  <div
    class="loading-bar"
    style="width: 100%; background-color: {progressColor}"
  />
</div>

<style>
  .loading-bar-container {
    width: 100%;
    height: 20px;
  }

  .loading-bar {
    height: 100%;
    transition: width 0.5s linear;
  }
</style>
