<script lang=ts>
	import MatchScoutBtns from "$lib/components/MatchScoutBtns.svelte";
	import PostMatch from "$lib/components/PostMatch.svelte";
	import PreMatch from "$lib/components/PreMatch.svelte";
	import { ArrowBigLeft, ArrowBigRight } from "lucide-svelte";

    let stage: number = $state(0);
    let stageNames: string[] = ["Prematch", "Auto", "Tele", "Postmatch"]

    let actions: string[] = $state([])

    let data = $state({
        teamKey: 1540,
        autoConeSucceed: 0,
        autoConeFail: 0,
        teleConeSucceed: 0,
        teleConeFail: 0,
        notes: "",

    })
</script>

<div class="flex flex-col h-[100vh]">
    <div class="flex justify-between items-center px-3">
        <button onclick={stage > 0 ? () => stage-- : () => {}} class={stage > 0 ? "opacity-50 active:opacity-100" : "opacity-0"}>
            <ArrowBigLeft/>
        </button>
        <div class="flex flex-col text-center pb-3">
            <h2 class="text-2xl text-white/50 mt-2">{stageNames[stage]}</h2>
            <h1 class="text-5xl text-xanthous font-bold">{data.teamKey}</h1>
        </div>
        <button onclick={stage < 3 ? () => stage++ : () => {}} class={stage < 3 ? "opacity-50 active:opacity-100" : "opacity-0"}> 
            <ArrowBigRight/>
        </button>
    </div>
    {#if stage == 0}
        <PreMatch/>
    {:else if stage == 1}
        <MatchScoutBtns bind:data={data} stageName="auto" bind:actions={actions}/>
    {:else if stage == 2}
        <MatchScoutBtns bind:data={data} stageName="tele" bind:actions={actions}/>
    {:else if stage == 3}
        <PostMatch/>
    {/if}
</div>
