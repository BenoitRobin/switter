<script>
    export let name;
    let message = '';
    export let messages = [];
    
    function updateMessage(event) {
        // console.log(event.target.value);
        message = event.target.value;
    }

    function savedMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: 'Sam' 
        }

        messages = [newMessage, ...messages];
        console.log('Mes messages : ', messages); 

        message = '';

    }
</script>

<!-- Mon style -->

<style type="text/scss">
	.main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
	
<!-- Mon code  -->

<main class="main">
	<h1>{name}</h1>
    <textarea cols="50" rows="5" on:input={updateMessage}></textarea>
</main>

<button on:click={savedMessage}>send</button>

<hr />

<section class='display'>
    <h2>Messages : </h2>
    <div class="display-tab">
        {#each messages as message}

        <li>
            {message.author} / {message.id} :
            <div>{message.text}</div>
        </li>
        <br>
        {/each}
    </div>
</section>    