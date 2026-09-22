<script lang=ts>
    import { goto } from "$app/navigation";
    import { resolve } from "$app/paths";

    function leaveQueue() {
        goto(resolve("/"))
    }
</script>

<div class="h-dvh w-full flex flex-col place-content-center text-center p-3">
    <h1 class="text-6xl">In Queue</h1>
    <button class="bg-gunmetal p-2 mt-4 text-4xl" onclick={leaveQueue}>
        Leave Queue
    </button>
</div>