

# Multi-Objective Reinforement Learning

slide: https://hackmd.io/@9KCqffEFR4C4AfiS32x7EQ/r1MKItbCI

---
## RL problem

- The learning agent is not provided explicitly what action to take
- The learning agent determines the best action to maximize long-term rewards and execute it
- The selected action makes the current state of the environment to transit into its successive state
- The agent receives a scalar reward signal that evaluates the effect of this state transition
- The agent learns optimal or near-optimal action policies from such interactions in order to maximize some notion of long-term objectives

![](https://i.imgur.com/fNXVuXZ.png)

---
### Challenges of RL

Despite of many advances in RL theory and algorithms, one remained challenge is to scale up to larger and more complex problems. 
The scaling problem for sequential decision-making mainly includes the following aspects:

1. Large or continuous state or action space
1. Hierarchically organized tasks and sub-tasks
1. To solve several tasks with different rewards simultaneously
> Multi-objective reinforcement learning (MORL) problem

---

### Multi-Objective Reinforcement Learning (MORL)

A combination of multi-objective optimization (MOO) and RL techniques to solve the sequential decision-making problems with multiple conflicting objectives

1. Obtain action policies which optimizes two or more objectives at the same time
1. Each objective has its own associated reward signal
1. The reward is not a scalar value but a vector
1. Combine the objectives if they are related
1. Optimize the objectives separately if they are completely unrelated
1. Make a trade-off among the conflicting objectives

---



---

### Architecture of extension

---

![](https://i.imgur.com/ij69tPh.png)

---

## Content script

- Bind with each page
- Manipulate DOM
- Add event listeners
- Isolated JavaScript environment
  - It doesn't break things

---

# :fork_and_knife: 

---

<style>
code.blue {
  color: #337AB7 !important;
}
code.orange {
  color: #F7A004 !important;
}
</style>

- <code class="orange">onMessage('event')</code>: Register event listener
- <code class="blue">sendMessage('event')</code>: Trigger event

---

# :bulb: 

---

- Dead simple API
- Only cares about application logic

---

```typescript
import * as Channeru from 'channeru'

// setup channel in different page environment, once
const channel = Channeru.create()
```

---

```typescript
// in background script
const fakeLogin = async () => true

channel.answer('isLogin', async () => {
  return await fakeLogin()
})
```

<br>

```typescript
// in inject script
const isLogin = await channel.callBackground('isLogin')
console.log(isLogin) //-> true
```

---

# :100: :muscle: :tada:

---

### Wrap up

- Cross envornment commnication
- A small library to solve messaging pain
- TypeScript Rocks :tada: 

---

### Thank you! :sheep: 

You can find me on

- GitHub
- Twitter
- or email me
