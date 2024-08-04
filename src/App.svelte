<script>
  	import Category from "./components/Category.svelte";
	import Home from "./components/Home.svelte";
	import Cart from "./components/Cart.svelte";
	import Router from "svelte-spa-router";
  	import About from "./components/About.svelte";
  	import Product from "./components/Product.svelte";
	import { onMount } from 'svelte';
	import LoadingSpinner from "./components/LoadingSpinner.svelte";

	let isLoading = true;

    onMount(() => {
        setTimeout(() => {
            isLoading = false;
        }, 900);
    });

	let routes = {
		"/": Home,
		"/categories": Category,
		"/cart-info": Cart,
		"/about": About,
		"/product/:prodName": Product
	}
</script>

<main>
	{#if isLoading}
		<LoadingSpinner message="Loading page content..." />
	{:else}
		<Router {routes} />
	{/if}
</main>

<style>
	
</style>