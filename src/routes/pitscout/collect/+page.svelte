<script lang=ts>
	import LabeledSection from "$lib/components/LabeledSection.svelte";
	import RadioSection from "$lib/components/RadioGroup.svelte";
	import CheckSection from "$lib/components/CheckGroup.svelte";
    import TextArea from "$lib/components/TextArea.svelte";
	import { goto } from "$app/navigation";


    let data = $state({
        teamKey: 1540,
        speed: "",
        drivetrain: "",
        weight: "",
        cog: "",
        extension: "",
        handoffs: "",
        canPickTipped: "",
        canPickUpright: "",
        drivePractice: "",
        timeSpent: "",
        notes: "",
    })

    function submit() {
        goto("/pitscout/teamlist")
    }
</script>

<center>
    <h2 class="text-2xl text-white/50 mt-2">Pitscout</h2>
    <h1 class="text-5xl text-xanthous font-bold">{data.teamKey}</h1>
</center>

<LabeledSection label="Specs">
    <TextArea label="Speed" bind:content={data.speed}></TextArea>
    <RadioSection label="Drivetrain" options={['Swerve', 'Tank', 'Other']} bind:selection={data.drivetrain}></RadioSection>
    <TextArea label="Weight" bind:content={data.weight}></TextArea>
    <TextArea label="Center of Gravity" bind:content={data.cog}></TextArea>
</LabeledSection>

<LabeledSection label="Abilities">
    <TextArea label="Extension length" bind:content={data.extension}></TextArea>
    <TextArea label="Handoffs" bind:content={data.handoffs}></TextArea>
    <CheckSection label="Can pick up cones:" source={data} options={[{label: "Upright", key: "canPickUpright"}, {label: "Tipped", key:"canPickTipped"}]}></CheckSection>
</LabeledSection>

<LabeledSection label="Misc.">
    <TextArea label="How much drive practice was had?" bind:content={data.drivePractice}></TextArea>
    <TextArea label="Time spent building/designing robot?" bind:content={data.timeSpent}></TextArea>
    <TextArea label="Other notes" bind:content={data.handoffs}></TextArea>
</LabeledSection>

<center>
    <button class="simple bg-gunmetal rounded p-3 mb-3 text-xl" onclick={submit}>
        Submit
    </button>
</center>