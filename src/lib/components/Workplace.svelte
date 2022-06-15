<script>
    export let description = `Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita labore eaque ullam velit doloremque est reiciendis recusandae inventore sapiente distinctio dolor rem fuga cum minus maiores deleniti impedit laboriosam nemo, aliquam fugiat consectetur, quam dolorem. Quam vero a molestias magnam illum fuga officia, ratione, maiores modi ut harum aut corrupti nisi et architecto, voluptatibus tempora cupiditate ducimus accusantium suscipit exercitationem?`;
    export let title = `Lorem ipsum dolor`;
    export let duration = `Lorem ipsum dolor`;
    export let tasks = ["Task 1", "Task 2", "Task 3"];
    export let logo = "some image";
</script>

<p class="description">
    {description}
</p>

<h4 class="title">
    {title}
</h4>
<p class="duration">
    {duration}
</p>
<section>
    <div class="text">
        <ul class="tasks">
            {#each tasks as task}
                <li>{task}</li>
            {/each}
        </ul>
    </div>
    <div class="logo">
        {@html logo}
    </div>
</section>

<style>
    section {
        display: flex;
        gap: 1rem;
    }
    section > .text {
        flex-basis: 60%;
    }
    p,
    ul {
        color: #bebebe;
        font-size: 1.2rem;
        font-weight: 400;
        line-height: 1.6;
        margin: 1.2rem 0;
    }
    .duration {
        color: #fff;
        font-size: 1rem;
        margin: 0;
    }
    h4 {
        font-size: 1.2rem;
        font-weight: 400;
        line-height: 1.6;
    }
    ul {
        font-weight: 400;
        list-style-type: none;
        margin: 1.2rem 0;
        padding: 0;
    }
    li {
        margin: 1.2rem 0;
        line-height: 1.6;
    }
    .logo {
        max-width: 50%;
        margin: 0 auto;
    }
</style>
