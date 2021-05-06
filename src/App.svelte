<script>
    import User from "./User.svelte"
    import UserSearch from "./UserSearch.svelte"
    import { onMount } from 'svelte'
    let users;

    onMount(() => {
        getGitHubUsers()
    });

    function getGitHubUsers() {
        fetch("https://api.github.com/users")
        .then(resp => resp.json())
        .then(data => (users = data));
    }
</script>

<style>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
        display: flex;
        flex-flow: wrap;
    }

    li {
        width: 20%;
        margin-bottom: 20px;
    }
</style>


<main>
    <UserSearch />
    {#if users}
        <ul>
        {#each users as user}
            <li>
                <User username={user.login} avatar="{user.avatar_url}" />
            </li>
        {/each}
        </ul>
    {/if}
</main>
