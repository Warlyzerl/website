<script context="module">
    import axios from "axios";
// @ts-nocheck
    export async function loadData() {
        try {
            const res = await axios.get('https://jsonplaceholder.typicode.com/posts', {
                headers: {},
                params: {}
            }); 
            const guides = await res.data
            console.log("?")
            console.log(res)
            console.log(guides)
            return {
                props: {
                    guides
                }
            }
        } catch (err) {
            console.log(err);
            return {
                status: 500,
                error: new Error('Uh oh')
            }
        }
    };
</script>

<script>
    import {onMount} from 'svelte';
    /**
	 * @type {any}
	 */
     let guides

     onMount(async () => {
        const res = await loadData();
        guides = res.props?.guides
     })
</script>

<div class="cards">
    <ul>
        {#if Array.isArray(guides)}
            {#each guides as guide}
                <li>
                    <a data-sveltekit-preload-data="hover" href={`/cards/${guide.id}`}>{guide.title}</a>
                </li>
            {/each}
        {:else}
            <p>No guides available</p>
        {/if}
    </ul>
</div>

<style>
    ul {
        list-style-type: none;
        padding: 0;
    }
    a {
        display: inline-block;
        margin-top: 10px;
        padding: 10px;
        border: 1px dotted rgba(255,255,255,0.2)
    }
</style>