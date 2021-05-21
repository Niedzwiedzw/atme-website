<script lang="typescript">
	import MultimediaLink from '/src/components/MultimediaLink.svelte';
	import { multimedia, images } from '../data';

	const nextRandomPhoto = (): string => images[parseInt(`${Math.random() * (images.length - 1)}`)];
	const currentPhoto: string = nextRandomPhoto();
</script>

<main style="background-image: url({currentPhoto});">
	{#each multimedia as media (media.link)}
		<MultimediaLink multimedia={media} />
	{/each}

	<div class="soundcloud-preview">
		<iframe
			width="100%"
			height="200"
			scrolling="no"
			frameborder="no"
			allow="autoplay"
			title="soundcloud"
			src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/248167604&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"
		/>
		<div
			style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"
		>
			<a
				href="https://soundcloud.com/atmeband"
				title="ATME"
				target="_blank"
				style="color: #cccccc; text-decoration: none;">ATME</a
			>
			·
			<a
				href="https://soundcloud.com/atmeband/atme-forgiving-myself"
				title="ATME - α.Forgiving Myself"
				target="_blank"
				style="color: #cccccc; text-decoration: none;">ATME - α.Forgiving Myself</a
			>
		</div>
	</div>
</main>

<style lang="scss">
	:global(body) {
		margin: 0;
		padding: 0;
		font-family: sans-serif;
	}
	main {
		display: grid;
		width: 100%;
		height: 100vh;
		align-items: center;
		justify-items: center;
		grid-template-columns: repeat(2, 1fr);

		.soundcloud-preview {
			grid-column: 1 / -1;
		}
	}
</style>
