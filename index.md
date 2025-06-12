# Welcome to Brewha's Taplist!

<h1>Current Tap List</h1>
<div id="beer-menu" style="display: flex; flex-wrap: wrap; gap: 1em; justify-content: center;"></div>

<script>
const apiUrl = "https://script.google.com/macros/s/AKfycbz7bLjFjF_doYOu-A6SXU98tJpTB8FnC0Pq1oK8vsUuAAUSbFKUkE7hvevyBNTvIgI/exec";

fetch(apiUrl)
  .then(res => res.json())
  .then(beers => {
    const container = document.getElementById("beer-menu")

    beers.forEach(beer => {
      const card = document.createElement("div");
      card.style = `
        background: white;
        border-radius: 10px;
        box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        padding: 1em;
        max-width: 300px;
        flex: 1 1 200px;
        font-family: sans-serif;
      `;

      card.innerHTML = `
        <div style="font-weight: bold; font-size: 1.2em;">${beer.Name}</div>
        <div><strong>Type:</strong> ${beer.Type}</div>
        <div><strong>ABV:</strong> ${beer.ABV }<strong>%</strong></div>
        <div><strong>Brewery:</strong> ${beer.Brewery}</div>
        <div><strong>Location:</strong> ${beer.Location}</div>
      `;

      container.appendChild(card);
    });
  })
  .catch(error => {
    document.getElementById("beer-menu").textContent = "Failed to load beer menu.";
    console.error("Error:", error);
  });
</script>
