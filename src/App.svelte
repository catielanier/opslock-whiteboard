<script>
  import Comments from "./components/Comments.svelte";
  import NewComment from "./components/NewComment.svelte";
  export let comments;
  export let username;

  let newComments = comments;
  let useNew = false;

  function valid(field) {
    var state = {
      saved: true,
      requirements: {
        Description: {
          required: true,
          maxlength: 140,
        },
        Files: {},
      },
    };

    if (!state.requirements[field.name]) {
      return true;
    }

    // required
    if (state.requirements[field.name].required) {
      if (field.tagName === "input" && field.value.length == 0) {
        field.classList.add("error");
        return false;
      } else if (field.value === undefined || field.value === "") {
        field.classList.add("error");
        return false;
      }
    }

    // max length
    if (state.requirements[field.name].maxlength) {
      if (field.value.length > state.requirements[field.name].maxlength) {
        field.classList.add("error");
        return false;
      }
    }

    field.classList.remove("error");
    return true;
  }

  function submit() {
    newComments = [
      ...comments,
      {
        name: username,
        message: document.querySelector("input[name='Description'").value,
        date: new Date().toISOString(),
      },
    ];
    useNew = true;
    document.querySelector('input[name="Description"]').value = "";
  }
</script>

<Comments comments={newComments} />
<NewComment {valid} {submit} />
