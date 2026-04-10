[[AI]]



---

# Intelligent Agents

**Course:** CS361 Artificial Intelligence
**Instructor:** Dr. Khaled Wassif
**Textbook:** *Artificial Intelligence: A Modern Approach*

---

## 🧠 Big AI Picture

AI studies **agents** that:

1. **Sense** the environment
2. **Reason** about it
3. **Act** on it
4. **Receive feedback**
5. **Learn**

> AI focuses on designing rational agents that perceive, think, and act effectively.

---

# 1️⃣ Agents and Environments

## 🔹 Agent Definition

An **agent** is anything that:

* **Perceives** through **sensors**
* **Acts** through **actuators**

### Examples

* **Human agent**

  * Sensors: eyes, ears
  * Actuators: hands, legs, mouth
* **Robot agent**

  * Sensors: cameras, infrared
  * Actuators: motors
* **Software agent**

  * Inputs: keystrokes, files, packets
  * Outputs: display, file writing, network messages

---

## 🔹 Agent Function

Mathematically:

```
f: P* → A
```

Maps:

* Percept history → Action

Implementation:

```
Agent = Architecture + Program
```

---

## 🔹 Example: Vacuum Cleaner World

* **Environment:** Two squares (A, B)
* **Percepts:** Location + Dirt status
* **Actions:** Left, Right, Suck, NoOp
* **Rule:**

  * If Dirty → Suck
  * Else → Move

---

# 2️⃣ Rational Agents

## 🔹 What is Rationality?

A **rational agent**:

> Selects the action that maximizes expected performance given:

* Performance measure
* Prior knowledge
* Available actions
* Percept sequence

### Important:

* Rational ≠ Successful
* Rational ≠ Omniscient
* Rational ≠ Perfect

---

## 🔹 Performance Measure

Defines **success criteria**

Examples:

* Dirt cleaned
* Time taken
* Energy used
* Profit
* Safety

Evaluation timing matters:

* After one attempt?
* After N attempts?
* Average over time?

---

# 3️⃣ PEAS: Task Environment Specification

PEAS stands for:

| Component | Meaning             |
| --------- | ------------------- |
| P         | Performance Measure |
| E         | Environment         |
| A         | Actuators           |
| S         | Sensors             |

---

## 🔹 Example: Taxi Driver

* **P:** Safe, fast, legal, comfortable, profitable
* **E:** Roads, traffic, pedestrians
* **A:** Steering, brake, accelerator, horn
* **S:** Cameras, GPS, speedometer

---

## 🔹 Example: Medical Diagnosis System

* **P:** Healthy patient, minimal cost
* **E:** Patient, hospital
* **A:** Display diagnosis
* **S:** Symptoms input

---

## 🔹 Example: Part-Picking Robot

* **P:** Correct bin percentage
* **E:** Conveyor belt
* **A:** Robot arm
* **S:** Camera, joint sensors

---

# 4️⃣ Properties of Task Environments

Environment classification dimensions:

---

## 1️⃣ Observable

* **Fully observable**
* **Partially observable**
* **Unobservable**

---

## 2️⃣ Agents

* **Single-agent**
* **Multi-agent**

  * Competitive (Chess)
  * Cooperative (Taxi driving)

---

## 3️⃣ Determinism

* **Deterministic**
* **Stochastic**
* **Strategic** (multi-agent deterministic)

---

## 4️⃣ Episodic vs Sequential

* **Episodic:** Independent decisions
* **Sequential:** Current action affects future

---

## 5️⃣ Static vs Dynamic

* **Static:** No change during thinking
* **Dynamic:** Changes during deliberation
* **Semidynamic:** State fixed but performance changes

---

## 6️⃣ Discrete vs Continuous

* **Discrete:** Finite states/actions (Chess)
* **Continuous:** Real values (Taxi driving)

---

## 7️⃣ Known vs Unknown

* **Known:** Rules available
* **Unknown:** Must learn environment

---

### 🔥 Hardest Environment Type

Partially observable
Multi-agent
Stochastic
Sequential
Dynamic
Continuous
Unknown

---

# 5️⃣ Structure of Agents

```
Agent = Architecture + Program
```

Architecture:

* Receives percepts
* Runs program
* Executes actions

---

## 🦴 Skeleton Agent Structure

Steps:

1. Update memory with percept
2. Choose best action
3. Store action in memory

Memory persists across time.

---

# 6️⃣ Table-Driven Agent

Stores:

* Entire percept history
* Lookup table of actions

### ❌ Problems:

1. Huge table size (e.g., chess ≈ 10^120 states)
2. Hard to design
3. No autonomy
4. Cannot adapt easily

---

# 7️⃣ Types of Agent Programs

---

## 1️⃣ Simple Reflex Agent

* Uses **condition-action rules**
* Based only on **current percept**
* No memory

✔ Works only in fully observable environments
❌ Fails in partial observability

---

## 2️⃣ Model-Based Reflex Agent

* Maintains **internal state**
* Uses a **model of the world**

  * How world evolves
  * How actions affect world

Handles **partial observability**

---

## 3️⃣ Goal-Based Agent

* Has explicit **goals**
* Uses search & planning
* Considers future consequences

More flexible than reflex agents.

---

## 4️⃣ Utility-Based Agent

Uses a **utility function** to:

* Compare different states
* Handle conflicting goals
* Handle uncertainty

Chooses action that maximizes:

```
Expected Utility
```

Best for:

* Trade-offs
* Risk handling
* Uncertain outcomes

---

# 8️⃣ Learning Agents

All agents can improve through:

* Experience
* Feedback
* Adaptation

Autonomy increases with learning.

---

# 📌 Key Takeaways

* Agents perceive → reason → act
* Rationality = maximizing expected performance
* PEAS defines task environment
* Environment properties determine design
* Four main agent types:

  * Simple reflex
  * Model-based
  * Goal-based
  * Utility-based
* Learning enhances performance

---

# 🏷️ Tags


#AI
#ArtificialIntelligence
#IntelligentAgents
#RationalAgents
#PEAS
#AgentArchitecture
#EnvironmentProperties
#Search
#Planning
#UtilityTheory
#LearningAgents
#CS361


---
