<script>
    import RatingCard from "./RatingCard.svelte";
    export let image = 'image';
    export let name = 'name';
    export let price = 'price';
    export let rating = 'rating';
    export let id = 10019;

    let productInfo;
    
    const fetchDetails = async () => {
        let error = null;
        try {
            const response = await fetch(`http://localhost:8090/api/products/${id}`);
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            const data = await response.json();
            productInfo = data;
            console.log(productInfo);
        } catch (err) {
            error = err.message;
            console.error('Error fetching product details:', error);
        }
    };
</script>

    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="product-card" on:click={fetchDetails}>
        <div 
            class="product-img" 
            style="
                background-image: url('{image}');
                background-size: contain;
                border-radius: 7.5px 7.5px 0 0;
            "
        ></div>
        <div class="product-name">{name}</div>
        <div class="product-price">{price}</div>
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

<style>
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