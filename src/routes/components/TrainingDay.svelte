<script>
    let nbOfDays = [
        {id: 1, text: "1 jour", value: [1]},
        {id: 2, text: "2 jours", value: [1, 2]},
        {id: 3, text: "3 jours", value: [1, 2, 3]},
        {id: 4, text: "4 jours", value: [1, 2, 3, 4]},
        {id: 5, text: "5 jours", value: [1, 2, 3, 4, 5]},
        {id: 6, text: "6 jours", value: [1, 2, 3, 4, 5, 6]},
        {id: 7, text: "7 jours", value: [1, 2, 3, 4, 5, 6, 7]},
    ];
    let nbDaysTrainingPerWeek;

</script>

<form>
    <select bind:value={nbDaysTrainingPerWeek}>
    {#each nbOfDays as day (day.id)}
        <option value={day}>{day.text} par semaine</option>
    {/each}
    </select>
</form>
{JSON.stringify(nbDaysTrainingPerWeek)}
