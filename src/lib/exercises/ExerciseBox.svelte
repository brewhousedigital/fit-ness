<script>
    import CompletedAnimation from "$lib/exercises/CompletedAnimation.svelte";

    let complete = false;
    export let exercise = "Wrist Circles";
    export let timer = 3;

    function startCountdown() {
        let countdown = setInterval(() => {
            timer--;

            // Clear interval when done
            if(timer === 0) {
                clearInterval(countdown);
                complete = true;
            }
        }, 1000)
    }
</script>


<style>
    .exercise {
        border: 1px solid #464646;
        width: calc(50% - 16px);
        display: inline-block;
        margin-bottom: 12px;
        margin-left: 8px;
        margin-right: 8px;
        padding: 10px 8px;
    }

    .box-done h2,
    .box-done h3,
    .box-done p {
        opacity: 0.5;
    }

    .done {
        text-decoration: line-through;
    }
</style>


<div class="exercise shadow {complete ? 'box-done' : ''}">
    <p class={complete ? 'done' : ''}>{exercise}</p>

    <h3 class="display-1">{timer}<span class="small">s</span></h3>

    <p><button class="btn btn-primary btn-lg px-4" on:click={startCountdown}>Start</button></p>

    <CompletedAnimation show={complete} />
</div>