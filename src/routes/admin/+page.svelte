<script lang=ts>
    type Robot = {teamKey: string, color: 'blue' | 'red'}
    type Match = [Robot, Robot, Robot, Robot, Robot, Robot]

    const emptyMatch: () => Match = () => [
        {teamKey: '', color: 'red'},
        {teamKey: '', color: 'red'},
        {teamKey: '', color: 'red'},
        {teamKey: '', color: 'blue'},
        {teamKey: '', color: 'blue'},
        {teamKey: '', color: 'blue'},
    ]

    let currentMatch: Match = $state(emptyMatch())
    let nextMatch: Match = $state(emptyMatch())
    let matchKey: string = $state('qm1')
    let scoutQueue: string[] = $state(['scout1', 'scout2'])

    function queueMatch() {
        if (nextMatch.filter((robot) => robot.teamKey == '').length == 0) {
            currentMatch = nextMatch;
            nextMatch = emptyMatch();
        } else {
            console.log("Make sure robts are filled in.")
            console.log(nextMatch.filter((robot) => robot.teamKey == '' ).length)
        }
    }

    function loadMatch() {}

    function clearRobots() {
        currentMatch = emptyMatch();
    }

    function removeScout(i: number) {
        scoutQueue.splice(i, 1)
    } 

    function loadEvent() {}

    function updateData() {}
</script>


<div class="grid grid-cols-4 grid-flow-col gap-2 p-2">
    <!--mathces and stuff-->
    <div class="col-span-2">

        <!--next match-->
        <div class="grid grid-cols-3 grid-flow-col gap-2 text-sm mb-2">
            <input type="text" class="col-span-1 bg-gunmetal rounded p-2" placeholder="Match Key" bind:value={matchKey}>
            <button class="col-span-1 simple bg-gunmetal rounded p-2" onclick={loadMatch}>
                Load Match
            </button>
            <button class="col-span-1 simple bg-gunmetal rounded p-2" onclick={queueMatch}>
                Queue Match
            </button>
        </div>

        <div class="bg-gunmetal p-3 rounded text-center">
            <div class="grid grid-cols-3 grid-rows-2 gap-2">
                {#each currentMatch as {color}, i}
                    <input bind:value={nextMatch[i].teamKey} class="bg-eerie-black rounded p-3 {color == 'red' ? "bg-imperial-red" : "bg-steel-blue"}" placeholder={color+" "+(i%3+1)}>
                {/each}
            </div>
        </div>
        
        <!--current match-->
        <div class="bg-gunmetal p-3 rounded mt-2 text-center">
            <span class="text-center">Current Match</span>
            <div class="grid grid-cols-3 grid-rows-2 gap-2 mt-3">
                {#each currentMatch as {teamKey, color}}
                    <div class="bg-eerie-black rounded p-3">
                        <span class="{color == 'red' ? 'text-imperial-red' : 'text-steel-blue'}">
                            {teamKey == '' ? '-' : teamKey}
                        </span>
                    </div>
                {/each}
            </div>
        </div>
    </div>

    <!--queue-->
    <div class="col-span-1 bg-gunmetal p-3 text-center rounded">
        Scout Queue: {scoutQueue.length}
        <div class="bg-eerie-black rounded mt-2">
            {#each scoutQueue, i}
                <div class="p-1 {i == 0 ? "" : "border-t-1"} border-white/25">
                    <button class="hover:opacity-50 hover:line-through decoration-2 hover:scale-100" onclick={() => removeScout(i)}>
                        {scoutQueue[i]}
                    </button>
                </div>
            {/each}
        </div>
    </div>
    <!--buttons-->
    <div class="col-span-1 bg-gunmetal p-3 text-center rounded">
        <button class="bg-eerie-black p-2 rounded text-center w-full" onclick={clearRobots}>
            Clear Robots
        </button>
        <hr class="my-2 opacity-50">
        <input placeholder="Match Key" class="bg-eerie-black rounded p-2 w-full">
        
        <button class="bg-eerie-black p-2 rounded text-center w-full mt-2" onclick={loadEvent}>
            Load New Event
        </button>

        <button class="bg-eerie-black p-2 rounded text-center w-full mt-2" onclick={updateData}>
            Update Match Data
        </button>
    </div>

</div>