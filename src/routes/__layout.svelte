<script>
    import "../styles/global.css";
    import Hamburger from '$lib/components/Hamburger.svelte';
    import Modal from '$lib/components/Modal.svelte';
    import Logo from '$lib/components/Logo.svelte';
    let showModal = false;
</script>

{#if showModal}
<Modal />
{/if}
<header>
    <Logo />
    <Hamburger on:hamburgerClicked="{()=>showModal = !showModal}"/>
</header>
<main>
    <slot />
</main>

<style>
    header {
        display: flex;
        justify-content: space-between;
    }    
</style>
