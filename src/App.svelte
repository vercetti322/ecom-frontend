<script>
	import Navbar from "./components/Navbar.svelte";
	import ProductList from "./components/ProductList.svelte";
	import HomeIntro from "./components/HomeIntro.svelte";
</script>

<main>
	<Navbar/>
	<div class="main-content">
		<HomeIntro/>
		<ProductList/>
	</div>
</main>

<style>
	.main-content {
		display: flex;
		flex-direction: column;
        align-items: center;
	}
</style>