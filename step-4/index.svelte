<script>
  import Post from './Post.svelte'
  import { onMount } from 'svelte'

  let posts = []

  let newPostTitle = ''
  let newPostContent = ''

  const username = 'Hugh Jazz'

  const fetchPosts = () => {
    fetch('https://hackgt-reddit.now.sh')
      .then(response => response.json())
      .then(json => (posts = json))
  }

  onMount(
    () => {
      fetchPosts() // run fetchPosts the first time (setInterval will call this function 5 seconds later)
      const refresh = setInterval(() => fetchPosts, 5000) // use setInterval to run the fetchPosts function every 5 seconds
    },
    () => clearInterval(refresh) // fancy Svelte syntax here. Allows us to close the interval once the page is closed. Not necessary, but encouraged.
  )

  const addPost = () => {
    if (newPostTitle === '' || newPostContent === '') {
      return // don't create the post if either of the textboxes are empty
    }

    const newPost = {
      title: newPostTitle,
      content: newPostContent,
      author: username,
      votes: 0,
    }

    let options = {
      method: 'POST', // to specify that we want to post something to the database
      body: JSON.stringify(newPost), // put the content we want to add in the body. Turn it into a string in order to send!
      headers: {
        'Content-Type': 'application/json',
      },
    }
    fetch('https://hackgt-reddit.now.sh', options).catch(err =>
      console.error(err)
    ) // log if something bad happens

    posts = [...posts, newPost] // add the post to the local array of "posts" so you can see the addition instantly
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
