# MB-compatibility-
Compatibility Score for MB results 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>MBTI Compatibility Checker</title>
<script>
  const types = ["INTJ","ENFP","ENTP","INFJ","ENTJ","INFP","ENFJ","INTP","ISTP","ESTP","ISFJ","ESFJ","ISTJ","ESTJ","ISFP","ESFP"];

  // Compatibility data template (simplified; you can update values)
  const compatibilityData = {};
  types.forEach(your => {
    compatibilityData[your] = {};
    types.forEach(partner => {
      if(your === partner){
        compatibilityData[your][partner] = { score: 80, good: "Mutual understanding", bad: "Both risk rigidity" };
      } else {
        compatibilityData[your][partner] = { 
          score: Math.floor(Math.random()*40) + 60, 
          good: "Some complementary traits", 
          bad: "Some potential friction" 
        };
      }
    });
  });

  function init() {
    const yourType = document.getElementById('yourType');
    const partnerType = document.getElementById('partnerType');
    const submitBtn = document.getElementById('submitBtn');

    // Populate dropdowns dynamically
    types.forEach(t => {
      const option1 = document.createElement("option");
      option1.value = t;
      option1.textContent = t;
      yourType.appendChild(option1);

      const option2 = document.createElement("option");
      option2.value = t;
      option2.textContent = t;
      partnerType.appendChild(option2);
    });

    function updateButtonState() {
      submitBtn.disabled = !(yourType.value && partnerType.value);
    }

    yourType.addEventListener('change', updateButtonState);
    partnerType.addEventListener('change', updateButtonState);

    // ensure initial state
    updateButtonState();
  }

  function checkCompatibility() {
    const you = document.getElementById("yourType").value;
    const partner = document.getElementById("partnerType").value;
    const resultBox = document.getElementById("result");

    if (!you || !partner) {
      resultBox.innerHTML = `<p>Please select both types and press Submit.</p>`;
      return;
    }

    const data = compatibilityData[you][partner];
    resultBox.innerHTML = `
      <h3>${you} + ${partner}</h3>
      <p><strong>Compatibility:</strong> ${data.score}%</p>
      <p><strong>Strengths:</strong> ${data.good}</p>
      <p><strong>Challenges:</strong> ${data.bad}</p>
    `;
  }

  window.addEventListener('DOMContentLoaded', init);
</script>
<style>
  body { font-family: Arial, sans-serif; margin: 20px; }
  .card { border: 1px solid #ddd; padding: 16px; border-radius: 8px; max-width: 720px; }
  label { display: block; margin-bottom: 6px; }
  select { width: 220px; padding: 6px; }
  button { padding: 8px 14px; font-size: 16px; }
  #result { margin-top: 20px; padding: 10px; border: 1px solid #ccc; border-radius: 6px; }
</style>
</head>
<body>
<div class="card">
  <h1>MBTI Compatibility Checker</h1>
  <p>Select your type and your partner's type, then press <strong>Submit</strong>.</p>

  <label for="yourType">Your Type:</label>
  <select id="yourType">
    <option value="">-- Select Type --</option>
  </select>

  <br /><br />

  <label for="partnerType">Partner's Type:</label>
  <select id="partnerType">
    <option value="">-- Select Type --</option>
  </select>

  <br /><br />

  <button id="submitBtn" onclick="checkCompatibility()">Submit</button>
  <div id="result"></div>
</div>
</body>
</html>
