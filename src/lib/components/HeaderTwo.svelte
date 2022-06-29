<script>
    import Logo from "./Logo.svelte";
    import { activeHeader } from "$lib/stores.js";

    let activeSection;
    activeHeader.subscribe((value) => (activeSection = value));
</script>

<section>
    <ul class="list">
        <li class:active={activeSection === "About"}>
            <a class="blue" href="/#About" data-text="&nbsp;About&nbsp;">&nbsp;About&nbsp;</a
            >
        </li>
        <li class:active={activeSection === "Work History"}>
            <a class="red" href="/#Work-history" data-text="&nbsp;Work&nbsp;History&nbsp;"
                >&nbsp;Work&nbsp;History&nbsp;</a
            >
        </li>
        <li><Logo /></li>
        <li class:active={activeSection === "Projects"}>
            <a class="yellow" href="/#projects" data-text="&nbsp;Projects&nbsp;"
                >&nbsp;Projects&nbsp;</a
            >
        </li>
        <li class:active={activeSection === "Resume"}>
            <a class="green" href="/#Resume" data-text="&nbsp;Resume&nbsp;"
                >&nbsp;Resume&nbsp;</a
            >
        </li>
    </ul>
</section>

<style>
    section {
        display: flex;
        justify-content: center;
        align-items: flex-start;
        justify-items: flex-start;
    }
    ul.list {
        padding: 0;
        width: 62.5rem;
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }
    a,
    a:visited {
        text-decoration: none;
        color: #f5f5f1;
        position: relative;
    }
    ul li a::before {
        text-decoration: none;
        content: attr(data-text);
        display: inline;
        position: absolute;
        color: var(--clr);
        overflow: hidden;
        width: 0;
        border-right: 1px solid var(--clr);
        transition: 0.75s ease-in-out;
        -webkit-text-stroke: 1px var(--clr);
    }
    ul li a:hover::before,
    .active a::before {
        width: 100%;
        /* filter: drop-shadow(0 0 5px var(--clr)); */
    }
    .active {
        opacity: 0.5;
        pointer-events: none;
    }
    ul.list li {
        font-size: 1.2rem;
        font-variant: small-caps;
        margin-inline: 2rem;
        list-style-type: none;
        transition: 0.75s ease-in-out;
    }
    .blue {--clr: #3193fa;}
    .red {--clr: #ff4000;}
    .yellow {--clr: #ffda71;}
    .green {--clr: #5bc0be;}

</style>
