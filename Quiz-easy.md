---
layout: default
---

<div id="quiz-container" class="quiz">
  <!-- Question 1 -->
  <div class="question-step active">
    <h3>Question 1: What is Terraria?</h3>
    
    <form id="quiz-form">
    <label>
      <input type="radio" name="type" value="wrong"> Large
    </label><br>
    <label>
      <input type="radio" name="type" value="correct"> Medium
    </label><br>
    <label>
      <input type="radio" name="type" value="wrong"> Small
    </label><br><br>
  </form>
    
    <p class="result-message checks"></p>
    
    <button type="button" class="submit" onclick="checkAnswer(this)">
    
    <button onclick="nextQuestion(1)" class="next-btn" disabled>Next</button>
  </div>

  <!-- Question 2 -->
  <div class="question-step">
    <h3>Question 2: Who is the first boss?</h3>
    
    <button onclick="nextQuestion(2)">Next</button>
  </div>

  <!-- Result Screen -->
  <div class="question-step">
    <h3>Quiz Finished!</h3>
  </div>
</div>



<script>

function checkAnswer(btn) {
  // Find the specific step container for this button
  const step = btn.closest('.question-step');
  const form = step.querySelector('.quiz-form');
  const result = step.querySelector('.result-message');
  const nextBtn = step.querySelector('.next-btn');
  const selected = form.querySelector('input[name="type"]:checked');

  if (!selected) {
    result.textContent = "Please select an answer first!";
    result.style.color = "orange";
    return;
  }

  if (selected.value === "correct") {
    result.textContent = "Correct! You can now proceed.";
    result.style.color = "green";
    
    // UNLOCK the next button
    nextBtn.disabled = false; 
  } else {
    result.textContent = "Wrong! Try again.";
    result.style.color = "red";
    
    // Keep it locked if they get it wrong
    nextBtn.disabled = true;
  }
}


function nextQuestion(currentStep) {
  // Get all question divs
  const steps = document.querySelectorAll('.question-step');
  
  // Hide current step
  steps[currentStep - 1].classList.remove('active');
  
  // Show next step
  if (steps[currentStep]) {
    steps[currentStep].classList.add('active');
  }
}
</script>

[back](./quiz.html)
