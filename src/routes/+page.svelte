<script>
  import { MetaTags } from 'svelte-meta-tags';
  import logo from '$lib/assets/img/logo.png';
  import sandbox from '$lib/assets/img/bg/True_Ending_BG.jpg';
</script>

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

<img alt="The project logo" src={logo} style="width: 100%; height: auto;" />S