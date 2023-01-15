<script>
  import { onDestroy } from "svelte";

  let progress = 0;
  let progressColor;

  function getProgressColor(progress) {
    var r = 255;
    var g = Math.round(255 * (1 - progress));
    var b = 0;

    return (progressColor = "rgb(" + r + "," + g + "," + b + ")");
  }

  let intervalId = setInterval(() => {
    progress = (progress + 0.005) % 1;
  }, 10);

  let progressIteration = setInterval(() => {
    getProgressColor(progress);
  }, 10);

  onDestroy(() => clearInterval(intervalId));
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
