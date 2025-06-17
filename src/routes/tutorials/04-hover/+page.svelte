<script lang="ts">
	import { gsap } from 'gsap'

	let goodJob: gsap.core.Tween | null = $state(null)
	let link: gsap.core.Tween | null = $state(null)

	$effect(() => {
		goodJob = gsap.fromTo(
			'emoji.stamp',
			{
				opacity: 0,
				rotate: -45,
				scale: 0,
			},
			{
				opacity: 1,
				scale: 1,
				rotate: -12,
				ease: 'power3.out',
				paused: true,
			},
		)

		link = gsap.fromTo(
			'emoji.ok',
			{
				opacity: 0,
				scale: 0,
				transformOrigin: 'bottom',
			},
			{
				opacity: 1,
				scale: 1,
				duration: 0.2,
				paused: true,
			},
		)
	})
</script>

<section class="space-y-12">
	<div class="flex items-end">
		<article
			class="inline-block cursor-crosshair"
			onmouseenter={() => goodJob?.play()}
			onmouseleave={() => goodJob?.reverse()}
		>
			<div class="relative">
				<big class="text-7xl">📄</big>
				<emoji class="stamp absolute bottom-0 left-1/8 mix-blend-darken">💮</emoji>
			</div>
		</article>

		<p>👈 Hover over me!</p>
	</div>

	<a
		class="ok-link relative"
		href="#"
		onmouseenter={() => link?.play()}
		onmouseleave={() => link?.reverse()}
	>
		It's O.K.
		<emoji class="ok absolute bottom-0 left-0 -z-1 translate-x-1/2 text-center">👌</emoji>
	</a>
</section>
