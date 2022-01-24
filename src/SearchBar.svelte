<script>
  import {createEventDispatcher} from "svelte"

  export let _class = "";
  export let thm = "";

  export let value = "";

  let dispatch = createEventDispatcher();
  function search() {
    dispatch("enter", {
      value
    })
  }

  if (_class != "") {
    if (thm != "" && thm != "dark" && thm != "lite") {
      thm = "dark";
    }
  } else {
    if (thm != "dark" && thm != "lite") {
      thm = "dark";
    }
  }
</script>

<form
  class={_class}
  class:dark-sui={thm == "dark"}
  class:lite-sui={thm == "lite"}

  on:submit={search}
>
  <input type="text" placeholder="Search" bind:value={value} />
  <button>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      ><path
        d="M10 18a7.952 7.952 0 0 0 4.897-1.688l4.396 4.396 1.414-1.414-4.396-4.396A7.952 7.952 0 0 0 18 10c0-4.411-3.589-8-8-8s-8 3.589-8 8 3.589 8 8 8zm0-14c3.309 0 6 2.691 6 6s-2.691 6-6 6-6-2.691-6-6 2.691-6 6-6z"
      /></svg
    >
  </button>
</form>

<style>
  form {
    width: min-content;
    display: flex;
    align-items: center;

    padding: 0.2rem .5rem;
    margin: 0 16px;
    border-radius: 0.2rem;
  }

  form input, form button {
    border: none;
    outline: none;
    background-color: rgba(0, 0, 0, 0);
  }

  form input {
    width: 350px;
  }

  form button {
    height: 2rem;
    width: 2rem;
    padding: 0;
  }

  form button svg {
    width: 100%;
    height: 100%;
  }

  .dark-sui {
    background-color: #3a3a3a;
    color: white;

    box-shadow: 
      1px 1px 1px black
    ;
  }
  .dark-sui svg {
    fill: white;
  }
  .dark-sui input {
    color: #fff;
  }

  .lite-sui {
    background-color: white;
    color: #242424;

    border: 1px solid #6c6c6c;
  }
  .lite-sui svg {
    fill: #242424;
  }
  .lite-sui input {
    color: #242424;
  }
</style>
