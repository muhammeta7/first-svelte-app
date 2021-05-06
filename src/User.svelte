<script>
    export let username;
    export let avatar;
</script>

<style>
    img {
        max-width: 50px;
    }

    h3 {
        margin: 0;
    }
</style>

<img src={avatar} alt={`${username}'s Avatar`}>
<h3>{username}</h3>
