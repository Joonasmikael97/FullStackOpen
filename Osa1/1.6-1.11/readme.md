// tehtävät 1.6-1.11
import React, { useState } from 'react';


const Button = ({ handleClick, text}) => (
  <button onClick={handleClick}>{text}</button>
);

const StatisticLine = ({ text, value}) => (
  <p>
    {text}: {value}
  </p>
);

const Statistics = ({good, neutral, bad}) => { 
  const total = good + neutral + bad;

  if (total == 0) {
    return <p>No Feedback</p>
  }
  const average = total ? (good - bad) / total : 0;
  const positivePercentage = total ? (good / total) * 100 : 0;

  return (
    <div>
      <StatisticLine text="Good" value={good} />
      <StatisticLine text="Neutral" value={neutral} />
      <StatisticLine text="Bad" value={bad} />
      <StatisticLine text="Total" value={total} />
      <StatisticLine text="Average" value={average.toFixed(1)} />
      <StatisticLine text="Positive Percentage" value={`${positivePercentage.toFixed(1)}%`} />
    </div>
  );
}



const App = () => {
  const [good, setGood] = useState(0);
  const [neutral, setNeutral] = useState(0);
  const [bad, setBad] = useState(0);

  const increaseGood = () => setGood(good + 1);
  const increaseNeutral = () => setNeutral(neutral + 1);
  const increaseBad = () => setBad(bad + 1);

  return (
    <div>
      <h1>Give Feedback</h1>
      <button onClick={increaseGood}>Good</button>
      <button onClick={increaseNeutral}>Neutral</button>
      <button onClick={increaseBad}>Bad</button>
      <h2>Statistics</h2>
      <Statistics good={good} neutral={neutral} bad={bad} />
    </div>
  );
};

export default App;