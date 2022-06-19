<script>
    import Workplace from "$lib/components/Workplace.svelte";
    import Layout from "./__layout.svelte";
    import { geotabLogo } from "$lib/stores.js";
    import { LearnStyleLogo } from "$lib/stores.js";
    import { EtagLogo } from "$lib/stores.js";
    import { fly, fade } from "svelte/transition";

    let workplaces = [
        {
            id: 0,
            name: "Geotab",
            description:
                "Geotab strives to help its clients make the right decision when it comes to fleet management. To do that, they provide a rich set of telemtric data through a wide range of hardware and software offerings.",
            title: "Learning Design Intern",
            duration: "Jan 2022 - Present",
            tasks: [
                "Created accessible, SCORM-compliant e-learning content using a number of authoring tools, such as Storyline 360, Camtasia & Snagit, as well as using plain HTML/CSS and JavaScript.",
                "Integrated learning content with Geotab's new Learning Management System (LMS) by writing JavaScript code that extend the functionality of content made with authoring tools.",
                "Wrote automation scripts that assist with the transition to the new LMS and facilitated the management of it. This includes scripts that crawl through the course catalogue and collect course information that are not collectible with native LMS features.",
            ],
            logo: `${geotabLogo}`,
        },
        {
            id: 1,
            name: "LearnStyle",
            description:
                "LearnStyle is all about transforming the life trajectory of children with learning exceptionalities. They do that by coaching students on how to leverage assistive technology with learning strategies to have an equal access to education and become independent learners.",
            title: "Senior Educator & Technology Learning Consultant",
            //duration: "Sep 2021 - Present\nMar 2018 - Sep 2021: Educator & Tech. Coach",
            duration: "Mar 2018 - Present",
            tasks: [
                "Provided personalized learning to students on how to use assistive technologies & learning strategies appropriate to their learning disability",
                "Gave workshops on the topics of assistive technology and learning strategies to teachers and special education staff",
                "Created instructional content for students, teachers, and colleagues on the topic of learning disabilities and assistive technology",
                "Mentored new employees on the ins and outs of technology training.",
            ],
            logo: `${LearnStyleLogo}`,
        },
        {
            id: 2,
            name: "ETAG Online",
            description:
                "Etag's mission is to leave no senior citizen behind. They endevour to help the elderly navigate the digital world by teaching them how to use their devices to help with everday tasks such as grocery shopping, paying bills, and connecting with their loved ones.",
            title: "Volunteer Educator",
            duration: "Jan 2015 - Aug 2016",
            tasks: [
                "Taught ETAG clients on the use of variety of devices and operating systems from laptops and smartphones to messaging apps and internet browsers",
                "Managed sessions and tutored new volunteers",
                "Helped coordinate session times and space reservation",
            ],
            logo: `${EtagLogo}`,
        },
    ];
    let workplaceID = 0;
    let showResume;

    let options = {
        root: null,
        rootMargin: "-30% 0px -60% 0px",
        threshold: 0,
    };

    function observeMe(node) {
        let observer = new IntersectionObserver(changeOpacity, options);
        let faded = true;
        observer.observe(node);
        function changeOpacity(entries) {
            entries.forEach((entry) => {
                if (entry.isIntersecting && faded) {
                    node.animate([{opacity: 1}],{duration:1000,fill:"forwards"});
                    faded = false;
                    return
                } else if (!entry.isIntersecting && !faded) {
                    node.animate([{opacity: 0.3}],{duration:1000,fill:"forwards"});
                    faded = true;
                    return
                } else {

                }
            });
        }
        return {
            destroy() {
                observer.disconnect();
            },
        };
    }
</script>

<section use:observeMe class="main-content" id="main-content">
    <p>Hi! My name is</p>
    <h1>Ali Nasser</h1>
    <h2>Learning Desinger & AT Specialist</h2>
    <p>
        I am a Toronto-based Educator and an Assistive Technology Specialist who
        is passionate about using technology to create individualized training
        to learners who have a variety of learning needs and abilities.
        Currently, I am working at Geotab to develop instructional content in
        the field of telemtrics and to assist in managing the LMS.
    </p>
</section>

<section use:observeMe class="about" id="About">
    <h3><span>01: </span>About Myself</h3>
    <p>
        Hello! My name is Ali Nasser and I enjoy combining my knowledge in
        learning design, assistive technologies, and web development to create
        personalized learning solutions for learners of various abilities. I
        work hard to get to know my stakeholders and build the training
        experiance that they need. I started out in the field of psychology and
        over the years I have built up a skillset in using web technologies too.
        This allows me to diversify the delivery of instructional content from
        in-person training to SCORM-compliant e-learning courses.
    </p>
    <p>
        Over the years, I have had the privilege to work with students with
        learning exceptionalities in the Peel and Halton Catholic school boards,
        a retail tech startup, an advertising agency and few startups. My focus
        these days is to create accessible learning content for adult learners
        in the field of telemetrics.
    </p>
    <p>Here is a snapshot of the tools and strategies that I used recently:</p>
    <div class="toolsList">
        <ul>
            <li>Web Technologies</li>
            <li>JavaScript (NodeJS/SvelteKit)</li>
            <li>HTML/CSS</li>
            <li>Authoring Tools (Articulate Stroyline & Rise 360)</li>
        </ul>
        <ul>
            <li>Assistive Technologies</li>
            <li>read&write</li>
            <li>WordQ</li>
            <li>Google & Microsoft Office Tools</li>
        </ul>
        <ul>
            <li>Learning Strategies</li>
            <li>TOWER</li>
            <li>SQ4R</li>
            <li>Store & Share</li>
        </ul>
    </div>
</section>

<section use:observeMe class="work-history" id="Work-history">
    <h3><span>02: </span>Here's where I've worked</h3>
    <ul class="workplaces">
        {#each workplaces as { id, name }}
            <li
                class:active={workplaceID === id}
                on:click={() => {
                    workplaceID = id;
                }}
            >
                {name}
            </li>
        {/each}
    </ul>
    <Workplace {...workplaces[workplaceID]} />
</section>

<section use:observeMe class="resume" id="Resume">
    <h3><span>03: </span>Resume</h3>
    <div class="button">
        <p on:click={() => (showResume = !showResume)}>
            {showResume ? "Hide resume" : "Show resume"}
        </p>
    </div>
    <div class="resume-object-container">
        {#if showResume}
            <object
                title="resume"
                type="application/pdf"
                data="/Ali_Nasser_Resume_pdf.pdf"
                width="700px"
                height="700px"
                transition:fade={{ duration: 1000 }}
            />
        {/if}
    </div>
</section>

<style>
    section {
        opacity: 0.3;
    }
    .work-history {
        height: 55rem;
    }
    .main-content > h1 {
        width: 10ch;
        margin-right: 0;
        animation: typing 3s steps(10);
        font-family: monospace;
        text-transform: uppercase;
        white-space: nowrap;
        overflow: hidden;
    }
    @keyframes typing {
        from {
            width: 0;
        }
    }
    .resume {
        margin-bottom: 10rem;
    }
    .resume-object-container {
        height: 50rem;
        margin-top: 1rem;
    }
    .resume object {
        object-fit: cover;
    }
    .resume .button p {
        display: inline;
        color: #bebebe;
        font-size: 1.2rem;
        margin-right: 2rem;
        margin-bottom: 3rem;
        height: 2rem;
        list-style-type: none;
        cursor: pointer;
        text-align: center;
        border-bottom: 0.2rem solid #bebebe;
        position: relative;
        transition: transform 2s;
    }
    .resume .button p::before {
        content: "";
        background-color: #0a0b0b;
        position: absolute;
        width: 100%;
        height: 0.5rem;
        bottom: -0.5rem;
        right: 0;
        transition: 1s;
        z-index: inherit;
    }
    .resume .button p:hover:not(.active)::before {
        transform: scaleX(0);
    }
    ul.workplaces {
        display: flex;
        justify-content: flex-start;
        padding: 0;
        align-items: flex-start;
    }
    ul.workplaces > li {
        color: #6b6b6b;
        font-size: 1.2rem;
        margin-right: 2rem;
        list-style-type: none;
        cursor: pointer;
        text-align: center;
        border-bottom: 0.2rem solid #bebebe;
        position: relative;
        transition: transform 2s;
    }
    ul.workplaces > li::before {
        content: "";
        background-color: #0a0b0b;
        position: absolute;
        width: 100%;
        height: 0.5rem;
        bottom: -0.5rem;
        right: 0;
        transition: 1s;
        z-index: inherit;
    }
    ul.workplaces > li:hover {
        color: #fff;
    }
    ul.workplaces > li.active {
        color: #fff;
        pointer-events: none;
        cursor: default;
    }
    ul.workplaces > li:hover:not(.active)::before {
        transform: translateX(-50%) scaleX(0);
    }
    section {
        padding-top: 9rem;
        margin-top: 5rem;
    }
    h1 {
        font-size: 3.5rem;
        font-weight: 600;
    }
    h2 {
        font-size: 2.5rem;
        color: #bebebe;
        font-weight: 500;
    }
    p {
        color: #bebebe;
        font-size: 1.2rem;
        font-weight: 400;
        line-height: 1.6;
        margin: 1.2rem 0;
    }

    h3 {
        font-size: 1.5rem;
        font-weight: 400;
    }

    h3 span {
        font-size: 1rem;
        color: #bebebe;
    }
    .toolsList {
        display: flex;
        justify-content: space-between;
    }
    .about .toolsList > * {
        flex-basis: 33%;
    }
    .about .toolsList ul :first-child {
        text-align: center;
        font-weight: bold;
        list-style-type: none;
    }
    @media only screen and (max-width: 31.25rem) {
        .toolsList {
            flex-direction: column;
        }
        .work-history {
        height: 87rem;
    }
    }
</style>
