# Differential Equations — From Reality to Engineering

## Introduction — Change Is Everywhere

Everything around us changes with time — temperature, position, speed, voltage, current, etc.

We are interested not just in **what changes**, but in the **dynamics of how things change with time**.

For example, hot tea cools quickly at first and then gradually slows down as it approaches room temperature. A capacitor charges quickly at first and then more slowly. A drug concentration in the bloodstream gradually decreases after a dose.

**How do we arrive at mathematical equations that can predict, under ideal conditions, exactly how these quantities change as time progresses?**

## 1. Average Rate of Change

Suppose the temperature falls from **80°C to 60°C in 10 minutes**.

The temperature changed by -20°C over 10 minutes, so its average rate of change over this interval is:

**Average rate of change = -20°C / 10 min = -2°C/min**

This tells us the overall rate during those 10 minutes.

## 2. Why Average Rate Isn't Enough

The tea cools faster when it is hot and more slowly as it approaches room temperature.

So, it couldn't have been cooling at exactly **-2°C/min** throughout the entire 10 minutes.

The average rate tells us what happened **over an interval**, but not what was happening **at a particular instant**.

## 3. Instantaneous Rate of Change

What if we want to know:

> **How fast is the temperature changing exactly at 2 minutes?**

We can't calculate a rate over zero time directly. Instead, we calculate the average rate over a smaller and smaller time interval around 2 minutes.

For example:

- From 2 to 3 minutes → average rate
- From 2 to 2.1 minutes → average rate
- From 2 to 2.01 minutes → average rate

As the time interval becomes smaller, the average rate approaches the rate **at exactly 2 minutes**.

Here:

- **T** = temperature of the tea
- **t** = time
- **ΔT** = change in temperature
- **Δt** = change in time

The instantaneous rate is defined as the limiting value:

**Instantaneous rate = lim (Δt → 0) [ΔT / Δt]**

This is the **derivative** of temperature with respect to time:

**dT/dt**

Here, **dT/dt** means the instantaneous rate at which temperature **T** changes with respect to time **t**.

**Average rate → smaller interval → limit → instantaneous rate → derivative**

## 4. From Rate of Change to a Differential Equation

We now have a way to describe how temperature changes at any instant:

**dT/dt** = rate of change of temperature with time.

For hot tea, we observe that the hotter the tea is compared with the room, the faster it cools.

So the rate of cooling depends on the **difference between the tea temperature and the room temperature**.

If the room temperature is **Tₐ**, we can express this relationship as:

**dT/dt = -k(T - Tₐ)**

Here:

- **T** = temperature of the tea at time **t**
- **Tₐ** = room (ambient) temperature
- **k** = a constant that describes how quickly the tea cools

This relationship is known as **Newton's law of cooling**.

This is a **differential equation** because it relates a quantity **T** to its rate of change **dT/dt**.

## 5. What Should the Curve Look Like?

Before solving the equation, can we predict the **nature of the curve**?

We know that the rate of cooling depends on the temperature difference between the tea and its surroundings.

At the beginning, this temperature difference is large.

**Large temperature difference → large rate of cooling**

So the temperature should fall quickly.

As the tea cools, the temperature difference becomes smaller.

**Smaller temperature difference → smaller rate of cooling**

So the temperature should now fall more slowly.

As the tea gets closer and closer to the surrounding temperature, the difference becomes very small.

**Very small temperature difference → very small rate of cooling**

So the curve should gradually flatten as it approaches the surrounding temperature.

Therefore, even without solving the equation, we can predict the **nature of the response**:

**Steep at first → gradually less steep → almost flat near the surrounding temperature**

This does not tell us the exact mathematical shape of the curve. It tells us what kind of behavior we should expect from the physical relationship:

**dT/dt = -k(T - Tₐ)**

Now we can ask a more precise question: **Can we predict the exact temperature at any future time t?**

## 6. Can We Predict the Future?

We now have a differential equation that describes how the tea temperature changes:

**dT/dt = -k(T - Tₐ)**

The next step is to **solve this equation**.

Solving it gives us a mathematical expression for **T as a function of time t**.

That means we can use it to answer questions like:
- What will the temperature be after 5 minutes?
- After 10 minutes?
- How long will it take to reach a certain temperature?

This is where a differential equation becomes a **prediction tool**.

## 7. Solving the Differential Equation

Starting with:

**dT/dt = -k(T - Tₐ)**

First, separate the temperature terms from the time terms:

**dT / (T - Tₐ) = -k dt**

Now integrate both sides:

**ln|T - Tₐ| = -kt + C**

Rearranging and using the initial condition **T(0) = T₀** gives:

**T(t) = Tₐ + (T₀ - Tₐ)e^(-kt)**

where:

- **T(t)** = temperature at time **t**
- **T₀** = initial temperature of the tea
- **Tₐ** = room temperature
- **k** = cooling constant
- **t** = time

Now we have something powerful: **a single equation that predicts the temperature at any future time t.**

For example, if we know the initial temperature, room temperature, and cooling constant, we can calculate the tea's temperature after 5 minutes, 10 minutes, or 30 minutes or at any instant of time.

This is the first payoff of the differential equation: **we started with an observation about how things change and arrived at an equation that can predict their future behavior.**

## 8. What Does Each Term Tell Us?

The equation is:

**T(t) = Tₐ + (T₀ - Tₐ)e^(-kt)**

- **Tₐ — ambient temperature:** the temperature the tea approaches as time becomes very large.
- **T₀ — initial temperature:** the temperature of the tea at `t = 0`.
- **k — cooling constant:** describes how quickly the system responds to the temperature difference.

The value of **k** depends on the physical conditions of the system, such as exposed surface area, container material and shape, air movement, heat-transfer properties, and evaporation.

So **k is not a universal constant**. It represents the combined effect of these physical factors for a particular setup.

## 9. What Does the Equation Tell Us?

The equation gives us more than the temperature at a particular time.

- At **t = 0**, the temperature is **T₀**.
- As **t → ∞**, the temperature approaches **Tₐ**. This is the **steady-state temperature**.
- **k** determines how quickly the temperature approaches the steady state.

Instead of describing the speed of the response using **k**, engineers often use another quantity called the **time constant**, written as **τ**.

**τ = 1/k**

A larger **τ** means a slower response, while a smaller **τ** means a faster response.

After one time constant, the system has completed about **63% of its journey from the initial temperature toward the steady-state temperature**.

This idea of **time constant** appears again and again in engineering — in thermal systems, RC and RL circuits, and first-order control systems.
