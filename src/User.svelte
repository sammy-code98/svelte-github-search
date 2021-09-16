<script>
  // exporting props
  export let username;
  export let avatar;
</script>

<main>
  <div class="user">
    <img src={avatar} alt="{username}'s avatar" />
    <h3>{username}</h3>
  </div>
</main>

<style>
  .user {
    padding: 5px;
    border-radius: 5px;
    text-align: center;
    margin-left: 160px;
  }
  img {
    border-radius: 5px;
    max-width: 80px;
  }

  h3 {
    font-size: 16px;
    margin: 0;
  }
  @media screen and (max-width: 480px) {
    .user {
      margin: 30px;
      padding: 20px;
    }
  }
</style>
