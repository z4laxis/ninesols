<svelte:head>
  <title>Nine Sols</title>
</svelte:head>

<svelte:window onkeydown={handleKeydown} />

<MetaTags
  title="Nine Sols"
  description="Nine Sols unofficial website."
  canonical="https://example.com/"
  openGraph={{
    title: 'Nine Sols',
    description: 'Nine Sols unofficial website.',
    images: [{ url: logo, width: 1200, height: 630, alt: 'Nine Sols' }]
  }}
/>

<div class="credits">
    <h1>Credits</h1>

    <div class="credit-section">
        <div class="credit-header">
            <span>網站</span>
            <span>Website</span>
        </div>

        <div class="credit-row">
            <span>札拉西斯</span>
            <span>Zalaxis</span>
        </div>

        <div class="credit-row">
            <span>德羅特孔</span>
            <span>XDrotkon</span>
        </div>
    </div>
    
    <br>

    <div class="credit-section">
        <div class="credit-header">
            <span>製作人</span>
            <span>Producer</span>
        </div>

        <div class="credit-row">
            <span>楊邁維</span>
            <span>Vincent Yang</span>
        </div>
    </div>

    <br>

    <div class="credit-section">
        <div class="credit-header">
            <span>創作群</span>
            <span>Creators</span>
        </div>

        <div class="credit-row">
            <span>王光昊</span>
            <span>Light Wang</span>
        </div>

        <div class="credit-row">
            <span>王瀚宇</span>
            <span>Henry Wang</span>
        </div>

        <div class="credit-row">
            <span>何霧君</span>
            <span>Pege Ho</span>
        </div>

        <div class="credit-row">
            <span>姚舜庭</span>
            <span>Coffee Yao</span>
        </div>

        <div class="credit-row">
            <span>陳敬恆</span>
            <span>Finger Chen</span>
        </div>

        <div class="credit-row">
            <span>徐嘉陞</span>
            <span>Smiler Hsu</span>
        </div>

        <div class="credit-row">
            <span>張兆鴻</span>
            <span>Tata Cheong</span>
        </div>

        <div class="credit-row">
            <span>詹易衡</span>
            <span>Jerryee Chan</span>
        </div>

        <div class="credit-row">
            <span>楊邁維</span>
            <span>Vincent Yang</span>
        </div>

        <div class="credit-row">
            <span>簡廷任</span>
            <span>Minus Chien</span>
        </div>

        <div class="credit-row">
            <span>黨傳翔</span>
            <span>Dang Chuan-Hsiang</span>
        </div>

        <div class="credit-row">
            <span>林昇翰</span>
            <span>Sheng-Han Lin</span>
        </div>

        <div class="credit-row">
            <span>江東昱</span>
            <span>Doy Chiang</span>
        </div>
    </div>

    <br>

    <div class="credit-section">
        <div class="credit-header">
            <span>作曲家</span>
            <span>Composer</span>
        </div>

        <div class="credit-row">
            <span>無聲聚會</span>
            <span>Silence Party</span>
        </div>
    </div>

    <br>

    <div class="credit-section">
        <div class="credit-header">
            <span>發行商</span>
            <span>Publisher</span>
        </div>

        <div class="credit-row">
            <span>赤燭遊戲</span>
            <span>RedCandleGames</span>
        </div>
    </div>
</div>

<div class="menu-screen">
  <img class="background" src={bg} alt="" aria-hidden="true" />
  <div style="display: contents"><div style="position: absolute;width: 100%;height: 100%;top: 0;left: 0;box-shadow: inset 10em 1em 100px #000;overflow: hidden;z-index: 1;pointer-events: none;opacity: 0;"></div> <div style="position: absolute;width: 100%;height: 100%;top: 0;/*! left: 5%; */box-shadow: inset 10em 1em 1000px #000;overflow: hidden;z-index: 1;pointer-events: none;/*! opacity: 0.2; *//*! transform: scaleX(1.1); */background: rgba(0, 0, 0, 0.1);"></div></div>

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
    <span><b>E</b> Confirm</span>
    <span><b>X</b> Back</span>
  </div>
</div>

<style>
  :global(html),
  :global(body) {
    width: 100%;
    height: 100%;
    margin: 0;
    overflow: hidden;
    background: #000;
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
  z-index: 1;
  width: 13%;
  position: absolute;
  top: 11%;
  left: 13%;
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

  .credits {
    width: 100%;
    height: 100%;
    text-align: center;
    color: #fff;
    background: #000;
    display: none;
  }

  .credits h1 {
    margin: 40px 0 40px;
    font-size: 30px;
    font-weight: 400;
  }

  .credit-section {
  width: 275px;
  margin: 0 auto;
  position: relative;
  left: 50px;
  }

  .credit-header,
  .credit-row {
    display: grid;
    grid-template-columns: 120px 1fr;
    text-align: left;
  }

  .credit-header {
    margin-bottom: 4px;
    color: #6bff85;
  }

  .credit-row {
    line-height: 1.5;
  }

  .credit-header span:first-child,
  .credit-row span:first-child {
    text-align: right;
    padding-right: 50px;
  }

  .credit-header span:last-child,
  .credit-row span:last-child {
    text-align: left;
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
    if (document.querySelector(".credits").style.display === "block") {
      document.querySelector(".credits").style.display = "none";
    } else {
      document.querySelector(".credits").style.display = "block";
    }
  }

  function discord() {
    window.open('https://discord.gg/redcandlegames', '_blank', 'noopener,noreferrer');
  }

  function exitGame() {
    if (history.length > 2) {
      window.History.back();
    } else {
      window.History.replaceState(null, null, '/');
    }
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

    if (event.key === 'X' || event.key === 'x') {
      event.preventDefault();
      credits();
    }

    if (event.key === 'Enter' || event.key === 'z' || event.key === 'Z' || event.key === ' ') {
      event.preventDefault();
      activateSelected();
    }
  }
</script>