<script>
    export let messages;
</script>



<style type="text/scss">
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