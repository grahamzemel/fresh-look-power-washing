<script lang="ts">
    export let imagePairs: { before: string; after: string }[] = [];
</script>

<style>
    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 16px;
    }
    .image-pair {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .image-pair img {
        max-width: 100%;
        border-radius: 8px;
        margin-bottom: 8px;
    }
</style>

<div class="grid">
    {#each imagePairs as { before, after }}
        <div class="image-pair">
            <img src={before} alt="Before" />
            <img src={after} alt="After" />
        </div>
    {/each}
</div>