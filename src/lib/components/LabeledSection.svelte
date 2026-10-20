<script lang=ts>
    let { label } = $props()
</script>

<div class="mt-2 w-full p-3">
    <span class="text-2xl text-imperial-red">
        {label}
    </span>
    <slot />
</div>