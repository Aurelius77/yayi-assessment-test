<script>
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1 class="text-4xl font-bold text-center md:text-7xl header-text md:mt-2 md:mb-4">
		The Yaji Way!
	</h1>

	<h2 class="text-lg font-normal text-center md:text-2xl sub-text">
		Yaji is the next evolution of West African flavour—a fast-casual restaurant built around bold, fire-kissed bowls, wraps, and tacos. Inspired by suya culture. 

Made to move with you. 

Built to stay on your mind.
	</h2>

</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	
	.header-text{
       font-family: "Permanent Marker", cursive;
       font-weight: 400;
       font-style: normal;
       color: #4C0703;
	}

	.sub-text {
		font-family: 'Plus Jakarta Sans', sans-serif;
		font-weight: 400;
		font-style: normal;
		color: #4C0703;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		white-space: pre-line;
	}


</style>
