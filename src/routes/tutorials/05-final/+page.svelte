<script lang="ts">
	import { gsap } from 'gsap'
	import { GSDevTools } from 'gsap/dist/GSDevTools'

	gsap.registerPlugin(GSDevTools)

	let tl: gsap.core.Timeline = $state(
		gsap.timeline({
			defaults: { opacity: 0, ease: 'back' },
		}),
	)

	$effect(() => {
		GSDevTools.create()

		tl.from('#hero', { ease: 'linear', autoAlpha: 0 })
			.from('#hero h1', { x: 80 })
			.from('#hero h1 strong', { rotate: -180 }, '<')
			.from('#hero p:not(:has(button))', { x: -80 }, '-=0.25')
			.from('#hero p:has(button)', { yPercent: 100 }, '-=0.25')
			.from('#hero figure span', { scale: 0, opacity: 1, stagger: 0.1 }, '-=0.3')
	})
</script>

<section id="hero" class="invisible grid items-center gap-x-12 gap-y-6 md:grid-cols-2">
	<header class="space-y-4">
		<h1 class="text-4xl text-balance"><strong class="inline-block">Creative</strong> Process</h1>
		<p>Learn how to find inspiration in the things you love.</p>
		<p><button>Read more</button></p>
	</header>

	<figure class="grid aspect-square grid-cols-2 gap-4 border text-center text-7xl *:m-auto">
		<span>⚾</span>
		<span>🧢</span>
		<span>👨‍🚀</span>
		<span>🏌️‍♂️</span>
	</figure>
</section>
