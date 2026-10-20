<script lang=ts>
	import LabeledSection from "$lib/components/LabeledSection.svelte";
	import RadioSection from "$lib/components/RadioGroup.svelte";
	import CheckSection from "$lib/components/CheckGroup.svelte";
    import TextArea from "$lib/components/TextArea.svelte";


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
<!-- Speed done
Drivetrain done

Max Height
Weight done
Center of Gravity done
More details to come

What cones they
How far they extend
Handoffs
Additional comments
How long did you spend designing/building your robot
Do you have any driver practice -->