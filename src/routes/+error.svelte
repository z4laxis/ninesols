<script>
  import { page } from '$app/stores';
</script>

{#if $page.status === 404}
  <h1>404 - Page Not Found</h1>
  <p>Sorry, the page you're looking for doesn't exist.</p>
{:else}
  <h1>{$page.status}: {$page.error?.message}</h1>
{/if}