<script lang="ts">
    import { onDestroy, onMount } from "svelte";
    import { fade } from "svelte/transition";

    const images = [
        "background1.jpg",
        "background2.jpg",
        "background3.jpg",
        "background4.jpg",
    ];
    let index = 0;
    let interval: number;
    onMount(() => {
        interval = setInterval(() => {
            index++;
            if (index === images.length) {
                index = 0;
            }
        }, 3000);
    });
    onDestroy(() => clearInterval(interval));
</script>

{#each images as image, idx (idx)}
    {#if idx == index}
        <div
            transition:fade={{ duration: 300 }}
            class="h-screen fixed inset-0 bg-no-repeat bg-cover bg-center"
            style="background-image: url('images/{image}');"
        ></div>
    {/if}
{/each}
