<script>
  export let title = ''
  export let content = ''
  export let votes = 0
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
    <button>
      <img src="/icons/up-arrow.svg" alt="" />
    </button>
    <p class="votes">{votes}</p>
    <button>
      <img src="/icons/down-arrow.svg" alt="" />
    </button>
  </div>
  <div>
    <h1>{title}</h1>
    <p>{content}</p>
  </div>
</section>
