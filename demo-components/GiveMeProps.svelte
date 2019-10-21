<script>
  export let name = 'James Wang' // use "export" to expose a variable as a "prop"
  export let description = 'Amateur web developer, dude with no chill'
  export let picture =
    'https://media.licdn.com/dms/image/C5603AQHoBvk0rksJEA/profile-displayphoto-shrink_800_800/0?e=1577318400&v=beta&t=cA6W98ipsvcelFHgIVt3KRCJKb6lBroehH7YuvRdy8I'
</script>

<!-- Use bracket syntax {...} to insert variables into your HTML -->
<img src={picture} alt="The real James Wang" />
<h1>{name}</h1>
<p>{description}</p>
