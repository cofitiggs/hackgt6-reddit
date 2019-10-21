<script>
  import Post from './Post.svelte'

  const posts = [
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
  console.log(posts)
</script>

{#each posts as post}
  <Post title={post.title} content={post.content} votes={post.votes} />
{/each}
