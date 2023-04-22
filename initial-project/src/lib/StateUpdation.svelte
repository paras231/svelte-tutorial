<script>
  //  updating objects and arrays is very simple in svelte as compared to react js

  //  handeling objects in svelte->
  const obj = {
    userName: "Paras",
    age: "",
    lang: "Javascript",
  };

  function changeObj() {
    const prop = "Job is developer";
    obj["job"] = prop;
  }
  $: console.log(obj); // use $ to print the updated state.

  //  handeling arrays in svelte->

  let arr = [20, 40, 10, 60, 90, 45];
  //  sort this array->

  const handleSort = () => {
    // we just need to create  a new variable and assing that to old array->
    const newArr = arr.sort((a, b) => {
      return a - b;
    });
    arr = newArr;
  };
  $: console.log(arr);

  //  add new values to the existing array->
  const handleAddMore = () => {
    arr.push(Math.random());
    arr = arr;
  };

  // let's create a dynamic input field generator when user clicks on add more button->

  let userData = [
    {
      name: "",
      age: "",
      number: "",
    },
  ];
  // add field->
  const handleAddMoreField = () => {
    const obj = {
      name: "",
      age: "",
      number: "",
    };
    userData.push(obj);
    userData = userData;
  };
  $: console.log(userData);

  // remove field->
  const handleRemoveField = (index) => {
    userData.splice(index, 1);
    userData = userData;
  };
</script>

<main>
  <h1>State updating and mutating in svelte</h1>
  <strong>
    {obj.userName}
  </strong>
  {#if obj.job === undefined}
    <b>Job property does not exist in the object</b>
  {:else}
    <b>{obj.job}</b>
  {/if}
  {#each arr as num}
    <div>
      {num}
    </div>
  {/each}
  <button on:click={handleSort}> Sort Array </button>
  <button on:click={changeObj}> Change Oject </button>
  <button on:click={handleAddMore}>Add more values</button>
  <div class="input_container">
    {#each userData as input, index}
      <div>
        <input
          type="text"
          placeholder="Enter Your name"
          bind:value={input.name}
        />
        <input type="text" placeholder="Enter age" bind:value={input.age} />
        <input
          type="text"
          placeholder="Enter Number"
          bind:value={input.number}
        />
        <button on:click={handleAddMoreField}>Add more</button>
        <button class="remove_btn" on:click={() => handleRemoveField(index)}>Remove</button>
      </div>
    {/each}
  </div>
</main>

<style>
  .input_container {
    margin-top: 2vh;
  }
  .remove_btn{
    background: crimson;
  }
</style>
