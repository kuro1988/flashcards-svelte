<script>

  import {onMount} from 'svelte'

  const url = 'https://raw.githubusercontent.com/kuro1988/flashcards/master/questions.json'

  let question

	const updateQuestion = async () => {

    const result = await fetch(url)
    const data = await result.json()
    let index = Math.floor(Math.random()*(data.questions.length))
    question = (data.questions[index]).question

    // return question

  }

  onMount(() => {
    updateQuestion()
  })

</script>

<style>

</style>

<main>

  <div id="question-box">

    <div id="hero">

      <p id="text" className="question">
      {question}
        <br />
      </p>

    </div>

    <div className="buttons is-centered">
      <button id="new-question" on:click={updateQuestion} className="button is-info">
        New Question
      </button>

    </div>

  </div>




</main>

