<script>
    let { text, onclick } = $props();
    let hovered = $state(false);
</script>

<style>
    @font-face {
        font-family: 'Noto Sans';
        src: url('$lib/assets/fonts/NotoSans-Russian-Regular.ttf') format('truetype');
    }

    button {
        background: none;
        border: none;
        color: #ecd89a;
        font-size: 1.95rem;
        text-align: left;
        margin-bottom: 4px;
        cursor: pointer;
        opacity: 0.5;
        font-family: 'Noto Sans', sans-serif;
        transition: font-size 0.1s ease, opacity 0.1s ease;
    }

    button.hovered {
        font-size: 2.1rem;
        opacity: 1;
    }
</style>

<button
    class:hovered={hovered}
    onclick={onclick}
    onmouseenter={() => hovered = true}
    onmouseleave={() => hovered = false}
>
    {text}
</button>