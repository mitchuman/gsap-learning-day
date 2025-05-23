<script lang="ts">
	const links: Array<{ href: string; label?: string }> = [{ href: '0' }]
</script>

<nav>
	<details>
		<summary>Menu</summary>

		<ul class="list-[disc] pl-4">
			{#each links as { href, label }}
				<li>
					<a class="text-[dodgerblue] underline" href="/tutorials/{href}">{label ?? href}</a>
				</li>
			{/each}
		</ul>
	</details>
</nav>
