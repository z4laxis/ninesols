<script>
  import { MetaTags } from 'svelte-meta-tags';

  import logo from '$lib/assets/img/logo.png';
  import bg from '$lib/assets/img/bg/Normal_BG.jpg';
  import MenuButton from '$lib/MenuButton.svelte';

  const menuItems = [
    { text: 'Start Game', action: play },
    { text: 'Options', action: settings },
    { text: 'Credits', action: credits },
    { text: 'Discord', action: discord },
    { text: 'Exit Game', action: exitGame }
  ];

  let selectedIndex = $state(0);

  function play() {
    console.log('Play');
  }

  function settings() {
    console.log('Settings');
  }

  function credits() {
    console.log('Credits');
  }

  function discord() {
    window.open('https://discord.gg/redcandlegames', '_blank', 'noopener,noreferrer');
  }

  function exitGame() {
    history.back();
  }

  function activateSelected() {
    menuItems[selectedIndex].action();
  }

  function handleKeydown(event) {
    if (event.key === 'ArrowDown' || event.key === 's' || event.key === 'S') {
      event.preventDefault();
      selectedIndex = (selectedIndex + 1) % menuItems.length;
    }

    if (event.key === 'ArrowUp' || event.key === 'w' || event.key === 'W') {
      event.preventDefault();
      selectedIndex = (selectedIndex - 1 + menuItems.length) % menuItems.length;
    }

    if (event.key === 'Enter' || event.key === 'z' || event.key === 'Z' || event.key === ' ') {
      event.preventDefault();
      activateSelected();
    }
  }
</script>

<svelte:window onkeydown={handleKeydown} />

<MetaTags
  title="Nine Sols"
  description="Nine Sols main menu recreation."
  canonical="https://example.com/"
  openGraph={{
    title: 'Nine Sols',
    description: 'Nine Sols main menu recreation.',
    images: [{ url: logo, width: 1200, height: 630, alt: 'Nine Sols' }]
  }}
/>

<svelte:head>
  <title>Nine Sols</title>
</svelte:head>

<main class="menu-screen">
  <img class="background" src={bg} alt="" aria-hidden="true" />
  <div class="vignette" aria-hidden="true"></div>
  <div class="bottom-fade" aria-hidden="true"></div>

  <img class="logo" src={logo} alt="Nine Sols" />

  <nav class="menu-buttons" aria-label="Main menu">
    {#each menuItems as item, index}
      <MenuButton
        text={item.text}
        active={selectedIndex === index}
        onclick={item.action}
        onhover={() => selectedIndex = index}
      />
    {/each}
  </nav>

  <div class="controls" aria-hidden="true">
    <span><b>Z</b> Confirm</span>
    <span><b>X</b> Back</span>
  </div>
</main>

<style>
  :global(html),
  :global(body) {
    width: 100%;
    height: 100%;
    margin: 0;
    overflow: hidden;
    background: #07151a;
  }

  :global(body) {
    font-family: 'Noto Sans', sans-serif;
  }

  :global(*) {
    box-sizing: border-box;
  }

  .menu-screen {
    position: relative;
    width: 100vw;
    height: 100vh;
    min-height: 540px;
    overflow: hidden;
    background: #07151a;
    isolation: isolate;
  }

  .background {
    position: absolute;
    inset: 0;
    z-index: -3;
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
    user-select: none;
    -webkit-user-drag: none;
  }

  .vignette {
    position: absolute;
    inset: 0;
    z-index: -2;
    pointer-events: none;
    background:
      radial-gradient(ellipse at 42% 42%, transparent 18%, rgba(0, 0, 0, 0.08) 48%, rgba(0, 0, 0, 0.58) 100%),
      linear-gradient(90deg, rgba(0, 0, 0, 0.38) 0%, rgba(0, 0, 0, 0.12) 34%, rgba(0, 0, 0, 0.02) 68%, rgba(0, 0, 0, 0.18) 100%);
  }

  .bottom-fade {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    height: 19%;
    z-index: -1;
    pointer-events: none;
    background: linear-gradient(to bottom, transparent, rgba(3, 15, 27, 0.78));
  }

  .logo {
    position: absolute;
    z-index: 1;
    top: 9.5%;
    left: 11.5%;
    width: clamp(180px, 17.5vw, 336px);
    height: auto;
    user-select: none;
    -webkit-user-drag: none;
  }

  .menu-buttons {
    position: absolute;
    z-index: 2;
    top: 53.5%;
    left: 11.7%;
    display: flex;
    width: max-content;
    flex-direction: column;
    align-items: flex-start;
  }

  .controls {
    position: absolute;
    z-index: 2;
    left: 11.7%;
    bottom: 4.5%;
    display: flex;
    gap: 1.25rem;
    color: rgba(236, 216, 154, 0.48);
    font-size: clamp(0.65rem, 0.7vw, 0.82rem);
    letter-spacing: 0.01em;
    pointer-events: none;
  }

  .controls b {
    color: rgba(236, 216, 154, 0.72);
    font-weight: 500;
  }

  @media (max-width: 700px) {
    .logo {
      top: 8%;
      left: 9%;
      width: 45vw;
    }

    .menu-buttons {
      top: 51%;
      left: 9%;
    }

    .controls {
      left: 9%;
      bottom: 3%;
    }
  }
</style>
