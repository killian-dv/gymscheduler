<script>
    import { onMount } from "svelte";
    export let summary;
    let formattedData;
    let isDataFormatted = false;

    onMount(() => {
        prepareSummary();
    });

    function prepareSummary () {
        // acc looks like {"day 1": [], "day 2": [], "day 3": [] }
        // curr looks like {activity: "squat", sets: 4, reps: 10, title 'day 1'}
        formattedData = summary.reduce((acc, curr) => {
        if (Object.keys(acc).includes(curr.title)) {
            acc[curr.title] = [...acc[curr.title], curr];
        } else {
            acc[curr.title] = [curr];
        }
            return acc;
        }, {});
        isDataFormatted = true;
        console.log(formattedData);
    }
</script>
<style></style>

{#if isDataFormatted}
    <h2>Summary</h2>
    {#if summary.length}
        {#each Object.keys(formattedData) as day}
            <h2>{day}</h2>
            {#each formattedData[day] as ex}
                {ex.activity}: {ex.sets} séries de {ex.reps}<br>
            {/each}
        {/each}
    {:else}
    <div>Données manquantes : ajoutez un exercice</div>
    {/if}
{/if}

