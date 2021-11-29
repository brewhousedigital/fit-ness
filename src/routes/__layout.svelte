<script>
    import "$lib/css/_bootstrap.css";
    import {onMount} from "svelte";
    import {completionSpeech} from "$lib/stores";

    let loading = true;

    let password = "8080";
    let passwordEntry = "";
    let authenticated = false;

    onMount(() => {
        try {
            navigator.wakeLock.request('screen');
        }
        catch(error) {console.log("iOS doesnt support wakeLock")}

        const msg = new SpeechSynthesisUtterance();
        const voices = window.speechSynthesis.getVoices();
        msg.voice = voices[5];
        msg.lang = 'en';
        completionSpeech.set(msg);

        if(localStorage.getItem("fitness-authenticated") !== null) {
            authenticated = true;
        }

        loading = false;
    })

    function validatePassword() {
        if(passwordEntry === password) {
            authenticated = true;
            localStorage.setItem("fitness-authenticated", "true");
        } else {
            passwordEntry = "";
        }
    }
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

<div class="container" style={loading ? "opacity: 0;" : ""}>
    {#if authenticated}

        <nav class="mb-5">
            <a href="/">Home</a>
        </nav>

        <slot></slot>

    {:else}

        <div class="text-center">
            <h1>Password</h1>
            <input class="form-control mb-2" type="password" bind:value={passwordEntry}>
            <button class="btn btn-primary px-5" on:click={validatePassword}>Go!</button>
        </div>

    {/if}
</div>