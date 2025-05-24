<script lang="ts">
	import { gsap } from 'gsap'

	let anim: gsap.core.Timeline | null = $state(null)

	$effect(() => {
		anim = gsap
			.timeline()
			.from('.countdown', {
				opacity: 0,
				scale: 0,
				stagger: 1,
			})
			.add('T minus 5', 5)
			.add('T minus 3', 7)
			.add('launch')
			.from(
				'.rocket',
				{
					x: -3,
					repeat: -1,
					yoyo: true,
					ease: 'sine.inOut',
					duration: 1 / 24,
				},
				7,
			)
			.from('.smoke', { opacity: 0, scale: 0, y: -50, duration: 3 }, '<')
			.to('.smoke', { y: 50, ease: 'sine.in' }, '-=0.2')
			.to('.smoke', { opacity: 0 }, '<')
			.to('.rocket', { opacity: 1, y: -100, ease: 'sine.in' }, '<')
	})
</script>

<div class="flex">
	<div>
		<emoji class="countdown">🔟</emoji>
		<emoji class="countdown">9️⃣</emoji>
		<emoji class="countdown">8️⃣</emoji>
		<emoji class="countdown">7️⃣</emoji>
		<emoji class="countdown">6️⃣</emoji>
		<emoji class="countdown">5️⃣</emoji>
		<emoji class="countdown">4️⃣</emoji>
		<emoji class="countdown">3️⃣</emoji>
		<emoji class="countdown">2️⃣</emoji>
		<emoji class="countdown">1️⃣</emoji>
	</div>
	<div class="flex flex-col items-center">
		<emoji class="rocket ml-4 -rotate-45">🚀</emoji>
		<div class="flex *:-mr-4">
			<emoji class="smoke rotate-120 leading-none">💨</emoji>
			<emoji class="smoke rotate-90 leading-none">💨</emoji>
			<emoji class="smoke rotate-60 leading-none">💨</emoji>
		</div>
	</div>
</div>

<button onclick={() => anim?.restart()}>Start</button>
<button onclick={() => anim?.play('T minus 5')}>T minus 5</button>
<button onclick={() => anim?.play('T minus 3')}>T minus 3</button>
<button onclick={() => anim?.play('launch')}>Launch!</button>
