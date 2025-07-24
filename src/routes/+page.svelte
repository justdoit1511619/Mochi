<script lang="ts">
	import { expoIn } from 'svelte/easing';
	import { Cart, IsCartOpen } from '../stores/Cart.js';
	import CartDetails from '$lib/components/Cart/CartDetails.svelte';
	import { scale } from 'svelte/transition';
	import ProductList from '$lib/components/ProductList/ProductList.svelte';
	import { t } from '$lib/i18n/i18n.js';
	//import Main from './Main.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';
	export let data: { props: { products: { tags: string[] }[] } };
	const products = data.props.products;
	const bestseller = products.filter((product: { tags: string[] }) => product.tags.includes('bestseller'));
	let y = 0;
	$: cartNumber = $Cart.reduce((count, item) => count + item.qty, 0);
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
				<!-- Cart Items count -->
				{#key cartNumber}
					<div
						class="flex rounded-full text-2sm fixed {y < 90
							? 'bg-white text-black'
							: 'bg-black'} items-center top-12 right-10 px-2"
						in:scale={{ duration: 200, start: 1.5, opacity: 1, easing: expoIn }}
					>
						<!-- Cart Icon -->
						<svg
							in:scale|local={{ duration: 200, start: 1.5, opacity: 1, easing: expoIn }}
							class="block h-12 w-12 {y < 90 ? 'bg-white' : 'bg-black'} rounded-full p-2 ml-auto"
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke={y < 90 ? 'black' : 'white'}
							stroke-width="2"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"
							/></svg
						>					
						{cartNumber}
					</div>
				{/key}
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
