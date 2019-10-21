<script>
  const bestBands = [
    // initialize an array using brackets [], and put anything inside
    {
      // we're just making an "object" here using braces {}
      artist: 'Radiohead', // ... where the lefthand side is the "key" and the righthand side is the "value"
      description: 'Pretentious choice, but very good experimental cuts',
    },
    {
      artist: 'Foster the People',
      description: 'Pretty pop-y these days, but never forget Torches',
    },
    {
      artist: 'The Foals',
      description: 'Put out two flawless alt-rock albums this year',
    },
  ]
</script>

<!-- Create a loop using #each ARRAYNAME as ARRAYITEM -->
{#each bestBands as band}
  <!-- Use dot notation to get the key off of each object (ARRAYITEM.KEY)-->
  <h1>{band.artist}</h1>
  <p>{band.description}</p>
{/each}
