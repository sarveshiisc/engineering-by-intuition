# Cooling Experiment — Implementation Specification

## 1. Goal

Build a simple interactive experiment that helps the learner discover:

- Smaller `τ` → faster response
- `T₀` → starting temperature
- `Tₐ` → steady-state temperature

The Cooling Lab contains three guided experiments followed by an Explore Yourself mode. Each guided experiment isolates one parameter while the other parameters stay fixed. The guided experiments use the predict -> run -> observe -> compare learning cycle; Explore Yourself is free investigation without prediction feedback.

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

## 12. Experiment 2 — Change `T₀`

### Question

**What happens when the starting temperature changes?**

### Case A
- `T₀ = 80°C`
- `Tₐ = 25°C`
- `τ = 3 min`

### Case B
- `T₀ = 50°C`
- `Tₐ = 25°C`
- `τ = 3 min`

Only `T₀` changes. The two cases have the same ambient temperature and the same time constant.

### Prediction

Before running:

> **Which tea will be hotter after a few minutes?**

Options:

- Case A — `T₀ = 80°C`
- Case B — `T₀ = 50°C`
- They will cool to the same temperature

The learner can select an answer, but the answer must not block the experiment.

### Physical Animation

Show two tea cups using the same visual language as Experiment 1. During the experiment:

- Case A starts at `80°C`
- Case B starts at `50°C`
- temperature decreases continuously
- steam gradually decreases
- thermometer level follows temperature
- elapsed time increases

The animation should be subtle. The graph is the main learning visual.

### Graph

Plot both temperatures on the same graph.

**X-axis:** Time, `t` (min)

**Y-axis:** Temperature, `T` (°C)

Show:

- Case A curve
- Case B curve
- horizontal line at `Tₐ = 25°C`
- current-time marker

The curves should appear progressively as the experiment runs. The learner should clearly see that different starting temperatures change the starting point and the path, but both cases approach the same steady-state temperature.

### Simulation Model

Use the first-order cooling model:

`T(t) = Tₐ + (T₀ - Tₐ)e^(-t/τ)`

For the two cases:

### Case A

`T(t) = 25 + 55e^(-t/3)`

### Case B

`T(t) = 25 + 25e^(-t/3)`

The simulation should:

- start Case A at `80°C` and Case B at `50°C`
- approach `25°C` in both cases
- never overshoot the ambient temperature
- gradually flatten
- run long enough for the different starting responses to clearly converge toward the same steady-state temperature

### Run Button

Button text:

**▶ Run Starting Temperature Comparison**

When pressed:

1. Reset both experiments.
2. Start Case A at `80°C` and Case B at `50°C`.
3. Start the clock.
4. Animate both temperatures.
5. Draw both curves simultaneously.
6. Continue until both curves are sufficiently close to `25°C`.

After completion, show:

> **What did you notice?**

Then:

> **The starting temperature changes the starting point, not the steady-state temperature.**

Do not introduce the mathematical explanation yet.

### Interaction

The learner should be able to:

- run the experiment again
- pause/resume if practical
- reset the experiment

Do not add adjustable sliders, manual data entry, multiple graphs, or a quiz beyond the prediction.

### Success Test

The second prototype is successful if a learner can:

1. Read the question.
2. Make a prediction.
3. Press **Run Starting Temperature Comparison**.
4. Watch both cups cool.
5. See both curves and the shared ambient line on one graph.
6. Recognize that different starting temperatures still approach the same steady-state temperature.
7. Run it again without confusion.

## 13. Experiment 3 — Change `Tₐ`

### Learning Objective

**Changing the ambient temperature `Tₐ` changes the steady-state temperature that the tea approaches.**

### Question

**What do you think will happen to the two teas?**

### Case A
- `T₀ = 80°C`
- `Tₐ = 20°C`
- `τ = 3 min`

### Case B
- `T₀ = 80°C`
- `Tₐ = 30°C`
- `τ = 3 min`

Only `Tₐ` changes.

### Prediction

Options:

- They approach different final temperatures
- They eventually reach the same temperature
- They cool at completely different response speeds

Do not reveal the answer before the experiment runs. The prediction must not block the experiment.

### Simulation

Both teas start at `80°C`, have the same `τ = 3 min`, cool simultaneously, and approach their respective ambient temperatures. Reuse the Cooling Lab cup, thermometer, steam, timing, pause, resume, reset, and feedback behavior.

### Graph

Plot both temperatures on one progressively drawn graph with a current-time marker. Show two clearly labeled horizontal ambient/steady-state reference lines:

- Case A: `Tₐ = 20°C`
- Case B: `Tₐ = 30°C`

Do not show a single ambient-temperature line for this experiment.

### Simulation Model

`T(t) = Tₐ + (T₀ - Tₐ)e^(-t/τ)`

Case A:

`T(t) = 20 + 60e^(-t/3)`

Case B:

`T(t) = 30 + 50e^(-t/3)`

### Run Button

Button text:

**▶ Run Ambient Comparison**

After the experiment finishes, evaluate the learner's prediction using the existing feedback behavior. Keep the final observation short:

> **Different ambient temperatures → different steady-state temperatures.**

### Success Test

The learner can read the question, make a prediction, run both teas, see the two distinct steady-state levels, understand the result, and run the experiment again without confusion.

## 14. Explore Yourself

Explore Yourself is available alongside the three guided experiments after the learner has completed or explored them.

### Purpose

Explore Yourself is a free comparison laboratory. Let the learner configure two cooling systems and independently discover how the curves change. There is no correct answer or quiz in this mode.

### Controls

Provide exactly three sliders for each system, System A and System B, with their current numerical values displayed beside them:

- Initial temperature `T₀`: `30–100°C`
- Ambient temperature `Tₐ`: `10–40°C`
- Time constant `τ`: `1–10 min`

Use these suggested starting values:

System A: `T₀ = 80°C`, `Tₐ = 25°C`, `τ = 2 min`

System B: `T₀ = 80°C`, `Tₐ = 25°C`, `τ = 5 min`

Enforce `T₀ > Tₐ` independently for both systems. Invalid combinations must be handled clearly without breaking the simulation.

Include a **Copy A → B** button that copies all three System A parameters to System B.

### Display

Show:

- two tea cups labeled System A and System B
- one thermometer for each cup
- live temperature for each system
- elapsed time
- one shared temperature-vs-time graph with two curves
- clear System A/System B curve identification
- one or two ambient-temperature reference lines as needed
- Run Comparison and Reset controls

The graph and animation use:

`T(t) = Tₐ + (T₀ - Tₐ)e^(-t/τ)`

The graph should use the same axes for both systems and update when a slider changes. Running starts both clocks together and animates both teas; resetting returns elapsed time to zero and uses the current slider values. Display the current numerical value next to every slider. If ambient temperatures differ, show both steady-state reference levels clearly.

The learner workflow is:

**Change → Observe → Compare**

At the bottom of the mode, show:

> **Try changing one parameter at a time. What changes in the graph?**

Do not show a prediction quiz or correct/incorrect feedback in this mode. Keep the existing visual design and reuse the shared simulation code rather than duplicating the simulation engine.

## 15. Do Not Add Yet

Do not implement:

- additional experiments
- sliders for parameters other than `T₀`, `Tₐ`, and `τ` in Explore Yourself
- equation display
- differential-equation derivation
- `k = 1/τ` explanation
- advanced graph controls
- accounts
- data storage
- sound
- complex 3D graphics

Keep the first version simple.

## 16. Navigation and Implementation Constraint

Before modifying anything:

1. Inspect the existing repository structure.
2. Identify the current website framework/components.
3. Reuse the existing styling and architecture.
4. Do not rewrite existing lesson content.
5. Do not introduce a new framework.
6. Keep the simulation configurable so all three experiments and Explore Yourself use one simulation component.

The Cooling Lab must allow switching between:

- Experiment 1 — Change `τ`
- Experiment 2 — Change `T₀`
- Experiment 3 — Change `Tₐ`
- Explore Yourself

Switching modes resets the simulation and loads the appropriate parameters, graph, prediction question, and feedback. Explore Yourself loads two slider groups instead of a prediction question and feedback. Do not add equations, libraries, additional experiments, or unrelated features.

## 17. Success Tests

The Cooling Lab is successful if a learner can:

1. Run Experiment 1 and recognize that `τ = 2 min` responds faster than `τ = 5 min`.
2. Run Experiment 2 and recognize that different `T₀` values change the starting point while both cases approach `Tₐ = 25°C`.
3. Run Experiment 3 and recognize that different `Tₐ` values create different steady-state temperatures.
4. Receive meaningful feedback after making a prediction in every experiment.
5. Switch experiments and see the simulation, graph, prediction, and feedback reset to the selected experiment.
6. Run each experiment again without confusion.
7. Use Explore Yourself to change each of `T₀`, `Tₐ`, and `τ`, and see the curve update according to the cooling model while `T₀ > Tₐ` remains enforced.

**Core learning sequence:**

**Predict → Run → Observe → Compare**
