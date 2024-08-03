<script>
    import ProductCard from "./ProductCard.svelte";
    let products = Array(9).fill({})
</script>

<div class="product-list">
    {#each products as product}
        <ProductCard
            image={product.image}
            name={product.name}
            price={product.price}
            rating={product.rating}
        />
    {/each}
</div>

<style>
    .product-list {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 5px;
        padding: 5px;
    }
</style>