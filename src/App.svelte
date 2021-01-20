<script>
	import Block from './components/block.svelte';
	import List from './components/listMessages.svelte';

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
</style>
	
<!-- Mon code  -->

<main class='container'>

	<Block 
		name = Switter
		author = 'Bob'
		on:message={addMessage}
	/>
	<List messages = {messages} />
</main>

