<script>
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
            style="border-radius: 0 0 7.5px 7.5px;"
        >
            {rating}
        </div>
    </div>

<style>
    .product-card {
        display: grid;
        grid-template-rows: 6fr 1fr 1fr 1fr; 
        margin: 40px;
        border: none;
        border-radius: 7.5px;
        height: 250px;
        overflow: hidden;
        width: 210px;
        box-shadow: 0 0 10px #73bbd2;
        transition: transform 0.45s ease; 
    }

    .product-card > div {
        padding: 5px;
        background-color: #f5b235;
        color: black;
    }

    .product-card:hover {
        transform: scale(1.10); /* Slightly increase size */
        cursor: pointer;
    }
</style>