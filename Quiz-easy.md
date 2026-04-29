---
layout: default
---

<div id="quiz-container" class="quiz">
  <h3>What is the type of world recommended for beginners</h3>
  
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

  <p id="result-message" class="checks"></p>

  <h3>What items did you get when first spawning?</h3>
  
  <form id="quiz-form">
   <label>
       <input type="radio" name="type" value="wrong"> Iron Broadsword, Iron Pickaxe, Iron Hammer
   </label><br>
     <label>
       <input type="radio" name="type" value="wrong"> Tin Shortsword, Tin Pickaxe, Tin Axe
     </label><br>
     <label>
       <input type="radio" name="type" value="wrong"> Tungsten Broadsword, Tungsten Pickaxe, Tungsten Hammer.
     </label><br>
     <label>
       <input type="radio" name="type" value="correct"> Copper Shortsword, Copper Pickaxe, Copper Axe
     </label><br><br>
  </form>
  
  <p id="result-message" class="checks"></p>
  
  <button type="button" class="submit" onclick="checkAnswer()">
      Submit Answer
    </button>
</div>

<script>
function checkAnswer() {
  const form = document.getElementById('quiz-form');
  const result = document.getElementById('result-message');
  const selected = form.querySelector('input[name="type"]:checked');

  if (!selected) {
    result.textContent = "Please select an answer first!";
    result.style.color = "orange";
    return;
  }

  if (selected.value === "correct") {
    result.textContent = "Correct! The ancient spirits of light and dark have been released.";
    result.style.color = "green";
  } else {
    result.textContent = "Wrong! Try again, Noob.";
    result.style.color = "red";
  }
}
</script>

[back](./quiz.html)
