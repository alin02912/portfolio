<script>
    import "../styles/global.css";
    import Hamburger from "$lib/components/Hamburger.svelte";
    import Modal from "$lib/components/Modal.svelte";
    import Logo from "$lib/components/Logo.svelte";
    import HeaderTwo from "../lib/components/HeaderTwo.svelte";
    import { selected } from "$lib/stores.js";
    let showModal = false;
    let windowWidth;
</script>
<svelte:window bind:innerWidth="{windowWidth}"/>

{#if showModal}
    <Modal
        on:hamburgerClicked={() => {
            showModal = !showModal;
            selected.set(($selected = !$selected));
        }}
    />
{/if}
<section class="grid">
    <header class="{windowWidth <= 768 ? "headerOne" : "headerOne hidden" }">
        <Logo />
        <Hamburger
            on:hamburgerClicked={() => {
                showModal = !showModal;
            }}
        />
    </header>
    <header class="{windowWidth > 768 ? "headerTwo" : "headerTwo hidden" }">
        <HeaderTwo />
    </header>
    <main>
        <slot />
    </main>
</section>

<style>
    .grid {
        display: grid;
        position: relative;
        grid-template-columns: minmax(0, 1fr) minmax(0, 62.5rem) minmax(
                0,
                1fr
            );
    }
    .hidden {
        display: none;
    }
    .headerTwo {
        z-index: 902;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        margin: 0 0;
        height: max(5%, 5rem);
        backdrop-filter: blur(4px);
    }
    .headerOne {
        z-index: 902;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        margin: 0 0;
        height: max(5%, 5rem);
        display: flex;
        justify-content: space-between;
        backdrop-filter: blur(4px);
    }
    .hidden {
        display: none;
    }
    .grid > * {
        grid-column: 2;
        padding-left: 6.25rem;
        padding-right: 6.25rem;
    }

    @media only screen and (max-width: 48rem) {
        .grid > * {
            padding-left: 1.25rem;
            padding-right: 1.25rem;
        }
    }
</style>
