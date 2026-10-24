<script lang=ts>
    let { label, content = $bindable() } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-xl p-2 border-b-1 border-white/50">
        {label}
    </div>
    <textarea bind:value={content} placeholder={label} class="w-full resize-none outline-0 rounded-xs focus:outline-2 outline-imperial-red p-2"></textarea>
</div>