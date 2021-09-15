<script>
  import { onMount } from "svelte";
  import User from './User.svelte'
  import UserSearch from './UserSearch.svelte'
  //   create container to hold users
  let users;
  //   run this function once the lifecyle method happens
  onMount(() => {
    grabUsers();
  });
  // grab users from github
  function grabUsers() {
    fetch("https://api.github.com/users")
      .then((res) => res.json())
      .then((data) => {
        // console.log(data);
        // bind users to data
        users = data;
      });
  }
</script>

<main>
	<UserSearch />
	<!-- loop through -->
	{#if users}
	<ul class="user-list">
		{#each users as user}
		<li>
			<User username={user.login}  avatar={user.avatar_url}/>
		</li>
		{/each}
	</ul>
	{/if}

</main>

<style>
	.user-list{
		display: flex;
		flex-flow: wrap;
		list-style: none;
		margin: 0;
		padding: 0;
	}
	.user-list li{
		width: 20%;
		padding: 10px;
	}
</style>
