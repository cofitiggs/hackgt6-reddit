<script>
  export let title = ''
  export let content = ''
  export let author = ''
  export let votes = 0 // the "initial" votes before you started upvoting or downvoting
  export let id = ''

  let currentVotes = votes

  let upvoted = false
  let downvoted = false

  const updateVotes = newVotes => {
    const updates = {
      postId: id,
      votes: newVotes,
    }
    let options = {
      method: 'POST', // to specify that we want to post something to the database
      body: JSON.stringify(updates), // put the content we want to add in the body. Turn it into a string in order to send!
      headers: {
        'Content-Type': 'application/json',
      },
    }
    fetch('https://hackgt-reddit.now.sh', options).catch(err =>
      console.error(err)
    ) // log if something bad happens
  }

  const upvote = () => {
    upvoted = !upvoted // toggle the upvote flag
    downvoted = false // set downvote to false, since we're trying to upvote now
    /* 
      if the upvote flag is true, then we add a vote.
      If the flag is false, then we unselected our upvote, and need to bring the votes back down!
    */
    const newVotes = upvoted ? votes + 1 : votes
    updateVotes(newVotes) // send API call to update votes
    currentVotes = newVotes // update the votes locally to instantly see the change
  }
  const downvote = () => {
    downvoted = !downvoted
    upvoted = false
    const newVotes = downvoted ? votes - 1 : votes
    updateVotes(newVotes)
    currentVotes = newVotes
  }
</script>

<style>
  section {
    display: flex;
    align-items: center;
  }
  button {
    width: 30px;
    height: 30px;
  }
  .votes {
    margin-top: 10px;
    margin-bottom: 10px;
    text-align: center;
  }
  .button-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-right: 20px;
  }
</style>

<section>
  <div class="button-container">
    <button on:click={upvote}>
      <img src="/icons/up-arrow.svg" alt="" />
    </button>
    <p class="votes">{currentVotes}</p>
    <button on:click={downvote}>
      <img src="/icons/down-arrow.svg" alt="" />
    </button>
  </div>
  <div>
    <h1>{title}</h1>
    <p>{author}</p>
    <p>{content}</p>
  </div>
</section>
