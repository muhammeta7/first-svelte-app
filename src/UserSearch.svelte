<script>
    import User from './User.svelte'
    let user;
    let query = '';

    function handleSubmit(e) {
        e.preventDefault();
        fetch(`https://api.github.com/users/${query}`)
            .then(resp => resp.json())
            .then(data => (user = data));
    }
</script>

<style>
    .user-search {
        padding: 20px;
        background: #eee;
        border-radius: 10px;
        margin-bottom: 40px;
    }
</style>

<div class="user-search">
    <form on:submit={handleSubmit}>
        <input type="text" bind:value={query}>
        <button>Search</button>
    </form>

<!--    Display user here-->
    {#if user}
        <User username={user.login} avatar={user.avatar_url} />
    {/if}
</div>
