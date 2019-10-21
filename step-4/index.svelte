<script>
  import Post from './Post.svelte'

  let posts = []

  let newPostTitle = ''
  let newPostContent = ''

  const username = 'Hugh Jazz'

  setInterval(() => {
    fetch('URL')
      .then(response => response.json())
      .then(json => (posts = json.posts))
  }, 2000)

  const addPost = () => {
    if (newPostTitle === '' || newPostContent === '') {
      return // don't create the post if either of the textboxes are empty
    }

    posts = [
      ...posts,
      {
        title: newPostTitle,
        content: newPostContent,
        author: username,
        votes: 0,
      },
    ]
    newPostTitle = ''
    newPostContent = ''
  }
</script>

<style>
  form {
    display: flex;
    flex-direction: column;
  }
</style>

<form on:submit|preventDefault={addPost}>
  <label>Title</label>
  <input bind:value={newPostTitle} />
  <label>Woke content</label>
  <textarea bind:value={newPostContent} />
  <button type="submit">Post!</button>
</form>

{#each posts as post}
  <Post
    title={post.title}
    content={post.content}
    author={post.author}
    votes={post.votes} />
{/each}
