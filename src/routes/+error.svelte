<script>
    import { page } from '$app/stores'
    export let message = $page.url + ' ' + $page.error?.message
</script>

<div class="error">
    <h2>Error</h2>
    <p>{message}</p>
    <a href="/">Home</a>
</div>

<style>
    .error {
        text-align: center;
        margin-bottom: 60px;
    }
</style>