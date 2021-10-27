<script>
	import '../app.css';
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
</script>

<div
	class="flex flex-col min-h-screen w-full flex-grow bg-gradient-to-br from-gray-200 via-gray-400 to-gray-600"
>
	<Header />
	<main class="flex flex-col flex-grow">
		<slot />
	</main>
	<Footer />
</div>
