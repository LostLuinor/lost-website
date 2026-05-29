<script>
	import '../app.css';
	import Navbar from '$lib/components/layout/Navbar.svelte';
	import Footer from '$lib/components/layout/Footer.svelte';
</script>

<svelte:head>
	<title>Lost</title>
	<meta
		name="description"
		content="IDK.... Insights, tutorials, and thoughts on development and technology from LOST."
	/>
</svelte:head>

<Navbar />

<main>
	<slot />
</main>

<Footer />
