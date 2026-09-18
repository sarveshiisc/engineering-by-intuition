# Cooling Experiment — Implementation Specification

## 1. Goal

Build a simple interactive experiment that helps the learner discover:

- Smaller `τ` → faster response
- `T₀` → starting temperature
- `Tₐ` → steady-state temperature

Start with **Experiment 1 only**.

## 2. Experiment 1 — Change τ

### Question

**What happens when the time constant changes?**

### Case A
- `T₀ = 80°C`
- `Tₐ = 25°C`
- `τ = 2 min`

### Case B
- `T₀ = 80°C`
- `Tₐ = 25°C`
- `τ = 5 min`

Only `τ` changes.

## 3. Screen Layout

### Desktop

**Left**
- Experiment title
- Short prediction question
- Case A / Case B values
- Run Comparison button

**Right**
- Two tea cups side-by-side
- Thermometers
- Temperature displays
- Elapsed time

**Below**
- Temperature vs time graph

### Mobile

Stack vertically:

1. Experiment title
2. Prediction question
3. Case A / Case B
4. Run button
5. Tea animation
6. Temperature/time
7. Graph

## 4. Prediction

Before running:

> **Which tea do you think will cool faster?**

Options:

- Case A — `τ = 2 min`
- Case B — `τ = 5 min`
- They will cool at the same rate

The learner can select an answer, but **the answer must not block the experiment**.

## 5. Physical Animation

Show two simple cups of tea.

Each cup has:

- thermometer
- current temperature
- small amount of steam

During the experiment:

- temperature decreases continuously
- steam gradually decreases
- thermometer level follows temperature
- elapsed time increases

The animation should be subtle.

**The graph is the main learning visual.**

## 6. Graph

Plot both temperatures on the same graph.

**X-axis:** Time, `t` (min)

**Y-axis:** Temperature, `T` (°C)

Show:

- Case A curve
- Case B curve
- horizontal line at `Tₐ = 25°C`
- current-time marker

The curves should appear progressively as the experiment runs.

The learner should clearly see that Case A approaches room temperature faster.

## 7. Simulation Model

Use the first-order cooling model:

`T(t) = Tₐ + (T₀ - Tₐ)e^(-t/τ)`

For the two cases:

### Case A

`T(t) = 25 + 55e^(-t/2)`

### Case B

`T(t) = 25 + 55e^(-t/5)`

The simulation should:

- start at `80°C`
- approach `25°C`
- never overshoot
- gradually flatten
- run long enough for the difference between the two cases to be obvious

## 8. Run Button

Button text:

**▶ Run Comparison**

When pressed:

1. Reset both experiments.
2. Start both cups at `80°C`.
3. Start the clock.
4. Animate both temperatures.
5. Draw both curves simultaneously.
6. Continue until the curves are sufficiently close to `25°C`.

After completion, show:

> **What did you notice?**

Then:

> **The smaller time constant produced the faster response.**

Do not introduce the mathematical explanation yet.

## 9. Interaction

The learner should be able to:

- run the experiment again
- pause/resume if practical
- reset the experiment

Avoid:

- saving runs
- manually entering data
- complicated controls
- multiple graphs
- unnecessary quizzes

## 10. Visual Principle

The learner should be able to understand the main result **without reading a paragraph**.

They should see:

**smaller `τ` → steeper response → reaches steady state sooner**

## 11. Do Not Add Yet

Do not implement:

- Experiments 2 and 3
- adjustable sliders
- equation display
- differential-equation derivation
- `k = 1/τ` explanation
- advanced graph controls
- accounts
- data storage
- sound
- complex 3D graphics

Keep the first version simple.

## 12. Implementation Constraint

Before modifying anything:

1. Inspect the existing repository structure.
2. Identify the current website framework/components.
3. Reuse the existing styling and architecture.
4. Do not rewrite existing lesson content.
5. Do not introduce a new framework.
6. Keep the simulation component isolated so Experiments 2 and 3 can be added later.

Implement **Experiment 1 only**.

## 13. Success Test

The first prototype is successful if a learner can:

1. Read the question.
2. Make a prediction.
3. Press **Run Comparison**.
4. Watch both cups cool.
5. See both curves on one graph.
6. Immediately recognize that `τ = 2 min` responds faster than `τ = 5 min`.
7. Run it again without confusion.

**Core learning sequence:**

**Predict → Run → Observe → Compare**
