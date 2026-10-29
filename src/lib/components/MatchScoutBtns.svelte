<script lang=ts>
    let { stageName, data = $bindable(), actions = $bindable() }: { stageName: string, data: any, actions: any} = $props();

    function editData(action: string) {
        data[action]++;
        actions[actions.length] = action;
    }

    function undoData() {
        data[actions.pop()]--;
    }
</script>
<div class="flex-grow-1 flex flex-col">
    <div class="flex justify-between px-3 text-xl">
        <span>{stageName} successes: {data[stageName+"ConeSucceed"]}</span>
        <span>{stageName} fails: {data[stageName+"ConeFail"]}</span>
    </div>

    <div class="grid-wrap grid grid-rows-5 p-3 gap-3 pt-0 content-stretch h-full mt-1 flex-grow-1">
        <button class="{stageName != "auto" ? "bg-eminence" : "bg-steel-blue"} active:bg-white row-span-2 rounded text-4xl font-bold" onclick={() => editData(stageName+"ConeSucceed")}>Cone Succeed</button>
        <button class="{stageName != "auto" ? "bg-eminence" : "bg-steel-blue"} active:bg-white row-span-2 rounded text-4xl font-bold" onclick={() => editData(stageName+"ConeFail")}>Cone Fail</button>
        <button class="bg-gunmetal row-span-1 rounded p-2 text-white/75 text-xl {actions.length == 0 ? "opacity-50" : ""}" onclick={undoData}>
            Undo last action:
            <p class="font-bold text-white">{actions.length == 0 ? "None" : actions[actions.length-1]}</p>
        </button>
    </div>
</div>