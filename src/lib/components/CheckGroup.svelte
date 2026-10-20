<script lang=ts>
    let { label, source = $bindable(), options } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-lg p-2 border-b-1 border-white/50">
        {label}
    </div>
    {#each options as {label, key}}
        <button class="w-full p-2 {source[key] ? "bg-xanthous text-eerie-black" : ""}" onclick={() => {source[key] = !source[key]}}>
            {label}
        </button>
    {/each}
</div>