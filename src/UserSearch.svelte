<script>
    import User from './User.svelte'
  let usernameQuery = "";
  let user = "";
  //   search for user on form submission
  function handleSubmit(e) {
    e.preventDefault();
    fetch(`https://api.github.com/users/${usernameQuery}`)
      .then((res) => res.json())
      .then((data) => {
          console.log(data);
        user = data;
      });
  }
</script>

<main>
  <div class="user-search">
    <h2>Search for Users</h2>
    <!-- event binding -->
    <form on:submit={handleSubmit}>
      <!-- data binding -->
      <input type="text" bind:value={usernameQuery} />
      <button>Search</button>
    </form>
  </div>
  <!-- display search result -->
  <div>
    {#if user}
    <User username={user.login} avatar={user.avatar_url} />
  {/if}
  </div>
</main>

<style>
  .user-search {
    padding: 20px;
    border-radius: 10px;
    margin-bottom: 50px;
    background: rgb(250, 234, 234);
  }
  h2 {
    text-align: center;
    margin: 0 0 15px;
  }
  form {
    transform: translateX(35%);
    margin-top: 20px;
  }
  input {
    border: none;
    border-radius: 8px;
    padding: 10px;
  }
  button {
    border: none;
    border-radius: 8px;
    padding: 10px;
    margin: 12px;
    background: #fff;
    cursor: pointer;
  }

  	@media screen and (max-width: 480px) {
      .user-search{
        padding: 5px;
      }
      form{
        transform: translateX(10%);
      }
      button{
        width: 80%;
        margin-left: 0px;
      }
    }

</style>
