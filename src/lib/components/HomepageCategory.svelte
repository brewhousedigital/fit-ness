<script>
    export let title = "";
    export let description = "";
    export let link = "";
</script>


<style>
    .exercise-box {
        border: 1px solid #eee;
        padding: 40px;
        position: relative;
    }

    a {
        color: inherit;
    }
</style>


<div class="col-lg-4">
    <div class="exercise-box">
        <h1 class="card-title">{title}</h1>
        <p class="card-text">{description}</p>
        <a href={link} sveltekit:prefetch class="stretched-link">Start</a>
    </div>
</div><!-- end col -->