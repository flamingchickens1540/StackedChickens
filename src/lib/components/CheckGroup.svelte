<script lang=ts>
    let { label, source = $bindable(), options } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-xl p-2">
        {label}
    </div>
    {#each options as {label, key}}
        <button class="w-full p-2 border-t-1 border-white/50 {source[key] ? "bg-xanthous text-eerie-black" : ""}" onclick={() => {source[key] = !source[key]}}>
            {label}
        </button>
    {/each}
</div>