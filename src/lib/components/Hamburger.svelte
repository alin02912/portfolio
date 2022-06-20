<script>
    import { createEventDispatcher } from "svelte";
    import { selected } from '$lib/stores.js';

    const dispatch = createEventDispatcher();

    function handleClick() {
        dispatch("hamburgerClicked", {
            text: "Hello!",
        });
        selected.set($selected=!$selected);
    }
</script>

<div class={$selected ? "toggle selected" : "toggle"} on:click={handleClick}>
    <span />
    <span />
    <span />
</div>

<style>
    .toggle {
        position: relative;
        width: 4.375rem;
        height: 4.375rem;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        overflow: hidden;
    }
    .toggle span {
        width: 2.5rem;
        height: 0.25rem;
        background-color: #f5f5f1;
        position: absolute;
        border-radius: 0.25rem;
        transition: 1s;
    }
    .toggle span:nth-child(1) {
        transform: translateY(-1rem);
        width: 1.5625rem;
        left: 0.9375rem;
    }
    .toggle span:nth-child(2) {
        transform: translateY(1rem);
        width: 0.9375rem;
        left: 0.9375rem;
    }

    .toggle.selected > span:nth-child(3) {
        background-color: #ff3e00;
        transform: translate(4rem);
    }

    .toggle.selected > span:nth-child(1) {
        background-color: #ff3e00;
        transform: translate(0) rotate(45deg);
        width: 2.5rem;
    }
    .toggle.selected > span:nth-child(2) {
        background-color: #ff3e00;
        transform: translate(0) rotate(-45deg);
        width: 2.5rem;
    }
</style>
