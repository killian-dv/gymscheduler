<script>
    export let summary;
    export let days;
    let formattedData;
    let isDataFormatted = false;

    function prepareSummary () {
        // acc looks like {"day 1": [], "day 2": [], "day 3": [] }
        // curr looks like {activity: "squat", sets: 4, reps: 10, title 'day 1'}
        formattedData = summary.reduce((acc, curr) => {
            if (Object.keys(acc).includes(curr.title)) {
                acc[curr.title] = [...acc[curr.title], curr.exercises];
            } else {
                acc[curr.title] = [curr];
            }
            return acc
        }, {});
        isDataFormatted = true;
        console.log()
    }
    prepareSummary();
</script>
<style></style>

<h2>Résumé</h2>
{#if isDataFormatted}
    {formattedData}
{/if}