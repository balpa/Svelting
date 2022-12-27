<script>
  let seconds = 0;
  let chrono;

  function start() {
    chrono = setInterval(() => {
      seconds += 0.1;
    }, 100);
  }
  function stop() {
    clearInterval(chrono);
    seconds = 0;
  }
</script>

<div>
  <h1>Stopwatch</h1>
  <button on:click={start}> start </button>
  <button on:click={stop}> stop </button>
  <h1>{seconds.toFixed(1)}</h1>
</div>
