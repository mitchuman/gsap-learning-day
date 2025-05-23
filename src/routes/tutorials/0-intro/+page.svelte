<script lang="ts">
	import { gsap } from 'gsap'

	$effect(() => {
		gsap.to('h1', {
			x: 100,
			color: 'dodgerblue',
			fontSize: '2rem',
		})

		gsap.from('emoji', {
			x: 400,
			duration: 3,
		})

		gsap.to('.siren', {
			stagger: 1,
			scale: 2,
			duration: 1,
		})
	})
</script>

<h1>hello world</h1>

<div class="flex gap-4">
	<emoji>🏎️</emoji>

	<div class="flex">
		<emoji class="z-1">🚓</emoji>
		<emoji class="siren">🚨</emoji>
		<emoji class="siren">🚨</emoji>
		<emoji class="siren">🚨</emoji>
	</div>
</div>
