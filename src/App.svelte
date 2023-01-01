<script>
  import Chronometer from "./lib/Chronometer.svelte";
  import Counter from "./lib/Counter.svelte";
  import Header from "./lib/Header.svelte";
  import RandomData from "./lib/RandomData.svelte";

  export let enteredName = "";
  export let isEntered = false;

  function enter() {
    isEntered = true;
  }
  function handleInputOnchange(target) {
    enteredName = target.value;
  }
</script>

<main>
  {#if !isEntered}
    <div class="enterance">
      <input
        type="text"
        value={enteredName}
        id="name-input"
        placeholder="Enter name"
        on:change={(e) => handleInputOnchange(e.target)}
      />
      <button on:click={enter}>Enter</button>
    </div>
  {/if}

  {#if isEntered}
    <div class="card">
      <Header {enteredName} />
      <Counter />
      <Chronometer />
      <RandomData />
    </div>
  {/if}
</main>

<style>
  .enterance {
    display: flex;
    flex-direction: column;
  }
  button {
    margin-top: 10px;
  }
</style>
