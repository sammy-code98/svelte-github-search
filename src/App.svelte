<script>
  import { onMount } from "svelte";
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
      });
  }
</script>

<main />

<style>
</style>
