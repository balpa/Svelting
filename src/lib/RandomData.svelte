<script>
  const API_URL = "https://random-data-api.com/api/v2/";

  let choosenCategory = "";
  let showChoosenCategory = "";
  let fetchedData;

  function handleChoosenCategory(e) {
    choosenCategory = e.target.innerHTML;
  }

  async function fetchData() {
    if (choosenCategory != "") {
      await fetch(
        `${API_URL}${choosenCategory.toLowerCase().replace(" ", "_")}`
      )
        .then((res) => res.json())
        .then((data) => {
          fetchedData = data;
          showChoosenCategory = choosenCategory;
        });
    }
  }
</script>

<main>
  <div>
    <div id="button-container">
      <button on:click={(e) => handleChoosenCategory(e)}>Users</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Addresses</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Banks</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Appliances</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Beers</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Blood Types</button>
      <button on:click={(e) => handleChoosenCategory(e)}>Credit Cards</button>
    </div>
    <button on:click={fetchData}>Fetch</button>

    {#if fetchedData !== undefined}
      <p>Showing random {showChoosenCategory}</p>
      <div id="data-section">
        <pre>{@html JSON.stringify(fetchedData, null, 2)}</pre>
      </div>
    {/if}
  </div>
</main>

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
  #button-container {
    display: flex;
    overflow-x: auto;
    border: none;
  }
  button {
    margin: 3px;
    height: 50px;
    text-align: center;
    white-space: nowrap;
  }

  pre {
    white-space: pre-wrap;
    word-break: break-all;
  }
</style>
