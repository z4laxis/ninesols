<script>
  import { MetaTags } from 'svelte-meta-tags';

  import logo from '$lib/assets/img/logo.png';
  import bg from '$lib/assets/img/bg/New_Game_BG.jpg';
  import sandbox from '$lib/assets/img/bg/Normal_BG.jpg';
</script>

<style>
  :global(body) {
    margin: 0;
    overflow: hidden;
  }

  .logo {
    width: 13%;
    position: absolute;
    z-index: 1;
    left: 13%;
    top: 11%;
  }
</style>

<MetaTags
  title="Nine Sols"
  description="A short description of this page."
  canonical="https://example.com/my-page"
  openGraph={{
    title: 'Nine Sols',
    description: 'A short description of this page.',
    images: [{ url: 'https://example.com/og-image.jpg', width: 1200, height: 630, alt: 'Nine Sols' }]
  }}
/>

<img alt="Nine Sols Logo" src={logo} class="logo" />
<img alt="Sandbox Background" src="https://www.gameuidatabase.com/uploads/Nine-Sols12282024-070345-33433.jpg" style="width: 100%; height: auto;" />
