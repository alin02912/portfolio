<script>
    import "../styles/global.css";
    import Hamburger from "$lib/components/Hamburger.svelte";
    import Modal from "$lib/components/Modal.svelte";
    import Logo from "$lib/components/Logo.svelte";
    import { selected } from '$lib/stores.js';
    let showModal = false;
</script>

{#if showModal}
    <Modal
        on:hamburgerClicked={() => {
            showModal = !showModal;
            selected.set($selected=!$selected);
        }}
    />
{/if}
<section class="grid">
    <header>
        <Logo />

        <Hamburger
            on:hamburgerClicked={() => {
                showModal = !showModal;
            }}
        />
    </header>
    <main>
        <slot />
    </main>
</section>

<style>
    .grid {
        display: grid;
        grid-template-columns: minmax(2rem, 1fr) minmax(0, 40rem) minmax(
                2rem,
                1fr
            );
    }
    header {
        display: flex;
        justify-content: space-between;
        margin-top: 1rem;
    }
    .grid > * {
        grid-column: 2;
    }
</style>
