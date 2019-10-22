<script>
  let name = 'Ben'
  let description = 'Really smart'

  let resultText = ''

  const updateBio = event => {
    /*
      A submit callback is passed an "event" parameter.
      This specifies what event should occur by default, which we want to disable.
      By default, the page will open a URL with our form values as parameters.
      If that's confusing to you, don't worry! It's a holdover from the old days of web development.
    */
    event.preventDefault()
    resultText = `Updated name to "${name}" with description "${description}"`
  }
</script>

<style>
  section {
    border: 1px solid red;
    border-radius: 5px;
  }
  form {
    display: flex;
    flex-direction: column;
  }
</style>

<section>
  <h1>Edit user bio</h1>
  <form on:submit={updateBio}>
    <!--Here, we "bind" the input's "value" to the value of our "name" variable. They'll always stay in sync!-->
    <input bind:value={name} />
    <!--Use a <textarea> for long form text-->
    <textarea bind:value={description} />
    <!--Use type="submit" to identify this button as the form's submit button-->
    <button type="submit">Update</button>
  </form>
  <p>{resultText}</p>

</section>
