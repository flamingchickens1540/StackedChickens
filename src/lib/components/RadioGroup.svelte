<script lang=ts>
    let { label, selection = $bindable(), options } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-xl p-2">
        {label}
    </div>
    {#each options as option}
        <button class="w-full p-2 border-t-1 border-white/50 {option == selection ? "bg-xanthous text-eerie-black" : ""}" onclick={() => {selection = option}}>
            {option}
        </button>
    {/each}
</div>