# task-2-bharat-intern
<html lang="en">

<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
	<meta name="theme-color" content="#000000">
	<!--
      manifest.json provides metadata used when your web app is added to the
      homescreen on Android. See https://developers.google.com/web/fundamentals/engage-and-retain/web-app-manifest/
    -->
	<link rel="manifest" href="%PUBLIC_URL%/manifest.json">
	<link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico">
	<!--
      Notice the use of %PUBLIC_URL% in the tags above.
      It will be replaced with the URL of the `public` folder during the build.
      Only files inside the `public` folder can be referenced from the HTML.

      Unlike "/favicon.ico" or "favicon.ico", "%PUBLIC_URL%/favicon.ico" will
      work correctly both with client-side routing and a non-root public URL.
      Learn how to configure a non-root public URL by running `npm run build`.
    -->
	<title>React App</title>
</head>

<body>
	<noscript>
		You need to enable JavaScript to run this app.
	</noscript>
	<div id="root"></div>
	<!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->
</body>

</html>

app.js
import React, { Component, useState } from "react";
import "./styles.css";

const scaleNames = {
  c: "Celsius",
  f: "Fahrenheit"
};

function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <h1>The water would boil</h1>;
  }
  return <h1>The water would not boil</h1>;
}

// change f to c
function toCelsius(fahrenheit) {
  return ((fahrenheit - 32) * 5) / 9;
}

// change c to f
function toFahrenheit(celsius) {
  return (celsius * 9) / 5 + 32;
}

function tryConvert(temperature, convert) {
  const input = parseFloat(temperature);
  if (Number.isNaN(input)) {
    return "";
  }
  const output = convert(input);
  const rounded = Math.round(output * 1000) / 1000;
  return rounded.toString();
}

function App() {
  const [temperature, setTemperature] = useState("");
  const [scale, setScale] = useState("c");

  const handleCelsisusChange = (temperature) => {
    setScale("c");
    setTemperature(temperature);
  };

  const handleFahrenheitChange = (temperature) => {
    console.log("temperature", temperature);

    setScale("f");
    setTemperature(temperature);
  };

  const celsius =
    scale === "f" ? tryConvert(temperature, toCelsius) : temperature;
  const fahrenheit =
    scale === "c" ? tryConvert(temperature, toFahrenheit) : temperature;
  return (
    <div className="App">
      <TemperatureInput
        scale="c"
        temperature={celsius}
        onTemperatureChange={handleCelsisusChange}
      />
      <TemperatureInput
        scale="f"
        temperature={fahrenheit}
        onTemperatureChange={handleFahrenheitChange}
      />
      <BoilingVerdict celsius={parseFloat(temperature)} />
    </div>
  );
}

function TemperatureInput(props) {
  const { scale, temperature, onTemperatureChange } = props;

  const handleChange = (e) => {
    onTemperatureChange(e.target.value);
  };
  return (
    <div>
      <fieldset>
        <h1>Enter temperature in {scaleNames[scale]}:</h1>
        <input type="text" value={temperature} onChange={handleChange} />
      </fieldset>
    </div>
  );
}

export default App;
index.js
import React, { Component, useState } from "react";
import "./styles.css";

const scaleNames = {
  c: "Celsius",
  f: "Fahrenheit"
};

function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <h1>The water would boil</h1>;
  }
  return <h1>The water would not boil</h1>;
}

// change f to c
function toCelsius(fahrenheit) {
  return ((fahrenheit - 32) * 5) / 9;
}

// change c to f
function toFahrenheit(celsius) {
  return (celsius * 9) / 5 + 32;
}

function tryConvert(temperature, convert) {
  const input = parseFloat(temperature);
  if (Number.isNaN(input)) {
    return "";
  }
  const output = convert(input);
  const rounded = Math.round(output * 1000) / 1000;
  return rounded.toString();
}

function App() {
  const [temperature, setTemperature] = useState("");
  const [scale, setScale] = useState("c");

  const handleCelsisusChange = (temperature) => {
    setScale("c");
    setTemperature(temperature);
  };

  const handleFahrenheitChange = (temperature) => {
    console.log("temperature", temperature);

    setScale("f");
    setTemperature(temperature);
  };

  const celsius =
    scale === "f" ? tryConvert(temperature, toCelsius) : temperature;
  const fahrenheit =
    scale === "c" ? tryConvert(temperature, toFahrenheit) : temperature;
  return (
    <div className="App">
      <TemperatureInput
        scale="c"
        temperature={celsius}
        onTemperatureChange={handleCelsisusChange}
      />
      <TemperatureInput
        scale="f"
        temperature={fahrenheit}
        onTemperatureChange={handleFahrenheitChange}
      />
      <BoilingVerdict celsius={parseFloat(temperature)} />
    </div>
  );
}

function TemperatureInput(props) {
  const { scale, temperature, onTemperatureChange } = props;

  const handleChange = (e) => {
    onTemperatureChange(e.target.value);
  };
  return (
    <div>
      <fieldset>
        <h1>Enter temperature in {scaleNames[scale]}:</h1>
        <input type="text" value={temperature} onChange={handleChange} />
      </fieldset>
    </div>
  );
}

export default App;

.App {
  font-family: sans-serif;
  text-align: center;
}

package.son
{
  "name": "convert-temperature-reactjs",
  "version": "1.0.0",
  "description": "",
  "keywords": [],
  "main": "src/index.js",
  "dependencies": {
    "react": "16.12.0",
    "react-dom": "16.12.0",
    "react-scripts": "3.0.1"
  },
  "devDependencies": {
    "typescript": "3.8.3"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "browserslist": [
    ">0.2%",
    "not dead",
    "not ie <= 11",
    "not op_mini all"
  ]
}
