<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let input_this;
    let input_val = '';

    function add_list(){
        dispatch('add_list', {
            text: input_val
        });
        input_val = '';
    }

    function clear_list(){
        dispatch('clear_list', {});
    }

    function keydown_event(event){
        if(event.keyCode === 13) add_list();
    }
</script>

<div class='input_div'>
    <input type="text" placeholder="할 일을 입력해주세요" bind:value={input_val} on:keydown={keydown_event} bind:this={input_this}/>
    <button on:click={add_list}>ADD</button>
    <button on:click={clear_list}>CLEAR</button>
</div>

<style>
    .input_div{
        display: flex;
    }

    .input_div input{
        flex-grow: 1;
        border-radius: 25px;
		box-shadow: 0px 0px 10px 5px rgb(233, 233, 233);
        border: none;
        font-size: 20px;
    }

    .input_div input::placeholder{
        color:rgb(180, 180, 180);
    }

    .input_div button{
        background-color: rgb(89, 66, 189);
        color: white;
        padding: 0px 15px;
        border-radius: 25px;
		box-shadow: 10px 10px 10px rgb(233, 233, 233);
        border: none;
        cursor: pointer;
        margin-left: 5px;
    }
</style>