<script>
	import Title from "$lib/title.svelte";
    import '../styles/global.css'
</script>

<header>
    <nav>
        <Title title="Willie's Page"/>
    <div class="links">
        <a href="/about">About willie</a>
        <a href="/cards">cards</a>
    </div>
    </nav>
</header>
<main>
    <slot></slot>
</main>
<footer>
    <p>5'11" 193lbs</p>
</footer>

<style>
    header {
        text-align: center;
        background: rgba(0, 0, 0, 0.1);
    }
    main {
        max-width: 960px;
        margin: 20px auto;
    }
    footer {
        text-align: center;
    }
    .links {
        margin-right: 10px;
        margin-left: auto;
    }
    a {
        margin-left: 10px;
    }
    nav {
        display: flex;
        align-items: center;
        max-width: 960px;
        margin: 0 auto;
    }
</style>