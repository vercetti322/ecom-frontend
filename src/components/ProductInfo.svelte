<script>
    export let data;
    console.log(data);
    import RatingCard from "./RatingCard.svelte";
    let isClicked = false;


    function handleClick() {
        if (!isClicked) {
            isClicked = true;
            incrementItems();
        }
    }
</script>

<div class="product-info">
    <div class="product-image-container">
        <img src="{data.productKey.image}" alt="img" class="product-image">
        <div class="product-stats" style="padding-left: 30px;">
            <div class="product-price" style="font-size: 28px;">${data.price}</div>
            <div class="product-rating">
                <RatingCard rating={data.rating}/>
            </div>
        </div>
    </div>
    <div class="product-desc-container">
        <div class="product-name" style="font-size: 22.5px; font-weight: bold; margin-bottom: 13.5px">{data.productKey.name}</div>
        <div class="product-category" style="color: yellow; font-size: 16px; margin-bottom: 5px">{data.productKey.category}</div>
        <div class="product-desc" style="font-size: 13px; margin-bottom: 10px;">{data.description}</div>
        <div class="product-availability" style="font-size: 18px;">
            {#if data.available}
                <h3 style="color: green;">In Stock</h3>
                <button 
                    class={isClicked ? 'carton-button' : 'carton-button-disabled'}
                    on:click={handleClick}
                    disabled={isClicked}
                >
                    Add to Cart
                </button>
            {:else}
                <h3 style="color: red;">Out of Stock!</h3>
                <button class="cart-button" disabled>Add to Cart</button>
            {/if}
        </div>

    </div>
</div>

<style>
    .product-info {
        display: grid;
        background-color: rgb(255, 178, 36);;
        grid-template-columns: 1fr 1fr;
        margin-top: 100px;
        margin-left: 300px;
        margin-right: 315px;
        margin-bottom: 150px;
        border: none;
        border-radius: 15px;
        height: 330px;
        width: 390px;
    }

    .product-desc-container, .product-image-container {
        padding: 12px;
    }

    .product-image-container {
        display: grid;
        grid-template-rows: 2.3fr 1fr;
    }

    .product-stats {
        margin-top: 15px;
    }

    .product-image-container img {
        width: 100%;
        height: auto;
        object-fit: cover;
        border: none;
        border-radius: 15px;
        padding: 7.5px;
    }

    .cart-button {
        margin-top: 10px;
        cursor: pointer;
        margin-left: 5px;
        background-color: rgb(208, 107, 0);
        border-radius: 35px;
        border: none;
        height: 40px;
        width: 100px;
        color: yellow;
    }

    .cart-button:active {
        background-color: orange;
        color: white;
        border-radius: 35px;
        border: none;
        height: 40px;
        width: 100px;
    }
</style>