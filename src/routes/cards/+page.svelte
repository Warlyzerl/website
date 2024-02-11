<script context="module">
    import axios from "axios";
// @ts-nocheck
    export async function loadData() {
        try {
            const res = await axios.get('https://williezeng.fly.dev/cards/?format=json', {
                headers: {},
                params: {}
            }); 
            const guides = await res.data
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

<div id="cardContainer">
    <div id="cardGrid">
        {#each new Array(78) as _, i}
            <img src="\cardback.png" class="card" alt={`Card ${i + 1}`}>
        {/each}
    </div>
</div>

<style>
    #cardContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #cardGrid {
        display: grid;
        grid-template-columns: repeat(13, 100px);
        gap: 25px;
        grid-row-gap: 0px;
    }

    .card {
        width: 150%;
        margin: 10px;
    }
</style>