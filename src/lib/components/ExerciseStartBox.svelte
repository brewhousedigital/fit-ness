<script>
    import ExerciseCompletedAnimation from "$lib/components/ExerciseCompletedAnimation.svelte";
    import {completionSpeech} from "$lib/stores";

    let complete = false;
    export let exercise = "Wrist Circles";
    export let timer = 3;

    function startCountdown() {
        let countdown = setInterval(() => {
            timer--;

            // 5 seconds left shoutout
            if(timer === 5) {
                $completionSpeech.text = "5 seconds left";
                window.speechSynthesis.speak($completionSpeech);
            }

            // 2 seconds left shoutout
            if(timer === 2) {
                $completionSpeech.text = "2 seconds left";
                window.speechSynthesis.speak($completionSpeech);
            }

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

    <ExerciseCompletedAnimation show={complete} />
</div>