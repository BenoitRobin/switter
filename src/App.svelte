<script>
	import Block from './components/block.svelte';
	import List from './components/listMessages.svelte';


    export let name;

	let messages = [
        {
            id: 1609937812087,
            text: ' Bien le bonjour Mr White !',
            author: 'Benoit'
        }
	];
	

	function addMessage (event) {
		let newMessage = event.detail;
		messages = [ newMessage, ...messages]
	}
</script>

<!-- Mon style -->

<style type="text/scss">

.container {
	width: 80%;
	background-color: rgba(156,205,202, .5);
	margin: auto;
	border-radius: 5px;
	padding: 10px;
}
h1 {
		color: #ff3e00;
		text-transform: uppercase;
		text-align: center;
		font-size: 4em;
		font-weight: 100;
	}
</style>
	
<!-- Mon code  -->

<main class='container'>

	<h1>{name}</h1>

	<Block 
		on:message={addMessage}
	/>

	<List 
		{messages}
	/>
</main>

