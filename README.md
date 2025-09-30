# MB-compatibility-
Compatibility Score for MB results 
!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>MBTI Compatibility Checker</title>
<script>
  const types = ["INTJ","ENFP","ENTP","INFJ","ENTJ","INFP","ENFJ","INTP","ISTP","ESTP","ISFJ","ESFJ","ISTJ","ESTJ","ISFP","ESFP"];

  const compatibilityData = {
    "INTJ": {
      "INTJ": { score: 80, good: "Mutual understanding, shared vision", bad: "Both risk rigidity and overthinking" },
      "ENFP": { score: 95, good: "Playful, spontaneous, balances seriousness", bad: "May feel scattered vs. your structure" },
      "ENTP": { score: 90, good: "Intellectual sparring partner", bad: "Can cause friction with constant debating" },
      "INFJ": { score: 90, good: "Shared depth and vision", bad: "Can get lost in overthinking" },
      "ENTJ": { score: 85, good: "Ambitious power couple", bad: "Leadership clashes possible" },
      "INFP": { score: 80, good: "Empathy softens your logic", bad: "May feel too idealistic" },
      "ENFJ": { score: 80, good: "Inspires growth, emotional leadership", bad: "May overwhelm with intensity" },
      "INTP": { score: 75, good: "Shared curiosity", bad: "Both may struggle with practical matters" },
      "ISTP": { score: 70, good: "Independent, capable", bad: "Too unstructured for you" },
      "ESTP": { score: 70, good: "Fun and energetic", bad: "Clashes with planning" },
      "ISFJ": { score: 70, good: "Reliable and caring", bad: "Too traditional for your taste" },
      "ESFJ": { score: 65, good: "Warm and social", bad: "May overwhelm introversion" },
      "ISTJ": { score: 65, good: "Steady and loyal", bad: "Too rigid and detail-focused" },
      "ESTJ": { score: 65, good: "Organized and strong-willed", bad: "Control clashes" },
      "ISFP": { score: 60, good: "Gentle and fun", bad: "Lacks long-term planning" },
      "ESFP": { score: 55, good: "Energetic and lively", bad: "Too spontaneous for your structure" }
    },
    "ENFP": {
      "INTJ": { score: 95, good: "Exciting, adventurous, sparks creativity", bad: "May push too hard on structure" },
      "ENFP": { score: 80, good: "Playful and adventurous", bad: "Both may struggle with follow-through" },
      "ENTP": { score: 90, good: "Fun, spontaneous, debates intellectually", bad: "Can become scattered" },
      "INFJ": { score: 85, good: "Deep emotional connection", bad: "INFJ may need more stability" },
      "ENTJ": { score: 80, good: "Ambitious and inspiring", bad: "ENTJ dominance may overwhelm" },
      "INFP": { score: 85, good: "Shared idealism", bad: "Can get lost in fantasies" },
      "ENFJ": { score: 90, good: "Social and dynamic energy", bad: "May compete for attention" },
      "INTP": { score: 80, good: "Curiosity and learning", bad: "May lack emotional depth at times" },
      "ISTP": { score: 70, good: "Adventurous and flexible", bad: "May feel too detached" },
      "ESTP": { score: 85, good: "High energy, spontaneous fun", bad: "Can be reckless together" },
      "ISFJ": { score: 65, good: "Caring and loyal partner", bad: "May clash with ENFP spontaneity" },
      "ESFJ": { score: 80, good: "Social harmony and warmth", bad: "May overwhelm ENFP independence" },
      "ISTJ": { score: 60, good: "Stable and dependable", bad: "Too rigid for ENFP" },
      "ESTJ": { score: 70, good: "Organized and energetic", bad: "May clash on impulsivity" },
      "ISFP": { score: 75, good: "Gentle, fun-loving", bad: "May avoid planning" },
      "ESFP": { score: 90, good: "Fun-loving, energetic", bad: "Can be too spontaneous" }
    },
    "ENTP": {
      "INTJ": { score: 90, good: "Exciting debates and challenges", bad: "May frustrate INTJ logic" },
      "ENFP": { score: 90, good: "Creative and spontaneous energy", bad: "Both may lack focus" },
      "ENTP": { score: 80, good: "Energetic and playful", bad: "Can be chaotic together" },
      "INFJ": { score: 75, good: "Deep discussions and inspiration", bad: "INFJ may need more stability" },
      "ENTJ": { score: 85, good: "Ambitious and intellectually stimulating", bad: "Leadership clashes possible" },
      "INFP": { score: 70, good: "Curiosity and open-mindedness", bad: "May lack emotional connection" },
      "ENFJ": { score: 85, good: "Dynamic, social energy", bad: "Competition for attention" },
      "INTP": { score: 90, good: "Great intellectual connection", bad: "May avoid emotions" },
      "ISTP": { score: 70, good: "Independent and adventurous", bad: "Can be inconsistent" },
      "ESTP": { score: 85, good: "Fun, adventurous, energetic", bad: "Risk of impulsiveness" },
      "ISFJ": { score: 60, good: "Stable and reliable", bad: "May feel constrained" },
      "ESFJ": { score: 75, good: "Social and friendly", bad: "May clash on impulsiveness" },
      "ISTJ": { score: 65, good: "Organized and logical", bad: "Can feel too rigid" },
      "ESTJ": { score: 80, good: "Energetic and ambitious", bad: "Potential control issues" },
      "ISFP": { score: 70, good: "Gentle and creative", bad: "May avoid structure" },
      "ESFP": { score: 85, good: "Fun and lively", bad: "Can be too spontaneous" }
    },
    "INFJ": {
      "INTJ": { score: 90, good: "Shared vision and depth", bad: "Can overthink together" },
      "ENFP": { score: 85, good: "Emotional connection and excitement", bad: "May feel scattered" },
      "ENTP": { score: 75, good: "Thought-provoking conversations", bad: "May lack emotional stability" },
      "INFJ": { score: 80, good: "Mutual understanding and empathy", bad: "Both can overanalyze" },
      "ENTJ": { score: 80, good: "Ambitious pairing", bad: "Leadership clashes possible" },
      "INFP": { score: 85, good: "Shared idealism", bad: "Can get lost in emotion" },
      "ENFJ": { score: 90, good: "Strong emotional and social bond", bad: "Both can dominate attention" },
      "INTP": { score: 75, good: "Intellectual connection", bad: "May struggle emotionally" },
      "ISTP": { score: 65, good: "Independent and thoughtful", bad: "May feel detached" },
      "ESTP": { score: 65, good: "Fun and dynamic", bad: "May clash with introspection" },
      "ISFJ": { score: 70, good: "Caring and loyal", bad: "May feel restricted" },
      "ESFJ": { score: 75, good: "Social harmony", bad: "Both can overextend socially" },
      "ISTJ": { score: 65, good: "Stable and dependable", bad: "Can be rigid" },
      "ESTJ": { score: 70, good: "Organized and structured", bad: "May clash on control" },
      "ISFP": { score: 70, good: "Gentle and creative", bad: "May lack structure" },
      "ESFP": { score: 65, good: "Energetic and playful", bad: "Can feel superficial" }
    },
    "ENTJ": {
      "INTJ": { score: 85, good: "Power couple, ambitious", bad: "Leadership clashes" },
      "ENFP": { score: 80, good: "Exciting, inspiring energy", bad: "May feel chaotic" },
      "ENTP": { score: 85, good: "Dynamic, intellectually stimulating", bad: "Power struggles possible" },
      "INFJ": { score: 80, good: "Visionary pairing", bad: "Can overanalyze" },
      "ENTJ": { score: 80, good: "Ambitious and goal-oriented", bad: "Leadership clashes likely" },
      "INFP": { score: 70, good: "Brings emotional insight", bad: "May feel idealistic" },
      "ENFJ": { score: 85, good: "Strong social and leadership energy", bad: "Both may dominate" },
      "INTP": { score: 75, good: "Intellectual stimulation", bad: "May lack emotional connection" },
      "ISTP": { score: 70, good: "Independent, capable", bad: "May feel detached" },
      "ESTP": { score: 75, good: "Energetic and decisive", bad: "May clash on impulsiveness" },
      "ISFJ": { score: 65, good: "Caring and loyal", bad: "May feel too constrained" },
      "ESFJ": { score: 70, good: "Social and warm", bad: "Can feel controlling" },
      "ISTJ": { score: 75, good: "Organized and reliable", bad: "Both can be rigid" },
      "ESTJ": { score: 80, good: "Strong leadership duo", bad: "Potential power struggle" },
      "ISFP": { score: 60, good: "Gentle balance", bad: "May lack ambition alignment" },
      "ESFP": { score: 65, good: "Fun energy", bad: "May clash on planning" }
    },
    // Repeat for the remaining 10 types: INFP, ENFJ, INTP, ISTP, ESTP, ISFJ, ESFJ, ISTJ, ESTJ, ISFP, ESFP
  };

  // For brevity, remaining types use placeholders but can be expanded similarly
  types.forEach(your => {
    if(!compatibilityData[your]){
      compatibilityData[your] = {};
      types.forEach(partner => {
        compatibilityData[your][partner] = { score: 70, good: "Some complementary traits", bad: "Some potential friction" };
      });
    }
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
    resultBox.innerHTML
