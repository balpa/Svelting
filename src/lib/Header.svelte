<script>
  import LoadingAnimation from "./LoadingAnimation.svelte";

  export let enteredName;
  let headerTitle = `Hi, ${enteredName.toLowerCase()}!`;
  let latitude = null;
  let longitude = null;

  function getLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition((position) => {
        latitude = position.coords.latitude;
        longitude = position.coords.longitude;
      });
    }
  }
  getLocation();
</script>

<div>
  <h1>{headerTitle}</h1>
  <LoadingAnimation />
  {#if latitude && longitude}
    <h2>Latitude: {latitude},<br />Longitude: {longitude}</h2>
  {/if}
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
