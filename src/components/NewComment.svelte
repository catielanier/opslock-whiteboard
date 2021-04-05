<script>
  export let submit;
  export let valid;
</script>

<style>
  form {
    background: white;
    width: 100%;
  }
  input {
    width: 100%;
    border: 0;
    padding: 15px 10px;
  }
  input::placeholder {
    color: #adb2be;
  }
  form div {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
  button {
    background: white;
    border: 0;
    color: #416ac5;
    padding: 15px 20px;
    margin-bottom: 0;
  }
</style>

<form
  id="theForm"
  on:submit|preventDefault={() => {
    if (valid(document.querySelector('input[name="Description"]'))) {
      submit();
    }
  }}>
  <div>
    <input name="Description" type="text" placeholder="Type here..." />
    <button type="submit">Comment</button>
  </div>
</form>
