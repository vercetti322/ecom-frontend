<script>
    import RatingCard from "./RatingCard.svelte";
    export let image;
    export let prodName;
    export let price;
    export let rating;
    const baseUrl = 'http://localhost:8080'
    let encodedProdName = encodeURIComponent(prodName);
    let encodedImage = encodeURIComponent(image);
    console.log(`${baseUrl}/#/product/${encodedProdName}/${encodedImage}`);
</script>

    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <a href="{baseUrl}/#/product/{encodedProdName}/{encodedImage}" class="card">
        <div class="product-card">
            <div 
                class="product-img" 
                style="
                    background-image: url('{image}');
                    background-size: cover;
                    border-radius: 7.5px 7.5px 0 0;
                "
            ></div>
            <div class="product-name"
                style="font-size: 12px;"
            >
            {prodName}</div>
            <div class="product-price"
                style="font-size: 14px; font-weight: bold"
            >{price}</div>
            <div 
                class="product-rating" 
                style="
                    border-radius: 0 0 7.5px 7.5px;
                    font-size: 13px;
                    font-weight: 700;
                "
            >
                {rating}/5
                <RatingCard {rating}/>
            </div>
        </div>
    </a>
<style>
    .card {
        text-decoration: none;
        color: black;
    }
    .product-card {
        display: grid;
        grid-template-rows: 6fr 1fr 1fr 1fr; 
        margin: 40px;
        border: none;
        border-radius: 7.5px;
        height: 215px;
        overflow: hidden;
        width: 175px;
        box-shadow: 0 0 10px #73bbd2;
        transition: transform 0.15s ease; 
    }

    .product-card > div {
        padding: 2.5px;
        margin: 0;
        background-color: rgb(255, 178, 36);
    }

    .product-card:hover {
        background-color: rgb(255, 178, 36);
        transform: scale(1.20); /* Slightly increase size */
        cursor: pointer;
    }
</style>