<script>
    export let _class = "";

    export let thm = "";
    export let layout = "";
    export let position = "";

    export let grid_temp = 1;
    export let style = "";

    if (style.length > 0 && style[style.length-1] != ";") {
        style += ";";
    }
    if (layout == "grid") {
        style += "grid-template-columns:";
        for (let i = 0; i < grid_temp; i++) {
            style += " 1fr";
        }
        style += ";";
    }

    if (_class != "") {
        if (thm != "" && thm != "dark" && thm != "lite") {
            thm = "dark";
        } 

        if (position != "" && position != "fixed" && position != "sticky") {
            position = "sticky"
        }

        if (layout != "" && layout != "flex" && layout != "grid") {
            layout = "flex"
        }
    } else {
        if (thm != "dark" && thm != "lite") {
            thm = "dark";
        } 

        if (position != "fixed" && position != "sticky") {
            position = "sticky"
        }

        if (layout != "flex" && layout != "grid") {
            layout = "flex"
        }
    }
</script>

<nav 
    class={_class}

    class:dark-sui={thm == "dark"}
    class:lite-sui={thm == "lite"}

    class:grid-layout-sui={layout == "grid"}
    class:flex-layout-sui={layout == "flex"}

    class:pos-fixed-sui={position == "fixed"}
    class:pos-sticky-sui={position == "sticky"}

    style={style}
>
    <slot></slot>
</nav>

<style>
    nav {
        z-index: 9;
        
        top: 0;
        width: 100%;
    }

    .pos-sticky-sui {
        position: sticky;
    }

    .pos-fixed-sui {
        position: fixed;
    }

    .grid-layout-sui {
        display: grid;
        align-items: center;
    }

    .flex-layout-sui {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .dark-sui {
        background-color: #242424;
        color: white;
    }

    .lite-sui {
        background-color: #eee;
        color: #242424;
        
        border-bottom: 1px solid #242424;
    }
</style>
