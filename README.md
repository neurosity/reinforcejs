# REINFORCEjs (fork)

**REINFORCEjs** is a Reinforcement Learning library by Andrej Karpathy that implements several common RL algorithms, all with web demos. In particular, the library currently includes:

- **Dynamic Programming** methods
- (Tabular) **Temporal Difference Learning** (SARSA/Q-Learning)
- **Deep Q-Learning** for Q-Learning with function approximation with Neural Networks
- **Stochastic/Deterministic Policy Gradients** and Actor Critic architectures for dealing with continuous action spaces. (_very alpha, likely buggy or at the very least finicky and inconsistent_)

See the [main webpage](http://cs.stanford.edu/people/karpathy/reinforcejs) for many more details, documentation and demos.

> This fork adds node.js and ESM support.

# Getting Started

Install the library as a dependency:

```bash
npm install @neurosity/reinforcejs
```

The library also includes a fork of Andrej's project [recurrentjs](https://github.com/karpathy/recurrentjs) with various utilities for building expression graphs (e.g. LSTMs) and performing automatic backpropagation. Agents for reinforncejs include:

- `DPAgent` for finite state/action spaces with environment dynamics
- `TDAgent` for finite state/action spaces
- `DQNAgent` for continuous state features but discrete actions

A typical usage might look something like:

```javascript
import { DQNAgent } from "@neurosity/reinforcejs";

// create an environment object
const env = {
  getNumStates: () => 8,
  getMaxNumActions: () => 4
};

// create the DQN agent
const spec = { alpha: 0.01 }; // see full options on DQN page
agent = new DQNAgent(env, spec);

setInterval(function () {
  // start the learning loop
  const action = agent.act(s); // s is an array of length 8
  //... execute action in environment and get the reward
  agent.learn(reward); // the agent improves its Q,policy,model, etc. reward is a float
}, 0);
```

The full documentation and demos are on the [main webpage](http://cs.stanford.edu/people/karpathy/reinforcejs).

# License

MIT.
