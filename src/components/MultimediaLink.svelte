<script lang="typescript">
	import type { Multimedia } from '../data';
	export let multimedia: Multimedia;
</script>

<div class="multimedia-link" on:click={() => window.open(multimedia.link, '_blank')}>
	{multimedia.text}
</div>

<style lang="scss">
	.multimedia-link {
		cursor: pointer;
	}
</style>
