<script>
//Slot is a way to pass data into a component
export let type="primary";
export let flat = false;
export let inverse = false;

</script>

<button class={type} class:flat={flat} class:inverse={inverse}>
    <slot></slot>
</button>

<style>
    button{
        border:0;
        cursor:pointer;
        border-radius:6px;
        padding:8px 12px;
        font-weight:bold;
        box-shadow:1px 2px 3px rgba(0,0,0,0.4);
    }
    .primary{
        background:crimson;
        color:white;
    }
    .secondary{
        background-color: #45c496;
        color:white;
    }
    .flat{
        box-shadow:none;
    }
    .primary.inverse{
        background-color: white;
        color:crimson;
    }
    .secondary.inverse{
        background-color: #fff;
        color:crimson;
    }
</style>