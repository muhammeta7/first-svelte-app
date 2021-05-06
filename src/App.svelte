<script>
    import { onMount } from 'svelte'
    let users;

    onMount(() => {
        getGitHubUsers()
    });

    function getGitHubUsers() {
        fetch("https://api.github.com/users")
        .then(resp => resp.json())
        .then(data => {
            console.log(data);
            users = data;
        });
    }

</script>

<style>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }

    img{
        max-width: 50px;
    }
</style>


<main>
    {#if users}
        <ul>
    {#each users as user}
        <li>
            <img src={user.avatar_url} alt={`${user.login}'s Avatar`}>
            {user.login}
        </li>
    {/each}
        </ul>
        {/if}
</main>
<!--<header class="header">-->
<!--    <h1 class="header-title">Svelte powered markdown editor</h1>-->
<!--</header>-->

<!--<div class="markdown-editor">-->
<!--    <div class="markdown-editor__left-panel">-->
<!--        <textarea bind:value="{source}" class="markdown-editor__source"></textarea>-->
<!--    </div>-->

<!--    <div class="markdown-editor__right-panel">-->
<!--        <div class="markdown-editor__output">{@html markdown}</div>-->
<!--    </div>-->
<!--</div>-->

<!--<style>-->
<!--    .header {-->
<!--        height: 10vh;-->
<!--        display: flex;-->
<!--        align-items: center;-->
<!--        justify-content: center;-->
<!--    }-->

<!--    .header-title {-->
<!--        margin: 0;-->
<!--    }-->

<!--    .markdown-editor {-->
<!--        width: 100%;-->
<!--        display: flex;-->
<!--        align-items:flex-start;-->
<!--        justify-content: space-evenly;-->
<!--    }-->

<!--    .markdown-editor__left-panel, .markdown-editor__right-panel {-->
<!--        width: 50%;-->
<!--        border: solid 1px black;-->
<!--        height: 90vh;-->
<!--    }-->

<!--    .markdown-editor__right-panel {-->
<!--        overflow: auto;-->
<!--    }-->

<!--    .markdown-editor__source {-->
<!--        border: none;-->
<!--        width: 100%;-->
<!--        height: 100%;-->
<!--    }-->

<!--    .markdown-editor__source:focus {-->
<!--        outline: none;-->
<!--    }-->

<!--    .markdown-editor__output {-->
<!--        width: 100%;-->
<!--        padding: 0 2em;-->
<!--    }-->
<!--</style>-->
