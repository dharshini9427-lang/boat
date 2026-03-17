<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Recipe Generator</title>
  <style>
    body {
      font-family: Arial;
      background: #f5f5f5;
      text-align: center;
    }
    .container {
      width: 400px;
      margin: 50px auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px gray;
    }
    input {
      width: 70%;
      padding: 10px;
      margin: 10px 0;
    }
    button {
      padding: 10px 15px;
      background: green;
      color: white;
      border: none;
      cursor: pointer;
    }
    .recipe {
      text-align: left;
      margin-top: 20px;
    }
  </style>
</head>
<body>

<div class="container">
  <h2>🍳 Recipe Generator</h2>
  
  <input type="text" id="search" placeholder="Enter dish name">
  <button onclick="getRecipe()">Search</button>

  <div id="result" class="recipe"></div>
</div>

<script>
const recipes = {
  "pasta": {
    ingredients: [
      "200g pasta",
      "2 tomatoes",
      "1 onion",
      "Salt",
      "Olive oil"
    ],
    steps: [
      "Boil pasta",
      "Cook onion and tomatoes",
      "Mix pasta with sauce",
      "Serve hot"
    ],
    time: "20 mins",
    servings: "2"
  },
  "omelette": {
    ingredients: [
      "2 eggs",
      "Salt",
      "Pepper",
      "Oil"
    ],
    steps: [
      "Beat eggs",
      "Heat pan",
      "Pour eggs",
      "Cook both sides"
    ],
    time: "10 mins",
    servings: "1"
  }
};

function getRecipe() {
  const search = document.getElementById("search").value.toLowerCase();
  const result = document.getElementById("result");

  if (recipes[search]) {
    const recipe = recipes[search];
    result.innerHTML = `
      <h3>${search.toUpperCase()}</h3>
      <p><b>Time:</b> ${recipe.time}</p>
      <p><b>Servings:</b> ${recipe.servings}</p>

      <h4>Ingredients:</h4>
      <ul>
        ${recipe.ingredients.map(i => `<li>${i}</li>`).join("")}
      </ul>

      <h4>Steps:</h4>
      <ol>
        ${recipe.steps.map(s => `<li>${s}</li>`).join("")}
      </ol>
    `;
  } else {
    result.innerHTML = "<p>❌ Recipe not found. Try 'pasta' or 'omelette'.</p>";
  }
}
</script>

</body>
</html>
