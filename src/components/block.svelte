<script>
    export let name;
    let message = '';
    export let messages = [
        {
            id: 1609937812087,
            text: ' Bien le bonjour Mr White !',
            author: 'Benoit'
        }
    ];
    
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

    hr {
        width: 50%;
    }
    .display {
        width: 60%;
        margin: 20px auto;
        background-color: #fff;
        padding: 1em;
        border-radius: 10px;

        &-tab {
            background-color: rgb(156,205,202);
            padding: 1em;
            border-radius: 5px;

            &--item {
                list-style: none;
                font-size: 1rem;
                font-weight: 600;
            }

            &--message {
                padding-top: 1em;
                padding-left: 2em;
                font-size: 1.5rem;
                color: white;
                text-transform: none;
                font-weight: 300;
            }
        }

    } 
</style>
	
<!-- Mon code  -->

<main class="main">
	<h1>{name}</h1>
    <textarea cols="50" rows="5" on:input={updateMessage} placeholder="Write something..."></textarea>
</main>

<button on:click={savedMessage}>send</button>

<hr />

<section class='display'>
    <h2>Messages : </h2>
    <div class="display-tab">
        {#each messages as message}

        <li class="display-tab--item">
            {message.author} - <span class="date">{message.id}</span>  :
            <div class="display-tab--message">{message.text}</div>
        </li>
        <br>
        {/each}
    </div>
</section>    