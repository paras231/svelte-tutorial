<script>
  import { onMount } from "svelte";
  import axios from "axios";

  let users = [];

  onMount(async () => {
    const { data } = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );
    users = data;
  });
</script>

<main>
  {#each users as user}
    <div>
      {user.name}
    </div>
  {/each}
</main>

<style></style>
