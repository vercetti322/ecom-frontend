<script>
    export let image = 'image';
    export let name = 'name';
    export let price = 'price';
    export let rating = 'rating';
</script>

<div class="product-card">
    <div class="product-img" style="background-image: url('{image}')">Image</div>
    <div class="product-name">{name}</div>
    <div class="product-price">{price}</div>
    <div class="product-rating">{rating}</div>
</div>

<style>
    .product-card {
        display: grid;
        grid-template-rows: 6fr 1.5fr 1fr 1fr; 
        margin: 40px;
        border: none;
        border-radius: 12px;
        height: 230px;
        width: 200px;
    }

    .product-card > div {
        padding: 5px;
        border-radius: 12px;
        background-color: #fcd58b;
    }

</style>