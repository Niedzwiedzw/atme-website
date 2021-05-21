<script lang="typescript">
	import MultimediaLink from '/src/components/MultimediaLink.svelte';
	import { multimedia, images } from '../data';

	const nextRandomPhoto = (): string => images[parseInt(`${Math.random() * (images.length - 1)}`)];
  let currentPhotoIndex = 0;
  $: currentPhoto = images[currentPhotoIndex];
  const rotatePhoto = () => {
    currentPhotoIndex = (currentPhotoIndex + 1) % (images.length)
  };

  rotatePhoto();
  
  $: currentPhotoStyle = `url(${currentPhoto})`;
  setInterval(() => {
    rotatePhoto();
  }, 6000);
</script>


<svelte:head>
  <title>
    • ATME •
  </title>


  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width">


  <meta name="description" content="• ATME • Official Website">
  <meta property="og:title" content="• ATME • Official Website">
  <meta property="og:description" content="• ATME • Official Website">
  <meta property="og:image" content="https://www.mywebsite.com/image.jpg">
  <meta property="og:image:alt" content="• ATME • Official Website">
  <meta property="og:type" content="website">
  <meta name="twitter:card" content="summary_large_image">
  <!-- <meta property="og:url" content="https://www.mywebsite.com/page"> -->
  <!-- <link rel="canonical" href="https://www.mywebsite.com/page"> -->

  <link rel="icon" href="/favicon.ico">
  
  <link rel="apple-touch-icon" href="/apple-touch-icon.png">
  <link rel="manifest" href="/my.webmanifest">
  <meta name="theme-color" content="#000000">

	{#each images as image (image)}
		<link rel="prefetch" href={image}/>
	{/each}

</svelte:head>



<main style="--background-image: {currentPhotoStyle}">

  <div style="position: relative" class="main-content">

    <h1 class="title">ATME</h1>


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
    justify-items: center;
    .main-content {
      .title {
        color: white;
        grid-column: 1 / -1;
        font-size: 3rem;
      }
		  grid-template-columns: repeat(2, 1fr);
		  display: grid;
		  width: 100%;
		  height: 100vh;
		  align-items: center;
		  justify-items: center;
      max-width: 40rem;
    }

		.soundcloud-preview {
			grid-column: 1 / -1;
		}
    &::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      transition: background-image 0.6s ease-in-out;
      background-image: var(--background-image);
      background-size: cover;
      filter: grayscale(100%) brightness(40%);
    }
	}
</style>
