<script>
    import ExerciseContainer from "$lib/exercises/ExerciseContainer.svelte";

    let exercises = [
        {name: "A Frame", time: 15},
        {name: "Bear Walk", time: 30},
        {name: "Bear Walk", time: 30},
        {name: "Bear Walk", time: 30},
    ];
</script>


<ExerciseContainer title="🐻 Movement 🐻" {exercises} prev="/bear" next="" />


