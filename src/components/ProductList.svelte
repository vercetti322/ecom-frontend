<script>
    import ProductCard from "./ProductCard.svelte";
    import { onMount } from 'svelte';
    // let newProducts = [];
    // let error = null;

    // onMount(async () => {
    //     try {
    //         const response = await fetch('http://localhost:8090/api/products/preview')
    //         if (!response.ok) {
    //             throw new Error('Network response was not ok');
    //         }
            
    //         const data = await response.json();
    //         newProducts = data;
    //         console.log(newProducts);
    //     } catch (err) {
    //         error = err.message;
    //     }
    // })


    let products = [
        {
            image: '../Images/product-1.webp',
            name: 'Product 1',
            price: '$20',
            rating: '4'
        },

        {
            image: '../Images/product-2.webp',
            name: 'Product 2',
            price: '$200',
            rating: '3'
        },

        {
            image: '../Images/product-3.webp',
            name: 'Product 3',
            price: '$10',
            rating: '1'
        },

        {
            image: '../Images/product-3.webp',
            name: 'Product 3',
            price: '$10',
            rating: '1'
        },

        {
            image: '../Images/product-1.webp',
            name: 'Product 1',
            price: '$20',
            rating: '4'
        },

        {
            image: '../Images/product-2.webp',
            name: 'Product 2',
            price: '$200',
            rating: '3'
        },

        {
            image: '../Images/product-3.webp',
            name: 'Product 3',
            price: '$10',
            rating: '1'
        },

        {
            image: '../Images/product-3.webp',
            name: 'Product 3',
            price: '$10',
            rating: '1'
        }
    ]
</script>

<div class="product-list">
    {#each products as product}
        <ProductCard
            image={product.image}
            name={product.name}
            price={product.price}
            rating={product.rating}
            id={product.id}
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