<script>
    import ProductCard from "./ProductCard.svelte";
    import { onMount } from 'svelte';
    
    let rawProducts = [];
    let products = [];
    let error = null;

    onMount(async () => {
        try {
            const baseUrl = 'http://localhost:8080';
            const path = window.location.pathname; 
            let response;
            if (path === '/') {
                response = await fetch('http://localhost:8090/api/products/preview');
            } else if (path === '/categories') {
                response = await fetch('http://localhost:8090/api/products/category');
            } 
            
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            
            const data = await response.json();
            rawProducts = data;
            
            // Update the products array based on the fetched rawProducts
            products = rawProducts.map(product => ({
                image: product.productKey.image,
                prodName: `${product.productKey.name} (${product.brand})`,
                price: `$${product.price}`,
                rating: product.rating
            }));

        } catch (err) {
            error = err.message;
        }
    });
</script>

<div class="product-list">
    {#each products as product}
        <ProductCard
            image={product.image}
            prodName={product.prodName}
            price={product.price}
            rating={product.rating}
        />
    {/each}
</div>

<style>
    .product-list {
        margin: 5px;
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1px;
        padding: 1px;
    }
</style>