<script>

    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    export let name;
    export let author;
    let message = '';
   

    function savedMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: author 
        }

        dispatch('message', newMessage)

        message = '';

    }

</script>

<!-- Mon style -->

<style type="text/scss">
	.main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;

        width: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

    .btn {
        width: 25%;
        align-self: flex-end;
        padding: .5em 0;
        border-radius: 5px;
        background-color:  rgb(156,205,202);
    }

    .btn:hover {
        background-color: #ff3e00;
        color: #fff;
    }
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}


    hr {
        width: 50%;
    }

</style>
	
<!-- Mon code  -->

<main class="main">
	<h1>{name}</h1>
    <textarea cols="50" rows="5" bind:value={message} placeholder="Write something..."></textarea>
    <button on:click={savedMessage} class="btn">send</button>
</main>


<hr />

