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
    color: white;
    border: 3px solid white;
    padding: 0.6rem;
    background-color: rgba(black, 0.4);
    font-weight: 700;
    text-transform: uppercase;
    width: 8rem;
    text-align: center;
    transition: color .4s  ease-in-out, background .2s;
    &:hover {
      background-color: rgba(white, 1);
      color: black;
    }
	}
</style>
