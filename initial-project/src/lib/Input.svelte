<script>
  export let inputProp;
  
  let name = "";

  let loading = false;

  const changeLoading = () => {
    loading = !loading;
  };

  let marked = false;
  let selected1 = "test";
  let selected2 = "test2";
</script>

<main>
  HELLOW WORLD

  <div>
    <input bind:value={name} type="text" placeholder="Enter name" />
  </div>
  <h3>{name}</h3>
  <button on:click={changeLoading}> Change Loading </button>
  <div>
    {#if loading}
      <h4>Loading is true</h4>
    {:else}
      <h4>Loading is false</h4>
    {/if}
  </div>
  <!-- handeling checkbox -->
  <div>
    <!-- checkbox always takes boolean -->
    <input type="checkbox" bind:checked={marked} />
    {#if marked}
      <h2>Marked is true</h2>
    {:else}
      <h2>Marked is false</h2>
    {/if}
  </div>
  <!-- handeling radio buttons -->
  <div>
    <input
      type="radio"
      group={selected1}
      name="selected"
      value="first is selected"
    />
    <input
      type="radio"
      group={selected2}
      name="selected"
      value="2nd selected"
    />
    <h3>{selected1}</h3>
  </div>
  <div>
    <h3>{inputProp}</h3>
  </div>
</main>

<style>
  input {
    height: 3vmax;
    padding-left: 10px;
    margin-top: 3vh;
  }
</style>
