<script lang="ts">
	import { gsap } from 'gsap'
	import type { Snippet } from 'svelte'
	import type { HTMLAttributes } from 'svelte/elements'

	let button: HTMLButtonElement | null = $state(null)
	let tween: gsap.core.Tween | null = $state(null)

	let { children, onclick, ...props }: { children: Snippet } & HTMLAttributes<HTMLElement> =
		$props()

	$effect(() => {
		tween = gsap.fromTo(
			button,
			{
				backgroundColor: 'dodgerblue',
			},
			{
				backgroundColor: 'green',
				paused: true,
			},
		)
	})
</script>

<button
	bind:this={button}
	onclick={(e) => {
		tween?.restart()
		onclick?.(e)
	}}
	{...props}>{@render children()}</button
>
