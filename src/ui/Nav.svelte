<script lang="ts">
	const links: Array<{ href: string; label?: string }> = [{ href: '/' }]
</script>

<nav>
	<ul>
		{#each links as { href, label }}
			<li>
				<a {href}>{label ?? href}</a>
			</li>
		{/each}
	</ul>
</nav>
