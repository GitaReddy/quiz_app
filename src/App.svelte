<script>
  let questions = [
    {
      question: "What is the capital of France?",
      options: ["Paris", "London", "Berlin", "Madrid"],
      answer: "Paris"
    },
    {
      question: "What is the largest planet in our solar system?",
      options: ["Mars", "Jupiter", "Saturn", "Venus"],
      answer: "Jupiter"
    },

	{
        question: "What is the capital of Telangana?",
        options: ["Chennai", "Bangalore", "Hyderabad", "Pune"],
        answer: "Hyderabad"
      },
	  {
        question: "What is the capital of Karnataka?",
        options: ["Chennai", "Bangalore", "Hyderabad", "Pune"],
        answer: "Bangalore"
      },
    // Add more questions here
  ];

  let currentQuestion = 0;
  let selectedOption = null;
  let score = 0;

  function checkAnswer() {
    if (selectedOption === questions[currentQuestion].answer) {
      score++;
    }
    nextQuestion();
  }


  function resetQuiz() {
    currentQuestion = 0;
    answer = [];
  }

  function nextQuestion() {
    selectedOption = null;
    if (currentQuestion < questions.length - 1) {
      currentQuestion++;
    } else {
      alert(`Quiz completed! Your score is ${score}/${questions.length}`);
      // You can reset the quiz or redirect to another page here
      resetQuiz()
    }
  }
</script>

<div class="quiz-container">
  <h2>Question {currentQuestion + 1}</h2>
  <p>{questions[currentQuestion].question}</p>

  {#each questions[currentQuestion].options as option}
    <label>
      <input type="radio" bind:group={selectedOption} value={option} />
      {option}
    </label>
  {/each}

  <button style="margin-top:10px;" on:click={checkAnswer} disabled={selectedOption === null}>
    Submit
  </button>
</div>

<style>
  .quiz-container {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #f7f7f7;
  }
</style>
