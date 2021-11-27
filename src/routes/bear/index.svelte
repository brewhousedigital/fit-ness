<script>
    import ExerciseContainer from "$lib/exercises/ExerciseContainer.svelte";

    let exercises = [
        {name: "General Stretch", time: 3},
        {name: "Hamstring", time: 30},
        {name: "Wrist Circles", time: 30},
        {name: "Wrist Pressing", time: 30},
        {name: "Back Circles 1/2", time: 30},
        {name: "Back Circles 2/2", time: 30},
        {name: "Walk Into Squat", time: 30},
    ];
</script>


<ExerciseContainer title="🐻 Warmup 🐻" {exercises} prev="" next="/bear/movement" />