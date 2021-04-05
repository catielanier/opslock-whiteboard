<script>
  export let comments;
</script>

<style>
  .cmt {
    display: grid;
    grid-template-columns: 1fr 9fr;
    margin: 15px 0;
    padding: 0 15px 0 0;
  }
  .cmt-content {
    background-color: #fff;
    padding: 12px;
    border-radius: 5px;
  }
  .cmt-content > div:last-child {
    color: grey;
  }
  .cmt-header {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    margin-bottom: 10px;
  }
  .cmt-header div:last-child {
    text-align: end;
    color: #c1c6cc;
  }
  .cmt-sidebar {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    justify-content: center;
  }
  .cmt-sidebar .cmt-bar {
    background: #c1c6cc;
    width: 3px;
    margin-top: 12.5px;
    margin-bottom: -10px;
    flex-grow: 1;
    z-index: 1;
  }
  .cmt-sidebar .cmt-bar.bar-hidden {
    visibility: hidden;
  }
  .cmt-image {
    width: 30px;
    height: 30px;
    margin-top: 7.5px;
    border-radius: 50%;
    overflow: hidden;
  }
  .cmt-image img {
    height: 40px;
  }
</style>

{#each comments as c, index}
  <div class="cmt">
    <div class="cmt-sidebar">
      <div class="cmt-image">
        <img src={c.profilePictureUrl} alt={c.name} />
      </div>
      {#if index !== comments.length - 1}
        <div class="cmt-bar" />
      {/if}
      {#if index === comments.length - 1}
        <div class="cmt-bar bar-hidden" />
      {/if}
    </div>
    <div class="cmt-content">
      <div class="cmt-header">
        <div>{c.name}</div>
        <div>{new Date(c.date).toLocaleString()}</div>
      </div>
      <div>{c.message}</div>
    </div>
  </div>
{/each}
