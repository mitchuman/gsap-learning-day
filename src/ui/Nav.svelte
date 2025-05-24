<script lang="ts">
	import { page } from '$app/state'
	import clsx from 'clsx'

	const links: Array<{ href: string; label?: string }> = [
		{ href: '0-intro' },
		{ href: '1-tween' },
		{ href: '2-controls' },
		{ href: '3-timeline' },
		{ href: '4-hover' },
	]
</script>

<nav>
	<details
		class="relative"
		onmouseenter={(e) => (e.currentTarget.open = true)}
		onmouseleave={(e) => (e.currentTarget.open = false)}
	>
		<summary>Menu</summary>

		<ul class="absolute top-full left-0 min-w-max list-[disc] bg-black p-2 pl-6 text-white">
			{#each links as { href, label }}
				{@const path = `/tutorials/${href}`}
				<li class={clsx(page.route.id === path && 'after:content-["_👈"]')}>
					<a class="text-[dodgerblue] underline" href={path}>{label ?? href}</a>
				</li>
			{/each}
		</ul>
	</details>
</nav>
