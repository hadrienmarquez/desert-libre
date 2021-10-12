<script context="module">

    // Posts metadata retrieving
    const modules = import.meta.glob("./posts/*.md");
    export const allPosts = [];

    for(let path in modules) {
        allPosts.push(modules[path]().then(({metadata}) => {
            return {path, metadata};
        }));
    }

    export const load = async () => {

    const posts = await Promise.all(allPosts);


    return {
        props: {
            posts,
        },
    };
    };

</script>

<script lang="ts">
        import BlogIndex from "/src/components/BlogIndex.svelte";
        export let posts;

        // Sorting posts by date.
        // @ts-ignore
        posts.sort((post1, post2) => {
            const date1: Date =  new Date(post1.metadata.date);
            const date2: Date =  new Date(post2.metadata.date);
            return   date2.getTime() - date1.getTime();
        })
</script>

<!-- Global things to add to head -->
<svelte:head>
    <title>Désert libre</title>
</svelte:head>

<main class="panel grid">
    <!-- Title -->
    <h1 class="title huge">Désert libre</h1>


    <!-- Liste des blogs -->
    <BlogIndex {posts}>

    </BlogIndex>


    <!-- Bas de page -->

</main>

<style>
    .panel {
        width: 70%;
        height: 100vh;
        margin: 0px 15vw;
    }

    main {
        grid-template-columns: 1fr 3fr 1fr;
        grid-template-rows: 3fr 4fr 2fr;
    }

    .title {
        font-weight: bold;
        grid-column:  2/3;
        justify-self: center;
        align-self: center;
    }



</style>