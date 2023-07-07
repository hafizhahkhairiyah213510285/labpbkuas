<template>
    <div class="weather-widget">
      <h2 class="widget-title">Weather Widget</h2>
      <div class="location-input">
        <label for="location">Enter Location:</label>
        <input type="text" id="location" v-model="location" />
        <button @click="fetchWeatherData">Get Weather</button>
      </div>
      <div v-if="weatherData" class="weather-data">
        <p class="location">Location: {{ weatherData.name }}</p>
        <p v-if="weatherData.main" class="temperature">
          Temperature: {{ weatherData.main.temp }}°C
        </p>
        <p v-if="weatherData.weather" class="description">
          Description: {{ weatherData.weather[0].description }}
        </p>
      </div>
      <p v-else>Loading weather data...</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        location: '',
        weatherData: null
      };
    },
    methods: {
      async fetchWeatherData() {
        try {
          const apiKey = 'b7bfca7b27a3485144fea086c50d09dc';
          const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${apiKey}`;
          const response = await fetch(apiUrl);
          const data = await response.json();
          this.weatherData = data;
        } catch (error) {
          console.error('Error fetching weather data:', error);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .weather-widget {
    border: 2px solid #3498db;
    padding: 20px;
    margin-bottom: 20px;
    text-align: center;
    background-color: #2980b9;
    font-family: 'Segoe UI', Arial, sans-serif;
    color: white;
  }
  
  .widget-title {
    margin-top: 0;
    color: #ecf0f1;
  }
  
  .location-input {
    margin-bottom: 10px;
  }
  
  .location-input label {
    font-weight: bold;
  }
  
  .location-input input[type="text"] {
    padding: 5px;
    border: 1px solid #bdc3c7;
    border-radius: 3px;
  }
  
  .location-input button {
    padding: 5px 10px;
    margin-left: 10px;
    background-color: #2ecc71;
    border: none;
    color: white;
    cursor: pointer;
    border-radius: 3px;
  }
  
  .weather-data {
    margin-top: 20px;
  }
  
  .location {
    font-size: 18px;
    font-weight: bold;
  }
  
  .temperature {
    font-size: 24px;
    color: #f39c12;
  }
  
  .description {
    font-size: 16px;
  }
  
  .loading-message {
    font-style: italic;
  }
  </style>
  