<script>
  let dittoInfo = {
    name: '',
    picture: '',
    picture2: '',
  }

  fetch('https://pokeapi.co/api/v2/pokemon/ditto/') // kick off the API call. Once it's done, our first .then callback function will fire
    .then(response => {
      return response.json() // when the information comes back, turn it into an object we can use (a JSON object)
    })
    .then(json => {
      dittoInfo = {
        // then, we can take the JSON object we created in the last callback to assign to our variable
        name: json.name,
        picture: json.sprites.front_default,
        picture2: json.sprites.front_shiny,
      }
    })
</script>

<img src={dittoInfo.picture} alt="Purple Ditto" />
<img src={dittoInfo.picture2} alt="Blue Ditto" />
<h1>{dittoInfo.name}</h1>
