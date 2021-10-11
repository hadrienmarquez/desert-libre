<script>
    import { goto } from '$app/navigation';
    export let posts;  

</script>

<main>
    <ul>
        {#each posts as {path, metadata: {title, date}}}
            <li on:click={() => {goto(`/${path.replace(".md","")}`)}}>
                    <h5>
                        {title}
                    </h5>
                    <p class="small">{new Date(date).toLocaleDateString("fr-FR")}</p>
            </li>
            
        {/each}
    </ul>
</main>


<style>
    main {
        overflow-y: scroll;
        border: 2px solid black ;
        grid-column:  2/3;
        grid-row: 2/3;
        
    
    }

    h5 {margin: 0px;
        padding: 0.5rem 0 0;
    }

    ul {
        background-color: lightgreen;
        position: relative;
        top: 0px;
    }

    li {
        cursor: pointer;
    }

    li:nth-child(2n) {
        background-color: lightgray;
    }


</style>