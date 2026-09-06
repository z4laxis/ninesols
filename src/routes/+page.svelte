<script>
  import { MetaTags } from 'svelte-meta-tags';

  import logo from '$lib/assets/img/logo.png';
  import bg from '$lib/assets/img/bg/Normal_BG.jpg';

  import MenuButton from '$lib/MenuButton.svelte';

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
    open("https://discord.gg/redcandlegames", "_blank");
  }

  function exitGame() {
    history.back()
  }

  function hover(event) {
    event.currentTarget.classList.add('hovered');  
    console.log('Hovered');
    }

  function unhover(event) {
    event.currentTarget.classList.remove('hovered');  
    console.log('Unhovered');
    }
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

  .menu-buttons {
    width: 20%;
    position: absolute;
    z-index: 9;
    left: 12%;
    top: 57.5%;
    display: flex;
    flex-direction: column;
  }
</style>

<MetaTags
  title="Nine Sols"
  description="A short description of this page."
  canonical="https://example.com/my-page"
  openGraph={{
    title: 'Nine Sols',
    description: 'A short description of this page.',
    images: [{ url: {logo}, width: 1200, height: 630, alt: 'Nine Sols' }]
  }}
/>

<div style="display: contents">
  <div style="position: absolute;width: 100%;height: 100%;top: 0;left: 0;box-shadow: inset 10em 1em 100px #000;overflow: hidden;z-index: 1;pointer-events: none;opacity: 0;"></div>
  <div style="position: absolute;width: 100%;height: 100%;top: 0;/*! left: 5%; */box-shadow: inset 10em 1em 1000px #000;overflow: hidden;z-index: 1;pointer-events: none;/*! opacity: 0.2; *//*! transform: scaleX(1.1); */background: rgba(0, 0, 0, 0.1);"></div>
</div>

<div class="menu-buttons">
    <MenuButton text="❘ Start Game" onclick={play} />
    <MenuButton text="❘ Options" onclick={settings} />
    <MenuButton text="❘ Credits" onclick={credits} />
    <MenuButton text="❘ Discord" onclick={discord} />
    <MenuButton text="❘ Exit Game" onclick={exitGame} />
</div>

<img alt="Nine Sols Logo" src={logo} class="logo" />
<!--<img alt="Sandbox Background" src="https://www.gameuidatabase.com/uploads/Nine-Sols12282024-070345-33433.jpg" style="width: 100%; height: 100%; object-fit: cover;" />-->
<img alt="Sandbox Background" src={bg} style="width: 100%; height: 100%; object-fit: cover;" />