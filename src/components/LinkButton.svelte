<script lang="ts">
    export let url: string;
</script>



<a class="small" href={url}>
    <slot></slot>
</a>

<style>

    a {
        background-color: var(--primary-color);
        padding: 2px 1em;
        border-radius: 50px;
        box-shadow: 2px 2px var(--secondary-color);
    }

</style>