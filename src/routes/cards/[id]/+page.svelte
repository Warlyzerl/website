<script context="module">
    import axios from "axios";
    import { redirect} from '@sveltejs/kit'
    export const hydrate = false;
// @ts-nocheck
    /**
	 * @param {string} [id]
	 */
    export async function loadData(id) {
        try {
            const res = await axios.get(`https://jsonplaceholder.typicode.com/posts/${id}`, {
                headers: {},
                params: {}
            }); 
            const guide = res.data
            return {
                props: {
                    guide
                }
            }
        } catch (err) {
            console.log(err);
            throw redirect(301, '/cards')
        }
    };
</script>

<script>
    import { page } from '$app/stores';
    import {onMount} from 'svelte';
    import { goto } from "$app/navigation";
    /**
	 * @type {{ title: any; body: any; }}
	 */
    let guide
    const id = $page.params.id
    onMount(async () => {
        try {
            const res = await loadData(id);
            guide = res.props?.guide
        } catch (err){
            goto('/')
        }
     })
</script>

<div class="guide">
    {#if guide}
    <h2>{guide.title}</h2>
    <p>{guide.body}</p>
    {:else}
        <p>Loading...</p>
    {/if}
</div>

<style>
    .guide {
        margin-top: 40px;
        padding: 10px;
        border: 1px dotted rgba(255, 255, 255, 0.2)
    }
</style>