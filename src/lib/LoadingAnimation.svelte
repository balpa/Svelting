<script>
  let loadingBars;
  console.log(loadingBars);
</script>

<div id="loading-container">
  <div class="loading-bar" bind:this={loadingBars}>1</div>
  <div class="loading-bar">2</div>
  <div class="loading-bar">3</div>
  <div class="loading-bar">4</div>
  <div class="loading-bar">5</div>
  <div class="loading-bar">6</div>
  <div class="loading-bar">7</div>
  <div class="loading-bar">8</div>
  <div class="loading-bar">9</div>
  <div class="loading-bar">10</div>
</div>

<style>
  #loading-container {
    width: 40px;
    height: 70px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
  }
  .loading-bar {
    width: 100%;
    height: 3px;
    background-color: white;
    border-radius: 5px;
  }
</style>
