<script>
    let { text, onclick, active = false, onhover } = $props();
    let hovered = $state(false);
</script>

<style>
    @font-face {
        font-family: 'Noto Sans';
        src: url('$lib/assets/fonts/NotoSans-Russian-Regular.ttf') format('truetype');
    }

    .button-wrap {
        position: relative;
        display: block;
        width: max-content;
        margin-bottom: 2px;
        padding-left: 17px;
    }

    .button-wrap::before {
        content: '';
        position: absolute;
        left: 2px;
        top: 17%;
        width: 1px;
        height: 66%;
        background: rgba(236, 216, 154, 0.56);
        transition: height 0.1s ease, top 0.1s ease, background 0.1s ease;
    }

    .button-wrap::after {
        content: '';
        position: absolute;
        z-index: -1;
        inset: -3px -10px -3px -6px;
        border: 2px solid #d83b35;
        border-radius: 999px;
        opacity: 0;
        transform: rotate(-1deg) scale(0.98);
        transition: opacity 0.08s ease, transform 0.08s ease;
        pointer-events: none;
    }

    .button-wrap.hovered::before,
    .button-wrap.active::before {
        top: 13%;
        height: 74%;
        background: #ecd89a;
    }

    .button-wrap.hovered::after,
    .button-wrap.active::after {
        opacity: 1;
        transform: rotate(-1deg) scale(1);
    }

    button {
        display: block;
        padding: 0;
        margin: 0;
        border: 0;
        outline: 0;
        background: none;
        color: #ecd89a;
        font-family: 'Noto Sans', sans-serif;
        font-size: clamp(1.15rem, 1.72vw, 2rem);
        font-weight: 400;
        line-height: 1.15;
        text-align: left;
        white-space: nowrap;
        cursor: pointer;
        opacity: 0.48;
        transform-origin: left center;
        transition: font-size 0.1s ease, opacity 0.1s ease, transform 0.1s ease;
    }

    .button-wrap.hovered button,
    .button-wrap.active button {
        opacity: 1;
        transform: translateX(1px);
    }

    button:focus-visible {
        outline: none;
    }
</style>

<div
    class="button-wrap"
    class:hovered={hovered}
    class:active={active}
    onmouseenter={() => {
        hovered = true;
        onhover?.();
    }}
    onmouseleave={() => hovered = false}
>
    <button onclick={onclick} aria-label={text}>
        {text}
    </button>
</div>
