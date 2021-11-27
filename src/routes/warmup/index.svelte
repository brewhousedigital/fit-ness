<script>
    import ExerciseContainer from "$lib/components/ExerciseContainer.svelte";

    let exercises = [
        {name: "General Stretch", time: 30},
        {name: "Hamstring", time: 30},
        {name: "Wrist Circles", time: 30},
        {name: "Wrist Pressing", time: 30},
        {name: "Back Circles Clockwise", time: 30},
        {name: "Back Circles Counter Clockwise", time: 30},
        {name: "Walk Into Squat", time: 30},
    ];
</script>


<ExerciseContainer title="🧘‍♂️ Warmup 🧘‍♂️" {exercises} prev="" next="" />