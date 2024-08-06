<script>
    $: numItems = 0;
    function incrementItems() {
        numItems += 1;
    }

    const baseUrl = 'http://localhost:8080'
</script>

<nav class="ecom-nav">
    <a href="{baseUrl}" class="ecom-brand">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <img src="./Images/Background/logo.png" alt="logo" class="ecom-logo">
    </a>
    <ul class="ecom-quick-links">
        <li><a href="{baseUrl}">Home</a></li>
        <li><a href="{baseUrl}/#/about">About</a></li>
        <li><a href="{baseUrl}/#/categories">Categories</a></li>
        <li><a href="{baseUrl}/#/cart-info">Cart ({numItems})</a></li>
    </ul>
</nav>

<style>
    .ecom-nav {
        display: flex;
        align-items: center;
        justify-content: left;
        height: 60px;
        padding-left: 15px;
        padding-top: 45px;
        padding-bottom: 15px;
        position: relative;
        background-image: url('../Images/Background/wave.png');
        background-size: contain;
    }

    .ecom-logo {
        margin-top: 35px;
        margin-right: 15px;
        height: auto;
        width: 120px;
        object-fit: contain;
        border-radius: 100%;
    }

    .ecom-nav ul li {
        padding-right: 25px;
        background: none;
    }

    .ecom-brand {
        display: flex;
        align-items: center;
        padding-right: 5px;
        height: 80px;
        background: none;
    }

    .ecom-quick-links {
        display: flex;
        justify-content: space-between;
        list-style-type: none;
        background: none;
    }

    .ecom-quick-links, .ecom-nav a {
        text-decoration: none;
        color: black;
        font-weight: 700;
        font-size: 20px;
        background: none;        
    }
</style>