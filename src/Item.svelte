<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let item;
    let style = '';

    $: style = item.isComplete ? 'text-decoration: line-through; color:rgb(167, 166, 166);' : '';

    function delete_item(){
        console.log(item.id);
        dispatch('delete_item', {
            id: item.id
        });
    }

    function span_click(){
        item.isComplete = !item.isComplete;
    }
</script>

<div class='item_div'>
    <input type="checkbox" bind:checked="{item.isComplete}">
    <span on:click={span_click} {style}>{item.text}</span>
    <button on:click={delete_item}>x</button>
</div>

<style>
    .item_div{
        display: flex;
        justify-content: space-between;
        font-size: 25px;
        margin-top: 10px;
        margin-bottom: 10px;
    }

    .item_div button{
        border: none;
        background-color: white;
        margin: 0px;
        padding: 0px;
        cursor: pointer;
        color: red;
        padding: 5px;
        margin: -4px 0 0 0;
    }

    .item_div > span {
        width: 100%;
        padding: 0 10px;
        word-break: break-all;
        text-align: left;
    }

    .item_div input[type=checkbox]{
        zoom: 1.5;
        vertical-align: middle;
        margin: -4px 0 0 0;
    }
</style>