<script>
    import { fade } from 'svelte/transition';
    import {completionSpeech} from "$lib/stores";

    export let show = false;

    $: {
        if(show) {
            // Show the animation when the parent passes "true"
            setTimeout(() => {show = false;}, 2000);

            try {
                window.navigator.vibrate([200, 100, 200, 100, 200]);
            }
            catch(error) {console.log("iOS doesnt support vibrate")}

            $completionSpeech.text = "Ok you got it!";
            window.speechSynthesis.speak($completionSpeech);
        }
    }
</script>


<style>
    img {
        position: absolute;
        width: 100vw;
        height: 100vh;
        top: 0;
        left: 0;
    }
</style>

{#if show}
    <div in:fade="{{delay: 0, duration: 1000}}" out:fade="{{delay: 0, duration: 1000}}">
        <img src="/giphy.webp" alt="Completed Animation" class="">
    </div>
{/if}