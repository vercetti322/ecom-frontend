<script>
    let numItems = 0;
</script>

<nav class="ecom-nav">
    <a href="#home" class="ecom-brand">
        <img src="./Images/logo.png" alt="logo" class="ecom-logo">
    </a>
    <ul class="ecom-quick-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#categories">Categories</a></li>
        <li><a href="#contact">Contact</a></li>
        <li><a href="#cart">Cart ({numItems})</a></li>
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
        background-color: #FFE5B4;
        padding-bottom: 15px;
        position: relative;
        background-image: url('../Images/wave.png');
        background-size: contain;
    }

    .ecom-logo {
        padding-top: 10px;
        padding-right: 15px;
        height: auto;
        width: 120px;
        object-fit: contain;
        background: none;
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