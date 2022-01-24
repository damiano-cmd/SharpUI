<script>
    export let is_switched;
    export let label;

    export let _class = "";
    export let thm = "";

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

<span 
    class={_class}
    class:dark-sui={thm == "dark"}
    class:lite-sui={thm == "lite"}
>
    <span class="Lb">{label}</span>
    <span>
        <label>
            <input type="checkbox" bind:checked={is_switched}>
            <span class="sw" ></span>
        </label>
    </span>
</span>

<style>
    span {
        display: flex;
        align-items: center;
    }

    span .Lb {
        margin: 0 4px;
    }

    label {
        position: relative;
        
        width: 2.5em;
        height: 1.5em;
        border-radius: 1em;

        margin: 4px;

        box-shadow: 1px 1px 1px black;
    }

    label input {
        opacity: 0;
        width: 0;
        height: 0;
    }
    label input:checked + span::after {
        left: 1.2em;
    }
    label input:checked + span {
        background-color: #00cc00 !important;
    }

    label span {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;

        width: 100%;
        height: 100%;
        border-radius: 1em;
    }

    .dark-sui {
        color: #fff;
    }

    .dark-sui .sw {
        background-color: #3a3a3a;
    }

    .lite-sui {
        color: #242424;
    }

    .lite-sui .sw {
        background-color: #ccc;
    }

    .lite-sui label {
        box-shadow: none;

        border: 1px solid #6c6c6c;
    }

    label span::after {
        position: absolute;
        top: 0.2em;
        left: 0.2em;

        content: "";

        width: 1.1em;
        height: 1.1em;

        background-color: #fff;

        border-radius: 0.55em;

        transition: all .2s ease;
    }
</style>