<script>
  let count = 0;

  const increment = () => {
    count += 1;
  };

  const decrement = () => {
    count -= 1;
  };

  const reset = () => {
    count = 0;
  };
</script>

<div>
  <h1>{count}</h1>
  <button on:click={increment}> increment </button>
  <button on:click={decrement}> decrement</button>

  <button on:click={reset}> reset </button>
</div>

<style>
  div {
    border: 2px solid #888;
    padding: 10px;
    border-radius: 20px;
    transition: 1s;
  }
  div:hover {
    border: 2px solid white;
  }
</style>
