<script lang="ts">
    export let text = ""
    export let Style = "bg-red-400"
    export let HoverStyle = "bg-red-300"

    export let LessRound = false

    export let Extra = ''

    $: usingStyle = Style

    const handleEnter = () => {
        usingStyle = HoverStyle
    }
    const handleLeave = () => {
        usingStyle = Style
    }


</script>

<div class="group relative w-fit h-fit select-none text-sm {Extra}">
    <button on:click on:mouseenter={handleEnter} on:mouseleave={handleLeave} class="shadow-md text-transparent w-fit px-4 py-2 {LessRound ? 'rounded-xl' : 'rounded-full' } cursor-pointer group-hover:scale-[1.03] transition-all duration-100 {usingStyle}">
        {text}
    </button>
    <div class="absolute pointer-events-none top-0 left-0 w-full h-full flex justify-center place-items-center">
        {text}
    </div>
</div>

<style lang="postcss">
</style>