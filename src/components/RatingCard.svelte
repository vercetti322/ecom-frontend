<script>
    export let rating;
    $: rating; 
    const maxRating = 5; 
</script>


<div class="rating">
    {#each Array(maxRating).fill().map((_, i) => i + 1) as star}
        <svg class="star {star <= rating ? 'filled' : ''}" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <polygon points="12 1.489 15.09 7.751 22 8.755 17 13.629 18.18 20.511 12 17.261 5.82 20.511 7 13.629 2 8.755 8.91 7.751 12 1.489" />
        </svg>
    {/each}
</div>

<style>
    .rating {
        background: none;
    }

    .star {
        width: 12px;
        height: 12px;
        display: inline-block;
        fill: #5b5a5a;
        background: none;
    }

    .star.filled {
        fill: green;
    }
</style>