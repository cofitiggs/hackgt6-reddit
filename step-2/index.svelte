<script>
  import Post from './Post.svelte'

  const posts = [
    {
      title: "You won't believe this!",
      content: '😱😱😱',
      author: 'Alex Jones',
      votes: 20,
    },
    {
      title: 'You will believe this.',
      content: '😐😐😐',
      author: 'The NY Times',
      votes: 30,
    },
    {
      title: 'Idk what to believe anymore',
      content: '🤔🤔🤔',
      author: 'Elon Musk',
      votes: 40,
    },
  ]
</script>

{#each posts as post}
  <Post
    title={post.title}
    content={post.content}
    author={post.author}
    votes={post.votes} />
{/each}
