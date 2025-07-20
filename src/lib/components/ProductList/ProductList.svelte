<script>
	import ProductCard from './ProductCard.svelte';
	export let products = [];
</script>

<div class="product-list">
	<div class="my-8 grid gap-10 md:grid-cols-2 xl:grid-cols-4">
		{#each products as product (product.id)}
			<ProductCard {product} />
		{/each}
	</div>
</div>
<style>
.product-list {
    display: flex;
    flex-direction: row;
    overflow-x: auto;
    gap: 1rem;
    padding-bottom: 1rem;
    scroll-behavior: smooth;
    /* Optional: for right-to-left scroll */
    direction: ltr;
}
</style>