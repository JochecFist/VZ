# Machine Learning for the Adaptation of Autonomous Agents

**English** | [Česky](README.cs.md)

Research task (výzkumný úkol), Faculty of Nuclear Sciences and Physical Engineering,
CTU in Prague, 2024. Department of Software Engineering.
Supervisor: Ing. Josef Nový, Ph.D.

CZ: *Strojové učení pro adaptaci autonomních agentů*

---

## What this is

A survey and design document: the groundwork for building a game AI opponent that adapts to the
player in real time instead of running a fixed behaviour tree. It reviews how game AI is
actually built in shipped titles, works through the machine learning options, and then proposes
a concrete agent architecture and a way to evaluate it.

This is the precursor to my [master's thesis](../../DP), which implemented the agent.

## Contents

**1. AI in games.** History from Turing's Minimax chess adaptation through Chinook, Deep Blue,
TD-Gammon and AlphaGo, then the techniques the industry actually ships: finite state machines,
behaviour trees, and utility system AI, with their respective trade-offs. Two case studies of
3D action games with unusually capable AI: F.E.A.R.'s goal-oriented action planning (a
descendant of STRIPS, where each action carries preconditions and effects), and the Nemesis
system from *Middle-Earth: Shadow of Mordor* and *Shadow of War*.

**2. Machine learning.** The four paradigms with representative algorithms for each: supervised
(support vector machines, decision trees), unsupervised (k-means, hierarchical clustering,
Apriori and GSP for frequent pattern mining), semi-supervised (generative adversarial networks),
and reinforcement learning.

**3. Agent design.** The proposed environment, built as a first-person shooter in Unreal Engine,
and a two-part agent: SARSA for choosing soldier equipment, on the grounds that it is a small
controlled space where nothing changes randomly, and Deep Q-Learning for battlefield
decision-making, where the state space is large and continuously shifting.

**4. Evaluation design.** Three ways to score the agent, each predicted to push it toward a
different strategy: kill efficiency (fast, fragile, aggressive soldiers, or one heavily armoured
immobile one), survival efficiency (armour-heavy, or a mobile long-range sniper), and a
combination of both.

## How this turned out

Worth stating plainly, because the follow-up work changed direction: **the implemented agent
does not use SARSA or Deep Q-Learning.** The master's thesis built it on Proximal Policy
Optimization instead.

The reason was practical. Implementation used the NevarokML plugin, which bridges Unreal Engine
to Stable-Baselines3, and within the algorithms it exposes, PPO turned out to be the better
compromise between training stability, implementation complexity and usability in a
non-stationary environment with a discrete action space. The split-brain design proposed here —
one algorithm for equipment, another for combat — was replaced by a single multi-head policy
handling movement, rotation, firing and equipment choice together.

The evaluation framing from part 4 did survive into the implementation, in the form of the
reward function, which balances aim accuracy, distance keeping and successful elimination.

## Repository contents

LaTeX source and the compiled text.

## Citation

```
JOCHEC, Martin. Strojové učení pro adaptaci autonomních agentů.
Výzkumný úkol. Praha: ČVUT, Fakulta jaderná a fyzikálně inženýrská, 2024.
Vedoucí práce Ing. Josef Nový, Ph.D.
```
