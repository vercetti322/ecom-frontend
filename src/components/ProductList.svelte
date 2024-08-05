<script>
    import ProductCard from "./ProductCard.svelte";
    import { onMount } from 'svelte';
    
    let rawProducts = [];
    let products = [];
    let error = null;
    let path;

    onMount(async () => {
        try {
            path = window.location.hash;
            let response;

            if (path === '') {
                response = await fetch('http://localhost:8090/api/products/preview');
                if (!response.ok)
                   throw new Error('Network response was not ok');
                
                const data = await response.json();
                rawProducts = data;

                // Update the products array based on the fetched rawProducts
                products = rawProducts.map(product => ({
                    image: product.productKey.image,
                    prodName: `${product.productKey.name} (${product.brand})`,
                    price: `$${product.price}`,
                    rating: product.rating
                }));
            }

            else if (path === '#/categories') {
                response = await fetch('http://localhost:8090/api/products/category')
                if (!response.ok)
                   throw new Error('Network response was not ok');
                
                const data = await response.json();
                rawProducts = data;

                // Update the products array based on the fetched rawProducts
                products = Object.keys(rawProducts).reduce((acc, key) => {
                    acc[key] = rawProducts[key].map(product => ({
                        image: product.productKey.image,
                        prodName: `${product.productKey.name} (${product.category})`,
                        price: `$${product.price}`,
                        rating: product.rating
                    }));
                    return acc;
                }, {});
            }

        } catch (err) {
            error = err.message;
        }
    });
</script>

{#if path === ''}
    <div class="product-list-preview">
        {#each products as product}
            <ProductCard
                image={product.image}
                prodName={product.prodName}
                price={product.price}
                rating={product.rating}
            />
        {/each}
    </div>
{:else if path === '#/categories'}
    <div class="product-list-category">
        {#each Object.keys(products) as category}
            <h2>{category}</h2>
            <div class="product-category">
                {#each products[category] as product}
                    <ProductCard
                        image={product.image}
                        prodName={product.prodName}
                        price={product.price}
                        rating={product.rating}
                    />
                {/each}
            </div>
        {/each}
    </div>
{/if}
<style>
    .product-list-preview {
        margin: 5px;
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1px;
        padding: 1px;
    }

    .product-category {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 1px;
        padding: 1px;
    }

    .product-list-category {
        margin: 5px;
    }

    h2 {
        grid-column: span 3;
        margin-top: 35px;
        text-align: center;
    }
</style>