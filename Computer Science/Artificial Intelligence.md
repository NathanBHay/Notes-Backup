Artificial Intelligence (**AI**) is the idea of creating intelligent agents that are able to make decisions based on the conditions they are able to observe. 

**Rationality** is one aspect AI researchers look to when creating agents that are able to navigate scenarios. A rational agent is able to maximise the benefit to themselves given observable information. This rationality can be bounded by [[CPU]] time, [[Memory|memory]], or aspects of the simulation.

An **agent** is anything that can be viewed as perceiving its environment, and acting its conditions. This is done through its **percepts** which observe the environment and keep a history, with it interacting with the environment through **actions**. More, formally the *agent function* $f$ maps from its *perceived histories* $\mathcal{P}^*$ to actions $\mathcal{A}$ with the *agent program*:
$$f:\mathcal{P}^*\to\mathcal{A}$$
This is usually subject to a **performance measure** (or objective function) that quantifiers the success of actions.

# Environment Types
There are various aspects of the environments in which an AI agent inhabits. These include:
- **Fully observable** where the agent knows all information or **partially observable** where only some is known.
- **Single-agent** only has one while **multi** will have multiple.
- **Dynamic** where the environment changes or **static** where is doesn't.
- **Episodic** where actions are made independent of each other, while **sequential** where has actions made of the consequence of the others.
- **Known** where the rules of how the environment functions are known with the inverse being **unknown**.

Depending on the environment we have different approaches to solving our decision

| **[[Searching Algorithms]]** | **[[Markov Chain#Markov Decision Process\|Markov Decision Process]]** | **[[Reinforcement Learning]]** |
| ---------------------------- | --------------------------------------------------------------------- | ------------------------------ |
| Fully Observable             | Fully Observable                                                      | Partially Observable           |
| Known                        | Known                                                                 | Initially Unknown              |
| Determenistic                | Stochastic                                                            | Stochastic                     |
