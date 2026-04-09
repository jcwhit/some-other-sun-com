<script lang="ts">
    import { onDestroy } from "svelte";
    import { onMount } from "svelte";
    import InPlaceEdit from "./InPlaceEdit.svelte";

    let timer: number | undefined;
    let paused = $state(false);
    let editing = $state(false);
    let ttl = $state(5000);
    let currentTime = $state(Date.now());
    let calculatedMillis = $derived(ttl)
    let timeText = $derived(getSeconds() + ":" + getMillis());

    function startTimer() {
        timer = setInterval(() => {
            if (!paused) {
                var elapsed = Date.now() - currentTime;
                calculatedMillis = ttl - elapsed;
            }
        });
    }

    function pauseTimer() {
        paused = true;
    }

    function resumeTimer() {
        currentTime = Date.now() - (ttl - calculatedMillis);
        paused = false;
    }

    function getSeconds() {
        var seconds = Math.floor(calculatedMillis / 1000);
        if (calculatedMillis <= 0) seconds = 0;
        return seconds.toString().padStart(2, "0");
    }
    
    function getMillis() {
        var millis = Math.ceil(calculatedMillis % 1000);
        if (millis <= 0) millis = 0;
        return millis.toString().padStart(3, "0");
    }   

    function pauseResumeTimer(button: HTMLButtonElement) {
        if (paused) {
            button.textContent = "Pause";
            button.classList.remove("btn-success");
            button.classList.add("btn-info");
            resumeTimer();
        } else {
            button.textContent = "Resume";
            button.classList.remove("btn-info");
            button.classList.add("btn-success");
            pauseTimer();
        }
    }

    onMount(() => {
        startTimer();
        pauseTimer();
    });

    onDestroy(() => {
        console.log("Destroying component, clearing timer.");
        clearInterval(timer);
    });
</script>

<h1 class="flex text-4xl justify-center font-bold mb-8">Borrowed Time</h1>
<div class="flex flex-col items-center justify-center h-screen">


    <h2 class="text-2xl">Time To Live:</h2>

    <InPlaceEdit paused={paused} timeText={timeText} bind:value={ttl} bind:editing={editing} /> 
    
    <div class="flex space-x-4 mt-4">
        <button disabled={editing} onclick={(e) => pauseResumeTimer(e.currentTarget)} class="btn btn-accent">Start</button>
    </div>
</div>
