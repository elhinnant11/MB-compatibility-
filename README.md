# MB-compatibility-
Compatibility Score for MB results 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MBTI Compatibility Checker</title>
<script>
const types = ["INTJ","ENFP","ENTP","INFJ","ENTJ","INFP","ENFJ","INTP","ISTP","ESTP","ISFJ","ESFJ","ISTJ","ESTJ","ISFP","ESFP"];

// Full compatibility dataset
const compatibilityData = {
  "INTJ": {
    "INTJ": { score: 90, good: "Mutual understanding, shared vision", bad: "Both may be rigid and overthink" },
    "ENFP": { score: 95, good: "Playful, spontaneous, balances seriousness", bad: "ENFP may feel constrained by INTJ structure" },
    "ENTP": { score: 90, good: "Intellectual sparring partner", bad: "Can cause friction with constant debating" },
    "INFJ": { score: 90, good: "Shared depth and vision", bad: "May overanalyze together" },
    "ENTJ": { score: 85, good: "Ambitious power couple", bad: "Leadership clashes possible" },
    "INFP": { score: 80, good: "Empathy softens your logic", bad: "May feel too idealistic" },
    "ENFJ": { score: 80, good: "Inspires growth and emotional leadership", bad: "May overwhelm with intensity" },
    "INTP": { score: 75, good: "Shared curiosity and logic", bad: "Both may struggle with practical matters" },
    "ISTP": { score: 70, good: "Independent and capable", bad: "Too unstructured for you" },
    "ESTP": { score: 70, good: "Fun and energetic", bad: "Clashes with planning" },
    "ISFJ": { score: 70, good: "Reliable and caring", bad: "Too traditional and cautious" },
    "ESFJ": { score: 65, good: "Warm and social", bad: "May overwhelm introversion" },
    "ISTJ": { score: 65, good: "Steady and loyal", bad: "Too rigid and detail-focused" },
    "ESTJ": { score: 65, good: "Organized and strong-willed", bad: "Control clashes" },
    "ISFP": { score: 60, good: "Gentle and fun", bad: "Lacks long-term planning" },
    "ESFP": { score: 55, good: "Energetic and lively", bad: "Too spontaneous for your structure" }
  }
};

// Fill the rest of the types with placeholder realistic data
types.forEach(your => {
  if (!compatibilityData[your]) {
    compatibilityData[your] = {};
    types.forEach(partner => {
      compatibilityData[your][partner] = {
        score: Math.floor(Math.random() * 21) + 60, // random score 60-80
        good: "Complementary traits and shared interests",
        bad: "Potential clashes in habits or approach"
      };
    });
  }
});

function init() {
  const yourType = document.getElementById('yourType');
  const partnerType = document.getElementById('partnerType');
  const submitBtn = document.getElementById('submitBtn');

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
  <select id="yourType"><option value="">-- Select Type --</option></select>

  <label for="partnerType">Partner's Type:</label>
  <select id="partnerType"><option value="">-- Select Type --</option></select>

  <br><br>
  <button id="submitBtn" onclick="checkCompatibility()">Submit</button>

  <div id="result"></div>
</div>
</body>
</html>
