<script>
    import Navbar from "./Navbar.svelte";
    import { onMount } from 'svelte';
    import LoadingSpinner from "./LoadingSpinner.svelte";

    export let params;
    let prodName = decodeURIComponent(params.prodName);
    let image = decodeURIComponent(params.image);
	console.log(params);

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
        <div class="main-content">
            <h3>{prodName}</h3>
            <img src={`${image}`} alt={prodName} />
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
