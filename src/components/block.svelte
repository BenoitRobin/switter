<script>


    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let author ='';
    let message = '';
    let maxLength = 24;
    $: nbCaracters = message.length;
    $: disabled = message.length > maxLength ? true : false;

    function savedMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: author || 'anonymous',
            date: new Date(),
        }

        dispatch('message', newMessage)

        message = '';
        author= '';

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

    .validation {
        display: flex;
        justify-content: space-between;
        align-items: baseline;

        &-btn {
            width: 25%;
            padding: .5em 0;
            border-radius: 5px;
            background-color:  rgb(156,205,202);
        }

        &-btn:hover {
            background-color: #ff3e00;
            color: #fff;
        }
    }

    .alert {
        color: orangered;
        font-weight: bold;
    }

    .btnAlert {
        color: white;
        width: 25%;
        padding: .5em 0;
        border-radius: 5px;
        background-color: gray;
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
    <input type="text" bind:value={author} placeholder='Your name'>
    <textarea cols="50" rows="5" bind:value={message} placeholder="Write something..."></textarea>
    <div class="validation">
        <div >
            Number of letter(s): <span class:alert={nbCaracters > maxLength}>{nbCaracters}</span>
            {#if disabled}
                <span class="alert">message too long ...</span>
            {/if}
        </div>
        <button on:click={savedMessage} {disabled} class={disabled ? 'btnAlert' : 'validation-btn' }>send</button>
        
    </div>
</main>


<hr />

