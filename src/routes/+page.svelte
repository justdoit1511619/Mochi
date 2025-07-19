<script>
	import ProductList from '$lib/components/ProductList/ProductList.svelte';
	import { t } from '$lib/i18n/i18n.js';
	//import Main from './Main.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';
	export let data;
	const products = data.props.products;
	const bestseller = products.filter((product) => product.tags.includes('bestseller'));
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			</picture>
		</span>
	</h1>

	<div class="text-center">
		<div class="pt-8">
			<div class="text-2xl">{$t('home.bestseller_title')}</div>
			<ProductList products={bestseller} />
		</div>
	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
