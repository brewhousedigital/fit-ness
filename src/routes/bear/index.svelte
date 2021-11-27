<script>
    import ExerciseContainer from "$lib/components/ExerciseContainer.svelte";

    let exercises = [
        {name: "A Frame", time: 15},
        {name: "Bear Walk", time: 30},
    ];

    function addMoreExercises() {
        exercises = [
            ...exercises,
            {name: "Bear Walk", time: 30}
        ]
    }
</script>


<ExerciseContainer title="🐻 Movement 🐻" {exercises} prev="" next="" />


<p class="text-center">
    <button class="btn btn-dark px-5" on:click={addMoreExercises}>Add More Bear</button>
</p>