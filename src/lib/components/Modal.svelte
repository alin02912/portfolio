<script>

import { fly, fade } from 'svelte/transition'
</script>

<div class="overlay" transition:fade="{{duration: 1000}}"></div>
<div class="menu-container" transition:fly="{{ y: 200, duration: 1000 }}">
    <ul>
        <li><a href="/#About">About</a></li>
        <li><a href="/#Profile">Profile</a></li>
        <li><a href="/#Work">Work</a></li>
        <li><a href="/#Contact">Contact</a></li>
    </ul>
</div>

<style>
    .overlay {
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        background-color: #0a0b0b88;
    }
    .menu-container {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    ul {
        padding: 0;
        margin: 0;
    }
    li {
        list-style-type: none;
        padding: 0;
        font-size: 1.5rem;
        line-height: 2;
    }
    a {
        text-decoration: none;
        color: #F5F5F1;
    }
</style>