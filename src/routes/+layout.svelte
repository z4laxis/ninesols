<script>
	import { MetaTags } from 'svelte-meta-tags';
	import favicon from '$lib/assets/favicon.png';

	let { children } = $props();
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

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}
