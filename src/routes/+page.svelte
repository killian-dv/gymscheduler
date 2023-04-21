<script>
    import TrainingDay from "./components/TrainingDay.svelte";
</script>
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Rubik', sans-serif;
    }
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 1rem;
    }
    h1 {
        color: #fb771a;
    }
    h1, h2, h3 {
        text-align: center;
    }
</style>
<main>
    <h1>GymScheduler</h1>
    <p>Voici ma première app avec Svelte</p>
    <TrainingDay />
</main>
