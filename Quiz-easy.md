---
layout: default
---

<div id="quiz-container" class="quiz">
  <!-- Question 1 -->
  <div class="question-step active">
    <h3>Question 1: What is the recommended world size for beginners?</h3>
    
    <form class="quiz-form">
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
    
    <button type="button" class="submit" onclick="checkAnswer(this)">Check Answer</button>
    
    <button onclick="nextQuestion(1)" class="next-btn submit" disabled>Next</button>
  </div>

  <!-- Question 2 -->
  <div class="question-step">
    <h3>Question 2: What are the items that you get when first spawning?</h3>
    
    <form class="quiz-form">
    <label>
      <input type="radio" name="type" value="wrong"> Iron Shortsword, Iron Pickaxe, and Iron Axe
    </label><br>
    <label>
      <input type="radio" name="type" value="correct"> Tin Shortsword, Tin Pickaxe, and Tin Axe
    </label><br>
    <label>
      <input type="radio" name="type" value="wrong"> Copper Shortsword, Copper Pickaxe, and Copper Axe
    </label><br><br>
  </form>
    
    <p class="result-message checks"></p>
    
    <button type="button" class="submit" onclick="checkAnswer(this)">Check Answer</button>
    
    <button onclick="nextQuestion(2)" class="next-btn submit" disabled>Next</button>
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
