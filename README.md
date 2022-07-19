# API-weather

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>

    <title>Weather API</title>
    <style>
      h1 {
        color: #6443ea;
        font-family: "PT Mono";
        text-align: center;
      }


    </style>
  </head>

  <body>
    <h1>🌤 Weather API</h1>

    <div id="weather" class="weather-temperature"></div>
    <script>
      function displayWeather(response) {
        let weatherDiv = document.querySelector("#weather");
        let temperature = Math.round(response.data.main.temp);
        let description = response.data.weather[0].description;

        weatherDiv.innerHTML = `It is ${temperature} degrees, ${description}, in ${
          response.data.name
        }`;
      }

      let city = "Rome";
      let key = "5f472b7acba333cd8a035ea85a0d4d4c";
      let url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${key}&units=metric`;

      axios.get(url).then(displayWeather);
    </script>
  </body>
