<script lang="ts">
	import { page } from '$app/state'
	import type { Snippet } from 'svelte'

	let { children }: { children: Snippet } = $props()

	const base_url = 'https://github.com/mitchuman/gsap-learning-day/tree/main/src/routes'
</script>

<nav class="text-right">
	<a
		class="border border-dashed p-2"
		href="{base_url}/{page.route.id}/+page.svelte"
		target="_blank"
	>
		View source code
	</a>
</nav>

{@render children()}
