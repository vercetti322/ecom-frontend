<script>
    import Navbar from "./Navbar.svelte";
    import { onMount } from 'svelte';
    import LoadingSpinner from "./LoadingSpinner.svelte";
	import ProductInfo from "./ProductInfo.svelte";

    export let params;
    let prodName = decodeURIComponent(params.prodName);
    let image = decodeURIComponent(params.image);
	const backendUrl = "http://localhost:8090/api/products"

	let parts = prodName.split(" (");
	let productName = parts[0];
	let productCategory = parts[1].replace(")", "");
	let data;

	onMount(async () => {
		const response = await fetch(`${backendUrl}/${productCategory}/${productName}?image=${encodeURIComponent(image)}`);
		if (!response.ok) {
			throw new Error("network error while fetching data...");
		}

		data = await response.json();
	})

    let isLoading = true;
    onMount(() => {
        setTimeout(() => {
            isLoading = false;
        }, 900); // Adjust the delay as needed
    });
</script>

<main>
    {#if isLoading}
        <LoadingSpinner message="Loading page content..." />
    {:else}
        <Navbar/>
        <ProductInfo {data}/>
    {/if}
</main>

<style>
   
</style>
