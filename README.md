# Ex06 BMI Calculator
## Date: 

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM

```
main.jsx:

import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './BMI'
createRoot(document.getElementById('root')).render(
  <StrictMode>
      <App />
  </StrictMode>,
)
```

```
BMI.jsx:

import React, { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [status, setStatus] = useState("");

  const calculateBMI = () => {
    if (!height || !weight) {
      alert("Please enter both height and weight");
      return;
    }

    const heightInMeters = height / 100;
    const bmiValue = (
      weight /
      (heightInMeters * heightInMeters)
    ).toFixed(2);

    setBmi(bmiValue);

    if (bmiValue < 18.5) {
      setStatus("Underweight");
    } else if (bmiValue < 25) {
      setStatus("Normal Weight");
    } else if (bmiValue < 30) {
      setStatus("Overweight");
    } else {
      setStatus("Obese");
    }
  };

  const resetFields = () => {
    setHeight("");
    setWeight("");
    setBmi(null);
    setStatus("");
  };

  return (
    <div className="container">
      <div className="card">
        <h2>BMI Calculator</h2>

        <input
          type="number"
          placeholder="Enter Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />

        <input
          type="number"
          placeholder="Enter Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />

        <button onClick={calculateBMI}>
          Calculate BMI
        </button>

        <button className="reset" onClick={resetFields}>
          Reset
        </button>

        {bmi && (
          <div className="result">
            <h3>Your BMI: {bmi}</h3>
            <h3>Status: {status}</h3>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
```



## OUTPUT
<img width="1332" height="600" alt="image" src="https://github.com/user-attachments/assets/852e5a28-6259-458b-a576-aa6609c56dbd" />





## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
