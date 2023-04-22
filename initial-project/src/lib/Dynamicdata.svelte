<script>
  import { onMount } from "svelte";
  import axios from "axios";
  let loading = false;
  let users = [];
  const fetchData = async () => {
    try {
      loading = true;
      const { data } = await axios.get(
        "https://jsonplaceholder.typicode.com/users"
      );
      users = data;
      loading = false;
    } catch (error) {
      loading = loading;
      console.log(error);
    }
  };

  onMount(fetchData);
</script>

<main>
  {#if loading}
    <h2>Loading...</h2>
  {:else}
    {#each users as user}
      <div>
        {user.name}
      </div>
    {/each}
  {/if}
</main>

<style></style>
