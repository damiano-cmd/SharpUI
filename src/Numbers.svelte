<script>
  export let showing = 5;
  export let curent = 0;
  export let maximum = 8;

  export let thm = "";
  export let _class = "";

  let numbers_array = [];

  $: [showing, curent, maximum] && generateNumbersArray();
  function generateNumbersArray() {
    numbers_array = [];

    if (showing >= maximum) {
      showing = maximum-1;
    }

    if (curent < 0) {
      curent = 0;
    }

    let on_side = parseInt(showing / 2);
    let from = curent - on_side;

    if (curent + on_side >= maximum) {
      from -= curent + on_side - maximum;
      from -= 1;
    }

    if (from < 0) {
      from = 0;
    }

    for (let i = 0; i < showing; i++) {
      if (i + from < maximum) {
        numbers_array.push(i + from);
      }
    }
  }

  function move(index) {
    if (index < 0 || index + curent == 0) {
      curent = maximum - 1;
    } else if (
      index >= maximum ||
      (index == maximum - 1 && curent == maximum - 1)
    ) {
      curent = 0;
    } else {
      curent = index;
    }
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

<div
  class={_class}

  class:dark-sui={thm == "dark"}
  class:lite-sui={thm == "lite"}
>
  <button
    on:click={() => {
      move(0);
    }}>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
        <path d="m12.707 7.707-1.414-1.414L5.586 12l5.707 5.707 1.414-1.414L8.414 12z"></path>
        <path d="M16.293 6.293 10.586 12l5.707 5.707 1.414-1.414L13.414 12l4.293-4.293z"></path>
      </svg>
    </button
  >
  <button
    on:click={() => {
      move(curent - 1);
    }}>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
        <path d="M13.293 6.293 7.586 12l5.707 5.707 1.414-1.414L10.414 12l4.293-4.293z"></path>
      </svg>
    </button
  >
  {#each numbers_array as i}
    <button on:click={() => (curent = i)} class:selected={curent == i}>
      {i + 1}
    </button>
  {/each}
  <button
    on:click={() => {
      move(curent + 1);
    }}>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
        <path 
          d="M10.707 17.707 16.414 12l-5.707-5.707-1.414 1.414L13.586 12l-4.293 4.293z">
        </path>
      </svg>
    </button
  >
  <button
    on:click={() => {
      move(maximum - 1);
    }}>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
        <path d="M10.296 7.71 14.621 12l-4.325 4.29 1.408 1.42L17.461 12l-5.757-5.71z"></path>
        <path d="M6.704 6.29 5.296 7.71 9.621 12l-4.325 4.29 1.408 1.42L12.461 12z"></path>
      </svg>
    </button
  >
</div>

<style>
  div {
    display: flex;

    padding: 1rem;
  }
  button {
    border: none;
    background: none;

    border-radius: 50%;

    width: 2.2rem;
    height: 2.2rem;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  
  svg {
    width: 2.5rem;
    height: 2.5rem;
  }


  .dark-sui {
    color: #fff;
  }
  .dark-sui .selected {
    background-color: #3a3a3a;
  }
  .dark-sui svg {
    fill: #fff;
  }
  .dark-sui button:hover {
    background-color: #3a3a3aa0;
  }
  .dark-sui button {
    color: #fff;
  }


  .lite-sui {
    color: #242424;
  }
  .lite-sui .selected {
    background-color: #c0c0c0;
  }
  .lite-sui svg {
    fill: #242424;
  }
  .lite-sui button:hover {
    background-color: #c0c0c0a0;
  }
  .lite-sui button {
    color: #242424;
  }
</style>
