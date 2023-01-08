<script>
  import Chronometer from "./lib/Chronometer.svelte";
  import Counter from "./lib/Counter.svelte";
  import Header from "./lib/Header.svelte";
  import RandomData from "./lib/RandomData.svelte";

  export let enteredName = "";
  export let isEntered = false;
  export let isEnteredNameValid = undefined;

  window.addEventListener("keydown", (event) => {
    if (event.key == "Enter") enter();
  });

  function enter() {
    if (enteredName != "" && enteredName.length > 1) {
      isEntered = true;
      isEnteredNameValid = true;
    } else isEnteredNameValid = false;
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
      {#if isEnteredNameValid == false}
        <span>Please enter a valid name!</span>
      {/if}
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
  span {
    color: red;
  }
  .card {
    max-width: 400px;
  }
</style>
