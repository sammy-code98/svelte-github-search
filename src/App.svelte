<script>
  import { onMount } from "svelte";
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
        console.log(data);
        // bind users to data
        users = data;
      });
  }
</script>

<main>
	<!-- loop through -->
	{#if users}
	<ul>
		{#each users as user}
		<li>{user.login}</li>
		{/each}
	</ul>
	{/if}

</main>

<style>
</style>
