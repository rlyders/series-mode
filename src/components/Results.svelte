<script>
    export let nums = "";
    let mostFrequentKeyVal = [0, 0];
    $: mostFrequentKeyVal = getMode(nums);
    $: entered = mostFrequentKeyVal && mostFrequentKeyVal[1] > 0;

    function getFrequencyMap(nums) {
        return [...nums].reduce((counts, num) => {
            counts.set(num, counts.get(num) + 1 || 1);
            return counts;
        }, new Map());
    }

    function getMode(nums) {
        return [...getFrequencyMap(nums)].reduce(
            (mostFrequent, keyVal) => {
                if (keyVal[1] > mostFrequent[1]) {
                    return [[keyVal[0]], keyVal[1]];
                } else if (keyVal[1] == mostFrequent[1]) {
                    return [[...mostFrequent[0], keyVal[0]], mostFrequent[1]];
                } else {
                    return mostFrequent;
                }
            },
            [[], 0]
        );
    }
</script>

<div class="d-flex flex-column">
    <div
        class="d-flex flex-column justify-content-center h5 {entered
            ? ''
            : 'invisible'}"
    >
        <div class="d-flex p-2 justify-content-center">
            Mode{mostFrequentKeyVal[0].length > 1 ? "s" : ""}:&nbsp;
            <span class="results">{mostFrequentKeyVal[0].sort()}</span>
        </div>
        <div class="d-flex p-2 justify-content-center">
            Occurrences:&nbsp;<span class="results"
                >{mostFrequentKeyVal[1]}</span
            >
        </div>
    </div>
</div>

<style>
    .results {
        color: #333;
        font-weight: bolder;
    }
</style>
