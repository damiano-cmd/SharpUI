<script>
  export let options = [];
  export let value;

  export let thm = "";
  export let _class = "";

  function select(index) {
    value = options[index];
  }

  if (options.length > 0) select(0);
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

<div class={"dropdown-sui " + _class}>
  <button 
    class="option-sui"
    class:dark-sui={thm == "dark"}
    class:lite-sui={thm == "lite"}
    >
    {#each Object.keys(value) as i}
      {#if i == "text"}
        {value[i]}
      {/if}
      {#if i == "image"}
        <img src={value[i]} alt="#" />
      {/if}
    {/each}
    <svg
      id="down-sui"
      viewBox="0 0 40 40"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:svg="http://www.w3.org/2000/svg">
      <g>
        <path
          sodipodi:type="star"
          id="path846"
          sodipodi:sides="3"
          sodipodi:cx="54.4631"
          sodipodi:cy="48.226879"
          sodipodi:r1="93.049583"
          sodipodi:r2="45.761784"
          sodipodi:arg1="1.5558721"
          sodipodi:arg2="2.6030696"
          d="M 55.851742,141.2661 15.178115,71.696663 -26.805549,2.9098674 53.780164,2.4701918 134.34311,0.50466975 94.431022,70.513783 Z"
          transform="matrix(0.24816804,0.0030904,-0.00334822,0.22905827,6.6620236,3.4692274)"
        />
      </g>
    </svg>
  </button>
  <div 
    class="options-sui"
    class:dark-sui={thm == "dark"}
    class:lite-sui={thm == "lite"}
    >
    {#each options as i}
      {#if i == "break"}
        <hr />
      {:else}
        <button
          on:click={() => {
            select(options.indexOf(i));
          }}
        >
          {#each Object.keys(i) as e}
            {#if e == "text"}
              {i[e]}
            {/if}
            {#if e == "image"}
              <img src={i[e]} alt="#" />
            {/if}
          {/each}
        </button>
      {/if}
    {/each}
  </div>
</div>

<style>
  .dropdown-sui {
    position: relative;
    margin: 0 8px;
  }
  .option-sui {
    display: flex;
    justify-content: center;
    align-items: center;

    border: none;
    border-radius: 4px;

    padding: 8px 10px;

    min-width: 60px;
    min-height: 2.5rem;
  }
  .option-sui #down-sui {
    width: 0.7rem;
    height: 0.7rem;
    padding: 0 0 0 0.5rem;
  }
  .option-sui:focus + .options-sui {
    display: grid;
  }

  img {
    width: 1.5rem;
    padding: 0 0.3rem;
  }

  .options-sui {
    position: absolute;
    top: calc(100% + .12rem);
    left: 50%;
    transform: translateX(-50%);

    display: none;
    grid-template-columns: 1fr;
    align-items: center;

    min-width: 100%;
    width: max-content;
    max-height: 310px;
    overflow-y: auto;

    border-radius: 4px;
  }
  .options-sui:hover {
    display: grid;
  }
  .options-sui hr {
    border: none;
    height: 1px;
    width: 100%;
  }

  .options-sui button {
    cursor: pointer;

    background: none;
    border: none;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 10px 0.4rem;
    margin: 0;
  }

  .dark-sui {
    background-color: #3a3a3a;
    color: #fff;

    box-shadow: 1px 1px 1px black;
  }

  .dark-sui button {
    color: #fff;
  }

  .dark-sui hr {
    background-color: #a4a4a4;
  }

  .dark-sui svg {
    fill: #fff;
  }

  .lite-sui {
    background-color: #eee;
    color: #242424;

    border: 1px solid #6c6c6c;
  }

  .lite-sui button {
    color: #242424;
  }

  .lite-sui hr {
    background-color: #5b5b5b;
  }

  .lite-sui svg {
    fill: #242424;
  }
</style>
