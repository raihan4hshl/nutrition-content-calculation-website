document.getElementById('compare-btn').addEventListener('click', () => {
    const selectedFoods = Array.from(document.getElementById('food-select').selectedOptions).map(option => option.value);
    const showCalories = document.getElementById('calories').checked;
    const showSugar = document.getElementById('sugar').checked;
    const showCarbs = document.getElementById('carbs').checked;

    fetchNutritionalData(selectedFoods, showCalories, showSugar, showCarbs);
});

function fetchNutritionalData(foods, showCalories, showSugar, showCarbs) {
    // Example nutritional data
    const nutritionalData = {
        rice: { calories: 130, sugar: 0.1, carbs: 28 },
        bread: { calories: 80, sugar: 1.2, carbs: 15 },
        potato: { calories: 77, sugar: 0.8, carbs: 17 }
    };

    const table = document.getElementById('comparison-table');
    table.innerHTML = ''; // Clear previous content

    // Create table headers
    let headers = '<tr><th>Food Item</th>';
    if (showCalories) headers += '<th>Calories</th>';
    if (showSugar) headers += '<th>Sugar</th>';
    if (showCarbs) headers += '<th>Carbohydrates</th>';
    headers += '</tr>';
    table.innerHTML += headers;

    // Populate table rows
    foods.forEach(food => {
        let row = `<tr><td>${food}</td>`;
        if (showCalories) row += `<td>${nutritionalData[food].calories}</td>`;
        if (showSugar) row += `<td>${nutritionalData[food].sugar}</td>`;
        if (showCarbs) row += `<td>${nutritionalData[food].carbs}</td>`;
        row += '</tr>';
        table.innerHTML += row;
    });
}
