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

<button on:click={increment}> increment </button>
<button on:click={decrement}> decrement</button>

<button on:click={reset}> reset </button>

<h1>{count}</h1>
