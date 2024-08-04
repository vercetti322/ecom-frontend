<script>
	import Navbar from "./Navbar.svelte";
	import ProductList from "./ProductList.svelte";
	import { onMount } from 'svelte';
	import LoadingSpinner from "./LoadingSpinner.svelte";

	let isLoading = true;

    onMount(() => {
        setTimeout(() => {
            isLoading = false;
        }, 900);
    });
</script>

<main>
	{#if isLoading}
		<LoadingSpinner message="Loading page content..." />
	{:else}
		<Navbar/>
		<div class="main-content">
			<ProductList/>
		</div>
	{/if}
</main>

<style>
	.main-content {
		display: flex;
		flex-direction: column;
        align-items: center;
	}
</style>