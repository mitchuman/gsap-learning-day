<script lang="ts">
	import { page } from '$app/state'
	import clsx from 'clsx'

	const links: Array<{ href: string; label?: string }> = [
		{ href: '00-intro' },
		{ href: '01-tween' },
		{ href: '02-controls' },
		{ href: '03-timeline' },
		{ href: '04-hover' },
		{ href: '05-final' },
		{ href: '06-typewriter' },
		{ href: '07-percent' },
		{ href: '08-chained' },
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
