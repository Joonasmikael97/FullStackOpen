// Tehtävät 1.12-1.14
import React, { useState } from 'react';

const Anecdote = ({ anecdote, votes, vote, randomAnecdote }) => {
  return (
    <div>
      <h2>Anecdote of the Day</h2>
      <p>{anecdote}</p>
      <p>Has {votes} votes</p>
      <button onClick={vote}>Vote</button>
      <button onClick={randomAnecdote}>Next Anecdote</button>
    </div>
  );
};

const MostVotedAnecdote = ({ anecdotes, votes }) => {
  const mostVotedIndex = votes.indexOf(Math.max(...votes));
  return (
    <div>
      <h2>Most Voted Anecdote</h2>
      <p>{anecdotes[mostVotedIndex]}</p>
      <p>Has {votes[mostVotedIndex]} votes</p>
    </div>
  );
};

const App = () => {
  const anecdotes = [
    'If it hurts, do it more often.',
    'Adding manpower to a late software project makes it later!',
    'The first 90 percent of the code accounts for the first 90 percent of the development time...The remaining 10 percent of the code accounts for the other 90 percent of the development time.',
    'Any fool can write code that a computer can understand. Good programmers write code that humans can understand.',
    'Premature optimization is the root of all evil.',
    'Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.',
    'Programming without an extremely heavy use of console.log is same as if a doctor would refuse to use x-rays or blood tests when diagnosing patients.',
    'The only way to go fast, is to go well.'
  ];

  const initialVotes = Array(anecdotes.length).fill(0);
  const [votes, setVotes] = useState(initialVotes);
  const [selected, setSelected] = useState(0);

  const randomAnecdote = () => {
    setSelected(Math.floor(Math.random() * anecdotes.length));
  };

  const voteAnecdote = () => {
    const newVotes = [...votes];
    newVotes[selected] += 1;
    setVotes(newVotes);
  };

  return (
    <div>
      <Anecdote anecdote={anecdotes[selected]} votes={votes[selected]} vote={voteAnecdote} randomAnecdote={randomAnecdote} />
      <MostVotedAnecdote anecdotes={anecdotes} votes={votes} />
    </div>
  );
};

export default App;
