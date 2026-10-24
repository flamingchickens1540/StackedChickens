<script lang=ts>
	import { goto } from "$app/navigation";
	import { ClipboardList } from "lucide-svelte";

    let teamEvents: {teamKey: number, completed: boolean}[] = [
        {teamKey: 1540, completed: true},
        {teamKey: 1541, completed: false}
    ]
</script>

<center>
    <h2 class="text-2xl text-white/50 mt-2">Pitscout</h2>
    <h1 class="text-5xl text-xanthous font-bold">Teams</h1>
</center>

<div class="p-3">
    <div class="rounded bg-gunmetal text-2xl">
        {#each teamEvents as teamEvent, i}
            <button class="w-full p-3 flex items-center justify-between {teamEvent.completed ? "" : "text-xanthous"} { i > 0 ? "border-t-1 border-white/50" : ""}" onclick={() => goto(`/pitscout/collect?teamKey=${teamEvent.teamKey}`)}>
                {teamEvent.teamKey}
                <ClipboardList color={teamEvent.completed ? "#fff" : "#f6b14b"} />
            </button>
        {/each}

    </div>
</div>