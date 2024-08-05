<script>
    import Category from "./components/Category.svelte";
    import Home from "./components/Home.svelte";
    import Cart from "./components/Cart.svelte";
    import About from "./components/About.svelte";
    import ProductPage from "./components/ProductPage.svelte";
    import LoadingSpinner from "./components/LoadingSpinner.svelte";
    import Router from 'svelte-spa-router';
    import { onMount } from 'svelte';

    let isLoading = true;

    onMount(() => {
        setTimeout(() => {
            isLoading = false;
        }, 100);
    });

    const routes = {
        "/": Home,
        "/categories": Category,
        "/cart-info": Cart,
        "/about": About,
        "/product/:prodName/:image": ProductPage
    };
</script>

<main>
    {#if isLoading}
        <LoadingSpinner message="Loading page content..." />
    {:else}
        <Router {routes} />
    {/if}
</main>

<style>
    /* Add your styles here */
</style>
