<script>
    import { fade } from "svelte/transition";
</script>

<section in:fade={{ duration: 1500, delay: 600}} out:fade={{duration: 400}}>
    <div class="explanation">
        <p>
            This is an e-learning course that I created to teach new employees about the processes and procedures of session cancellation and replacement in the Peel District School Board. It is an interactive course with software simulation, animation, and knowledge assessments.
        </p>
        <ul>
            Tools used:
            <li>Articulate Storyline 360</li>
        </ul>
    </div>
    <div class="video-container">
        <!-- svelte-ignore a11y-media-has-caption -->
        <video src="/video2.webm" autoplay loop muted>Video not loading</video>
    </div>
</section>

<style>
    .explanation {
        color: #bebebe;
        font-size: 1.2rem;
        font-weight: 400;
        line-height: 1.6;
        margin: 1.2rem 0;
    }
    section {
        width: 100%;
        display: grid;
        grid-gap: 1rem;
        grid-template-columns: 1fr 1fr;
        justify-content: space-between;
    }
    .video-container {
        display: flex;
        max-width: 100%;
    }
    video {
        max-width: 100%;
    }
    @media only screen and (max-width: 48rem) {
        section {
            display: flex;
            flex-direction: column;
        }
    }
</style>
