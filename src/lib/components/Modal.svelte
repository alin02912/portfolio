<script>
    import { fly, fade } from "svelte/transition";
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    function handleClick() {
        dispatch("hamburgerClicked", {
            text: "Hello!",
        });
    }
</script>

<div class="overlay" transition:fade={{ duration: 500 }} />
<div class="menu-container" transition:fly={{ y: 200, duration: 1000 }}>
    <ul on:click={handleClick}>
        <li><a href="/#About">About</a></li>
        <li><a href="/#Work-history">Work History</a></li>
        <li><a href="/#projects">Projects</a></li>
        <li><a href="/#Resume">Resume</a></li>
        
    </ul>
</div>

<style>
    .overlay {
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        background-color: #0a0b0bcc;
        z-index: 900;
    }
    .menu-container {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 901;
    }
    ul {
        padding: 0;
        margin: 0;
    }
    li {
        list-style-type: none;
        padding: 0;
        font-size: 1.5rem;
        line-height: 2;
    }
    a {
        text-decoration: none;
        color: #f5f5f1;
    }
</style>
