<script>
    import Workplace from "$lib/components/Workplace.svelte";
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
    <Workplace />
</section>

<style>
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
    .toolsList ul :first-child {
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
