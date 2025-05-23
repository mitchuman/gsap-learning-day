<script lang="ts">
	import { gsap } from 'gsap'

	$effect(() => {
		gsap.to('h1', {
			x: 400,
		})
	})
</script>

<h1>hello world</h1>
