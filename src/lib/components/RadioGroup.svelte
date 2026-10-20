<script lang=ts>
    let { label, selection = $bindable(), options } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-lg p-2 border-b-1 border-white/50">
        {label}
    </div>
    {#each options as option}
        <button class="w-full p-2 {option == selection ? "bg-xanthous text-eerie-black" : ""}" onclick={() => {selection = option}}>
            {option}
        </button>
    {/each}
</div>