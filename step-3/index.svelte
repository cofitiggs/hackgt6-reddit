<script>
  import Post from './Post.svelte'

  let posts = [
    {
      title: "You won't believe this!",
      content: '😱😱😱',
      votes: 20,
    },
    {
      title: 'You will believe this.',
      content: '😐😐😐',
      votes: 30,
    },
    {
      title: 'Idk what to believe anymore',
      content: '🤔🤔🤔',
      votes: 40,
    },
  ]

  let newPostTitle = ''
  let newPostContent = ''

  const addPost = () => {
    posts = [
      ...posts,
      {
        title: newPostTitle,
        content: newPostContent,
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
  <Post title={post.title} content={post.content} votes={post.votes} />
{/each}
