<script>
    import ExerciseStartBox from "$lib/components/ExerciseStartBox.svelte";

    export let title = "";
    export let exercises = [];
    export let prev = "";
    export let next = "";
</script>

<div class="text-center mb-4">
    <h1 class="mb-4">{title}</h1>

    {#each exercises as exercise}
        <ExerciseStartBox exercise={exercise.name} timer={exercise.time} />
    {/each}
</div>

<div class="d-flex">
    {#if prev.length > 0}<a href={prev} sveltekit:prefetch class="btn btn-secondary col mx-2">Prev</a>{/if}
    {#if next.length > 0}<a href={next} sveltekit:prefetch class="btn btn-secondary col mx-2">Next</a>{/if}
</div>