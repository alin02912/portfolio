<script>
    import { fade } from "svelte/transition";
</script>

<section in:fade={{ duration: 1500, delay: 600}} out:fade={{duration: 400}}>
    <div class="explanation" >
        <p>
            This is a work-in-progress, personal project that I am developing on with the goal of
            creating a driving game that simulates some of the variable that
            beginner drivers need to watch out for. These variables include
            paying attention to the speed limit, shifting gears properly, and
            remembering to buckle the seatbelt. You can try the game yourself at this link:
            <a href="https://alin02912.github.io/CarGame/" target="_blank">Car Game</a>
        </p>
        <ul>
            Tools used:
            <li>GDevelop</li>
            <li>Tiled</li>
            <li>Vanilla JavaScript</li>
        </ul>
    </div>
    <div class="video-container">
        <!-- svelte-ignore a11y-media-has-caption -->
        <video src="/video.webm" autoplay loop muted>Video not loading</video>
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
