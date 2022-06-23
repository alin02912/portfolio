<script>
    import { onMount } from "svelte";
    import { fade } from "svelte/transition";
    import { onDestroy } from "svelte";

    let ternary;
    let keyboard;
    let leaderboard;
    let textLength;
    let keyboardLength;
    let leaderboardLength;
    let switcher = true;
    onMount(() => {
        textLength = ternary.textContent.length;
        keyboardLength = keyboard.textContent.length;
        leaderboardLength = leaderboard.textContent.length;
        let ternaryAnimation = ternary.animate(
            [
                { width: 0, visibility: "visible" },
                { width: `${textLength}ch`, visibility: "visible" },
            ],
            { duration: 4000, easing: `steps(${textLength})`, fill: "forwards" }
        );
        ternaryAnimation.onfinish = () => {
            if (!keyboard) return;
            let keyboardAnimation = keyboard.animate(
                [
                    { width: 0, visibility: "visible" },
                    {
                        width: `${keyboardLength}ch`,
                        visibility: "visible",
                    },
                ],
                {
                    duration: (keyboardLength / 13.25) * 1000,
                    easing: `steps(${keyboardLength})`,
                    fill: "forwards",
                }
            );
            keyboardAnimation.onfinish = () => {
                if (!leaderboard) return;
                let leaderboardAnimation = leaderboard.animate(
                    [
                        { width: 0, visibility: "visible" },
                        {
                            width: `${leaderboardLength}ch`,
                            visibility: "visible",
                        },
                    ],
                    {
                        duration: 2000,
                        easing: `steps(${leaderboardLength})`,
                        fill: "forwards",
                        endDelay: 2000,
                    }
                );
                leaderboardAnimation.onfinish = () => {
                    ternaryAnimation.currentTime = 0;
                    keyboardAnimation.cancel();
                    leaderboardAnimation.cancel();
                    ternaryAnimation.cancel();
                    switcher = !switcher;
                    ternaryAnimation.play();
                };
            };
        };
        // return function () {
        //     document.getAnimations().forEach(function (animation) {
        //         animation.cancel();
        //     });
        // };
    });

    onDestroy(() => {
        document.getAnimations().forEach(function (animation) {
            // animation.cancel();
            try {
                keyboardAnimation.cancel();
                leaderboardAnimation.cancel();
                ternaryAnimation.cancel();
            } catch (error) {}
        });
    });
</script>

<section in:fade={{ duration: 1500, delay: 600 }} out:fade={{ duration: 400 }}>
    <div class="explanation">
        <p>
            In this project, I created an automation script that crawls through
            the LMS in order to modify course settings. This allowed 1,000s of
            courses to have their settings controlled progromatically and
            adjusted within a short period of time. This project also involved
            automatically collecting course attributes that were not collectible
            with LMS's built-in reporting tools.
        </p>
        <ul>
            Tools used:
            <li>Puppeteer Library</li>
            <li>Vanilla JavaScript</li>
        </ul>
    </div>
    <div class="animationHalf">
        <div
            bind:this={ternary}
            style="--textLength:{textLength}"
            class="ternary"
        >
            let points = courses.length > 5 ? <span
                class:green={switcher === true}>20</span
            >
            : <span class:green={switcher !== true}>5</span>;
        </div>
        <div bind:this={keyboard} class="keyboard">
            $$keyboard.type(points);
        </div>
        <div class="leaderboard-container">
            <p>leaderboard Points:</p>
            <div class="leaderboard-border">
                <div bind:this={leaderboard} class="leaderboard">
                    {switcher ? "20 points" : "5 points"}
                </div>
            </div>
        </div>
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
    .green {
        color: green;
    }
    .ternary,
    .keyboard,
    .leaderboard {
        font-family: monospace;
        white-space: nowrap;
        overflow: hidden;
        font-size: 1.5rem;
        visibility: hidden;
    }
    .leaderboard-container {
        font-family: monospace;
        white-space: nowrap;
        font-size: 1.5rem;
        display: flex;
        gap: 1rem;
    }
    .leaderboard-border {
        width: 10rem;
        padding-inline: 1rem;
        margin-right: 5rem;
        border: 0.25rem solid #696969;
        color: #000;
        background-color: #fff;
    }
    @media only screen and (max-width: 48rem) {
        section {
            display: flex;
            flex-direction: column;
        }
    }
</style>
