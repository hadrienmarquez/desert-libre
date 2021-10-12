<script>
  import LinkButton from "./LinkButton.svelte";
  export let posts;
</script>

<main>
  <ul>
    {#each posts as { path, metadata: { title, date } }}
      <li
        class="post grid"
      >
        <h5 class="post--title">
          {title}
        </h5>
        <p class="post--date smaller">
          {new Date(date).toLocaleDateString("fr-FR")}
        </p>
        <div class="post--button">
            <LinkButton url={`/${path.replace(".md", "")}`}>Lire l'article</LinkButton>
        </div>
        
      </li>
    {/each}
  </ul>
</main>

<style>
  main {
    overflow-y: scroll;
    border: 2px solid black;
    grid-column: 2/3;
    grid-row: 2/3;
    scrollbar-width: none;
    
  }

  /* No scrollbar, chrome compatibility  */
  .main::-webkit-scrollbar {
  display: none;
}

  h5 {
    margin: 0px;
    padding: 0.5rem 0 0;
  }

  ul {
    position: relative;
    top: 0px;
    width: 90%;
    margin: 0 auto;
  }

  .post {
    border-bottom: 1px solid black;



    height: 80px;
    padding: 0 1em;
    margin-bottom: 5px;

    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(2,1fr);
  }

  .post--date {
    font-style: italic;

    grid-column: 3/4;
    grid-row: 1/2;

    justify-self: end;
    align-self: center;
  }

  .post--title {

    
    grid-column: 1/3;
    grid-row: 1/2;


    justify-self: start;
    align-self: center;

  }

  .post--tag {

  }

  .post--button {
    grid-column: 3/4;
    grid-row: 2/3;


    justify-self: end;
    align-self: start;
}

</style>
