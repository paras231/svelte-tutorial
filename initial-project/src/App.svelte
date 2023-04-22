<script>
  // import svelteLogo from "./assets/svelte.svg";
  import Counter from "./lib/Counter.svelte";
  import Input from "./lib/Input.svelte";
  import Dynamicdata from "./lib/Dynamicdata.svelte";
  const objProps = {
    name: "input",
    type: "radio,checkboxes,select",
  };
</script>

<main>
  <div class="card">
    <Counter />
    <Input inputProp="props passed to input component" />
    <Dynamicdata />
  </div>
</main>

<style>
</style>
