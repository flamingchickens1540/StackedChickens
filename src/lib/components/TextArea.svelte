<script lang=ts>
    let { label, content = $bindable() } = $props()
</script>

<div class="mt-3 w-full bg-gunmetal rounded">
    <div class="text-lg p-2">
        {label}
    </div>
    <textarea bind:value={content} class="w-full resize-none border-t-1 border-white/50 p-2"></textarea>
</div>