<script>
    export let title;
    let exercise = {
        activity: "",
        sets: 4,
        reps: 10,
    }

    let exercises = [];

    function handleSubmit(event) {
        exercises = [...exercises, {... exercise}];
        console.log(exercises);
    }
</script>
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Rubik', sans-serif;
    }
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 1rem;
    }
    h2 {
        text-align: center;
    }
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 1rem;
    }
    .item {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 0.2rem;
    }
    .item label {
        width: 100%;
    }
    input {
        padding: 0.3rem 0.5rem;
        border-radius: 5px;
        border: none;
        outline: none;
    }
    button {
        padding: 0.5rem 1rem;
        border-radius: 5px;
        border: none;
        outline: none;
        background-color: #7adec9;
        color: white;
        cursor: pointer;
    }
</style>

<div class="container">
    <h2>{title}</h2>
    <div>
        <form on:submit|preventDefault={handleSubmit}>
            <div class="item">
                <label for="activity">Activité</label>
                <input type="text" id="activity" bind:value={exercise.activity}>
            </div>
            <div class="item">
                <label for="sets">Séries</label>
                <input type="number" id="sets" bind:value={exercise.sets}>
            </div>
            <div class="item">
                <label for="reps">Répétitions</label>
                <input type="number" id="reps" bind:value={exercise.reps}>
            </div>
            <button type="submit">Ajouter</button>
        </form>
    </div>
</div>