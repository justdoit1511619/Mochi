<svelte:head>
    <title>About</title>
    <meta name="description" content="About this app" />
</svelte:head>

<div class="fullscreen-frame">
    <iframe src="/happy birtday.html" frameborder="0"></iframe>
</div>

<style>
.fullscreen-frame {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    margin: 0;
    padding: 0;
    z-index: 9999;
    display: flex;
    align-items: center;
    justify-content: center;
}
.fullscreen-frame iframe {
    width: 90vw;
    height: 90vh;
    border: none;
    display: block;
    box-shadow: 0 0 24px rgba(0,0,0,0.2);
    border-radius: 16px;
    background: #fff;
}
</style>
