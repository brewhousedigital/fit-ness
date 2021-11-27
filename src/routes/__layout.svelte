<script>
    import "$lib/css/_bootstrap.css";
    import {onMount} from "svelte";
    import {completionSpeech} from "$lib/stores";

    onMount(() => {
        navigator.wakeLock.request('screen');

        const msg = new SpeechSynthesisUtterance();
        const voices = window.speechSynthesis.getVoices();
        msg.voice = voices[5];
        msg.lang = 'en';
        msg.text = "Ok you got it!";
        completionSpeech.set(msg);
    })
</script>


<style>
    :global(body) {
        background-color: #222;
        color: #eee;
        min-height: 100vh;
        font-size: 18px;
    }
    :global(#svelte) {
        /*min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;*/
    }

    a {
        color: inherit;
        font-weight: 700;
        font-size: 24px;
    }
</style>


<div class="container">
    <nav class="mb-5">
        <a href="/">Home</a>
    </nav>

    <slot></slot>
</div>