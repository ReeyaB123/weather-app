<script>
    let weathertemperature = "";
    let location = "";
    let weatherdescription = "";

    async function getWeather() {
    fetch('https://goweather.herokuapp.com/weather/' + location)
      .then((response) => response.json())
      .then((data) => {
        weathertemperature = data.temperature; // Path for temperature
        weatherdescription = data.description; // Path for description
      });
  }
</script>
<h1>Weather App</h1>

<form on:submit|preventDefault={getWeather}>
    <label for="location">Location:</label>
    <input id="location" bind:value={location} type="text" />
    <button type="submit">Check</button>
</form>

<p>Temperature: {weathertemperature}</p>
<p>Description: {weatherdescription}</p>