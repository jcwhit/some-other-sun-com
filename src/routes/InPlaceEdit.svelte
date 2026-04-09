<script lang="ts">
    let {
        paused,
        timeText,
        value = $bindable(),
        editing = $bindable(),
    } = $props();
    let editMode = $state(false);

    function save() {
        var valueInMillis = 0;

        getTimeParts().forEach((part: string, index: number) => {
            if (index === 0) {
                valueInMillis += parseInt(part) * 1000; // Convert seconds to milliseconds
                console.log(
                    "Seconds part:",
                    part,
                    "Value after seconds:",
                    valueInMillis,
                );
            } else if (index === 1) {
                valueInMillis += parseInt(part); // Milliseconds
                console.log(
                    "Milliseconds part:",
                    part,
                    "Value after milliseconds:",
                    valueInMillis,
                );
            }
        });

        value = valueInMillis;
        editMode = false;
        editing = false;
    }

    function toggleEditMode() {
        if (paused) {
            editing = true;
            editMode = !editMode;
        }
    }

    function cancel() {
        editMode = false;
    }

    function getSeconds() {
        return getTimeParts()[0].toString().padStart(2, "0");
    }

    function getMillis() {
        return getTimeParts()[1].toString().padStart(3, "0");
    }

    function getTimeParts() {
        return timeText.split(":");
    }
</script>

{#if editMode}
    <input
        type="text"
        bind:value={timeText}
        style="font-size: 100px; height: auto; width: auto;"
        class="input input-bordered w-full max-w-xs"
        onkeydown={(e) => {
            if (e.key === "Enter") save();
            else if (e.key === "Escape") cancel();
        }}
    />
{:else}
    <span
        onclick={() => toggleEditMode()}
        class="editable"
        tabindex="0"
        role="button"
        aria-pressed="false">{getSeconds()}:<span>{getMillis()[0]}<span class="text-info">{getMillis()[1]}{getMillis()[2]}</span></span></span
    >
{/if}

<style>
    .editable {
        cursor: pointer;
        padding: 0.25rem 0.5rem;
        border-radius: 0.25rem;
        transition: background-color 0.2s ease;
        font-size: 100px;
    }

    .editable:hover {
        background-color: rgba(255, 255, 255, 0.1);
    }
</style>
