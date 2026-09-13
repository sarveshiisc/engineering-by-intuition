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

## 5. Can We Predict the Future?

We now have a differential equation that describes how the tea temperature changes:

**dT/dt = -k(T - Tₐ)**

The next step is to **solve this equation**.

Solving it gives us a mathematical expression for **T as a function of time t**.

That means we can use it to answer questions like:

- What will the temperature be after 5 minutes?
- After 10 minutes?
- How long will it take to reach a certain temperature?

This is where a differential equation becomes a **prediction tool**.

## 6. Solving the Differential Equation

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
