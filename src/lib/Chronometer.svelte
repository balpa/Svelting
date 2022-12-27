<script>
  let seconds = 0;
  let chrono;
  let times = [];

  function start() {
    chrono = setInterval(() => {
      seconds += 0.1;
    }, 100);
  }
  function stop() {
    times = [...times, seconds];
    clearInterval(chrono);
    seconds = 0;
  }
  function clearArray() {
    times = [];
  }
</script>

<div>
  <h1>Stopwatch</h1>
  <button on:click={start}> start </button>
  <button on:click={stop}> stop </button>
  <button on:click={clearArray}> clear </button>
  <h1>{seconds.toFixed(1)}</h1>
  {#each times as time, index}
    <p>{index}. time: {time.toFixed(1)} seconds</p>
  {/each}
</div>

<style>
  div {
    border: 2px solid #888;
    border-radius: 15px;
    margin-top: 5px;
    padding: 10px;
    transition: 1s;
  }
  div:hover {
    border: 2px solid white;
  }
</style>
