# Human Failure Case Analysis

This page provides three representative examples of incorrect human responses for **two-agent** and **three-agent egocentric-motion** questions. These examples were manually inspected in response to reviewer comments regarding whether human failures arise from ambiguous questions or from the difficulty of multi-step spatial reasoning.

Each example contains the original agent views, the task presented to the annotators, the human responses, and a concise explanation of why the correct answer is uniquely determined.

---
# Two Agent Samples

# Example 1

## Agent Views

<p align="center">
  <img src="two_agents/example1/agent1.png" width="31%">
  <img src="two_agents/example1/agent2.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (right)

## Task

**Motion:** Agent 2 moves **backwards**.

**Question:** How should the motion be interpreted in **Agent 1's** local reference frame?

### Choices

- A. North
- B. East
- C. West
- D. South
### Human Response

**Prediction:** South
**Ground Truth:** **South**

## Required Spatial Reasoning

1. Determine Agent 2's approximate orientation relative to Agent 1
2. Interpret Agent 2's backward motion in its local frame
3. Transform this translation into Agent 1's egocentric coordinate system

---

# Example 2

## Agent Views

<p align="center">
  <img src="two_agents/example2/agent1.png" width="31%">
  <img src="two_agents/example2/agent2.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (right)

## Task

**Motion:** Agent 1 turns **45° counterclockwise** and subsequently moves **forward**.

**Question:** How should the latter translational motion be interpreted in **Agent 2's** local reference frame?

### Choices

- A. North
- B. East
- C. West
- D. South
### Human Response

**Prediction:** North
**Ground Truth:** **North**

## Required Spatial Reasoning

1. Determine Agent 2's approximate orientation relative to Agent 1
2. Apply the specified 45° CCW rotation to Agent 1's local coordinate frame
3. Interpret Agent 1's subsequent forward motion in its local frame
4. Transform this translation into Agent 2's egocentric coordinate system

---

# Example 3

## Agent Views

<p align="center">
  <img src="two_agents/example3/agent1.png" width="31%">
  <img src="two_agents/example3/agent2.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (right)

## Task

**Motion:** Agent 2 turns **90° clockwise**

**Question:** After rotating, what direction will Agent 2 be facing towards in Agent 1's local frame?

### Choices

- A. North
- B. East
- C. West
- D. South
### Human Response

**Prediction:** North
**Ground Truth:** **North**

## Required Spatial Reasoning

1. Determine Agent 2's approximate orientation relative to Agent 1
2. Apply the specified 90° CW rotation to Agent 2's local coordinate frame
3. Reinterpret Agent 2's updated local frame with respect to Agent 1's egocentric coordinate system


---
# Three Agent Samples

# Example 1

## Agent Views

<p align="center">
  <img src="three_agents/example1/agent1.png" width="31%">
  <img src="three_agents/example1/agent2.png" width="31%">
  <img src="three_agents/example1/agent3.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (center) &nbsp;&nbsp;&nbsp; **Agent 3** (right)

## Task

**Motion:** Agent 3 turns **90° clockwise** and then **moves to its right**.

**Question:** How should the latter translational motion be interpreted in **Agent 2's** local reference frame?

### Choices

- A. North
- B. East
- C. West
- D. South

### Human Responses

| Annotator | Response |
|-----------|----------|
| Human 1 | South |
| Human 2 | South |
| Human 3 | South |

**Ground Truth:** **East**

## Required Spatial Reasoning

1. Determine Agent 2's approximate orientation relative to Agent 1
2. Determine Agent 3's approximate orientation relative to Agent 1
3. Use the above information to determine Agent 3's approximate orientation relative to Agent 2
4. Apply the specified 90° clockwise rotation to Agent 3's local coordinate frame.
5. Interpret Agent 3's subsequent rightward translation in its updated local frame.
6. Transform this translation into Agent 2's egocentric coordinate system.

---

# Example 2

## Agent Views

<p align="center">
  <img src="three_agents/example2/agent1.png" width="31%">
  <img src="three_agents/example2/agent2.png" width="31%">
  <img src="three_agents/example2/agent3.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (center) &nbsp;&nbsp;&nbsp; **Agent 3** (right)

## Task

**Motion:** Agent 3 moves **backward**.

**Question:** How should this motion be interpreted in **Agent 1's** local reference frame?

### Choices

- A. North
- B. East
- C. West
- D. South

### Human Response

**Prediction:** North

**Ground Truth:** **West**

## Required Spatial Reasoning

1. Determine Agent 3's approximate orientation relative to Agent 2
2. Determine Agent 1's approximate orientation relative to Agent 2
3. Use the above information to determine Agent 3's approximate orientation relative to Agent 1
4. Express Agent 3's backward motion in its own local coordinate system.
5. Transform this motion into Agent 1's egocentric reference frame.

---

# Example 3

## Agent Views

<p align="center">
  <img src="three_agents/example3/agent1.png" width="31%">
  <img src="three_agents/example3/agent2.png" width="31%">
  <img src="three_agents/example3/agent3.png" width="31%">
</p>

**Agent 1** (left) &nbsp;&nbsp;&nbsp; **Agent 2** (center) &nbsp;&nbsp;&nbsp; **Agent 3** (right)

## Task

**Question ID:** 2514

**Motion:** Agent 3 moves **backward**.

**Question:** How should this motion be interpreted in **Agent 2's** local reference frame?

### Choices

- A. North
- B. East
- C. West
- D. South

### Human Response

**Prediction:** South

**Ground Truth:** **East**

## Required Spatial Reasoning

1. Determine Agent 2's approximate orientation relative to Agent 1
2. Determine Agent 3's approximate orientation relative to Agent 1
3. Using the above, determine Agent 2's approximate orientation relative to Agent 3
4. Represent Agent 3's backward motion in its local frame.
5. Transform this motion into Agent 2's egocentric coordinate system.
---

# Summary

These examples were selected because they are representative of the observed human failures on three-agent egocentric-motion questions. In all three cases, the correct answer follows from a deterministic sequence of reference-frame transformations once the relative agent orientations are established. We did not observe evidence that the correct answer depends on subjective interpretation of the scene geometry. Furthermore, each of these examples requires chaining 5 to 6 sequential reasoning operations before the final motion can be expressed in Agent 2's local coordinate system. Although each individual step is uniquely determined by the scene geometry and the specified motion, an error at any intermediate step propagates to the remainder of the reasoning process and substantially increases the likelihood of an incorrect final answer. Consequently, this example presents many more opportunities for error than the corresponding two-agent tasks while remaining fully deterministic and well-defined.

Importantly, these questions admit a systematic solution procedure rather than subjective interpretation. Once the relative orientations of the agents are established from cross-view correspondences, each subsequent coordinate transformation follows deterministically. The primary challenge is therefore not ambiguity in the scene or task specification, but accurately composing multiple egocentric reference-frame transformations whose relationships must first be inferred from the images.
