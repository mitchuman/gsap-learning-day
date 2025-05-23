<script lang="ts">
	import Nav from '@/ui/Nav.svelte'
	import '@/app.css'

	let { children } = $props()
</script>

<svelte:head>
	<title>Learning Day — GSAP</title>
</svelte:head>

<header class="relative z-10 flex items-center gap-4 bg-black p-4 text-white">
	<a href="/">Learning Day — GSAP</a>
	<Nav />
</header>

<main class="p-4">{@render children()}</main>
