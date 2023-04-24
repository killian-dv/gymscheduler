<script>
    import TrainingDayDetails from "./TrainingDayDetails.svelte";
    import TrainingWeekSummary from "./TrainingWeekSummary.svelte";

    let nbOfDays = [
        {id: 1, text: "1 jour", value: [1]},
        {id: 2, text: "2 jours", value: [1, 2]},
        {id: 3, text: "3 jours", value: [1, 2, 3]},
        {id: 4, text: "4 jours", value: [1, 2, 3, 4]},
        {id: 5, text: "5 jours", value: [1, 2, 3, 4, 5]},
        {id: 6, text: "6 jours", value: [1, 2, 3, 4, 5, 6]},
        {id: 7, text: "7 jours", value: [1, 2, 3, 4, 5, 6, 7]},
    ];
    let summary = [];
    let isSummaryReady = false;
    let nbDaysTrainingPerWeek;

    function handleNewExercise(event) {
        console.log(event.detail);
        summary = [...summary, event.detail];
        isSummaryReady = false
    }

    function generateSummary() {
        isSummaryReady = true;
    }
</script>

<style>
    .all-days {
        display: grid;
        width: 90%;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(auto, 1fr);
        grid-column-gap: 1rem;
        grid-row-gap: 1rem;
        background-color: #efefef;
        padding: 1rem;
        border-radius: 1rem;
    }
    .one-day {
        background-color: #fb771a;
        padding: 1rem;
        border-radius: 1rem;
        color: white;
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

<form>
    <select bind:value={nbDaysTrainingPerWeek}>
    {#each nbOfDays as day (day.id)}
        <option value={day}>{day.text} par semaine</option>
    {/each}
    </select>
</form>
{#if nbDaysTrainingPerWeek}
    <div class="all-days">
        {#each nbDaysTrainingPerWeek.value as dayNumber, i}
            <div class="one-day">
                <TrainingDayDetails title={`Jour ${++i}`} on:add-exercise={handleNewExercise} />
            </div>
        {/each}
    </div>
    {#if isSummaryReady}
    <TrainingWeekSummary summary={summary} days={nbDaysTrainingPerWeek.value.length}/>
    {/if}
    <button on:click={generateSummary}>Générer mon résumé</button>
{/if}

