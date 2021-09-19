<div class="ArrowToggle-comp">
    <img src="../assets/icon-prev.svg" alt="icon-prev" on:click={ () => {onClick(-1)} }>
    <img src="../assets/icon-next.svg" alt="icon-next" on:click={ () => {onClick(1)} }>
</div>

<script>
    import { createEventDispatcher } from "svelte"
    const dispatch = createEventDispatcher()
    const onClick = (dir) => {
        dispatch("arrow-clicked",dir)
    }
</script>

<style>
    .ArrowToggle-comp {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: white;
        width: 80px;
        height: 40px;
        padding: 0 14px;
        border-radius: 30px;
    }
    img {
        width: 10px;
        height: 13px;
        cursor: pointer;
    }
    
</style>