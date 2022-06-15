<script>
    import Workplace from "$lib/components/Workplace.svelte";
    import Layout from "./__layout.svelte";
    import {geotabLogo} from "$lib/stores.js";
    import { LearnStyleLogo } from "$lib/stores.js";
    import { EtagLogo } from "$lib/stores.js";
    let workplaces = [
        {
            name: "Geotab",
            description:
                "Geotab strives to help its clients make the right decision when it comes to fleet management. To do that, they provide a rich set of telemtric data through a wide range of hardware and software offerings.",
            title: "Learning Design Intern",
            duration: "Jan 2022 - Present",
            tasks: [
                "Create accessible, SCORM-compliant e-learning content",
                "Integrate learning content with Geotab's new Learning Management System (LMS)",
                "Write programs that assist with the transition to the new LMS",
            ],
            logo: `${geotabLogo}`,
        },
        {
            name: "LearnStyle",
            description: "LearnStyle is all about transforming the life trajectory of children with learning exceptionalities. They do that by teaching students how to leverage assistive technology to have an equal access to education and become independent learners.",
            title: "Senior Educator & Technology Learning Consultant",
            duration: "Mar 2018 - Present",
            tasks: ["Provided personalized learning to students on how to use assistive technologies & learning strategies appropriate to their learning disability", "Gave workshops on the topics of assistive technology and learning strategies to teachers and special education staff", "Created instructional content for students, teachers, and collegues on the topic of learning disabilities and assistive technology", "Mentored new employees in the ins and outs of technology training."],
            logo: `${LearnStyleLogo}`,
        },
        {
            name: "ETAG Online",
            description: "Etag's mission is to leave no senior citizen behind. They endevour to help the elderly navigate the digital world, troubleshoot ",
            title: "Educator",
            duration: "Jan 2015 - Aug 2016",
            tasks: "",
            logo: `${EtagLogo}`,
        },
    ];
</script>

<section class="main-content">
    <p>Hi! My name is</p>
    <h1>Ali Nasser</h1>
    <h2>Learning Desinger & AT Specialist</h2>
    <p>
        I am a Toronto-based Educator and an Assistive Technology Specialist who
        is passionate about using technology to create individualized training
        to learners of various learning needs and abilities. Currently, I am
        working at Geotab to develop instructional content and to assist in
        managing the LMS.
    </p>
</section>

<section class="about" id="About">
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

<section class="about" id="Profile">
    <h3><span>02: </span>Here's where I've worked</h3>
    <ul class="workplaces">
        {#each workplaces as { name }}
            <li on:click={() => console.log("hello")}>{name}</li>
        {/each}
    </ul>
    <Workplace {...workplaces[0]} />
</section>

<style>
    ul.workplaces {
        display: flex;
        justify-content: flex-start;
        padding: 0;
    }
    ul.workplaces > li {
        color: #6b6b6b;
        font-size: 1.2rem;
        margin-right: 2rem;
        height: 2rem;
        list-style-type: none;
        cursor: pointer;
        text-align: center;
        border-bottom: 0.2rem solid #bebebe;
        position: relative;
        transition: transform 2s;
        overflow: visible;
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
    }
    ul.workplaces > li:hover::before {
        transform: translateX(-50%) scaleX(0);
    }
    section {
        padding-top: 9rem;
    }
    .main-content,
    .about {
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
    }
</style>
