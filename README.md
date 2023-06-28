# Temperature-Converter
	<!DOCTYPE html>
<html>
<head>
  <title>Temperature Converter</title>
  <style>
    /* CSS code */
    body {
      background: url(weather.jpg) right;
      color: #fff;
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    
    h1 {
      background: url(summer.jpg) right;
      width: 1080px;
      padding: 20px;
      text-align: center;
    }
    
    .converter-container {
      width: 300px;
      margin: 0 auto;
      padding: 20px;
      background-color:  #301934;
      border-radius: 5px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
    
    .form-group {
      margin-bottom: 20px;
    }
    
    .form-group label {
      font-weight: bold;
      display: block;
    }
    
    .form-group input[type="text"] {
      width: 100%;
      padding: 5px;
    }
    
    .convert-button {
      padding: 8px 16px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 3px;
      cursor: pointer;
      width: 100%;
    }
    
    .result {
      margin-top: 20px;
      font-weight: bold;
      text-align: center;
    }
    
    .state-info {
      font-weight: normal;
      font-style: italic;
      text-align: center;
      margin-top: 10px;
    }
  </style>
  <script>
    function convertTemperature() {
      var temperature = parseFloat(document.getElementById("temperature").value);
      var unit = document.getElementById("unit").value;

      if (isNaN(temperature)) {
        document.getElementById("result").innerHTML = "Please enter a valid temperature.";
        document.getElementById("state-info").innerHTML = "";
        return;
      }

      var convertedTemperature;
      var convertedUnit;
      var stateInfo;

      if (unit === "celsius") {
        convertedTemperature = (temperature * 9/5) + 32;
        convertedUnit = "°F";
        stateInfo = "From Celsius to Fahrenheit";
      } else if (unit === "fahrenheit") {
        convertedTemperature = (temperature - 32) * 5/9;
        convertedUnit = "°C";
        stateInfo = "From Fahrenheit to Celsius";
      } else if (unit === "kelvin") {
        convertedTemperature = temperature + 273.15;
        convertedUnit = "K";
        stateInfo = "From Celsius to Kelvin";
      }

      document.getElementById("result").innerHTML = convertedTemperature.toFixed(2) + convertedUnit;
      document.getElementById("state-info").innerHTML = stateInfo;
    }
  </script>
</head>
<body>
  <h1>Temperature Converter</h1>
  
  <div class="converter-container">
    <div class="form-group">
      <label for="temperature">Temperature:</label>
      <input type="text" id="temperature" placeholder="Enter temperature">
    </div>
    
    <div class="form-group">
      <label for="unit">Unit:</label>
      <select id="unit">
        <option value="celsius">Celsius (C°)</option>
        <option value="fahrenheit">Fahrenheit (F°)</option>
        <option value="kelvin">Kelvin (K)</option>
      </select>
    </div>
    
    <button class="convert-button" onclick="convertTemperature()">Convert</button>
    
    <div class="result" id="result"></div>
    
    <div class="state-info" id="state-info"></div>
  </div>
</body>
</html>
