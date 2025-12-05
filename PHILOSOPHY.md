# The YenBuilds Flight Simming Philosophy  
## Craft Over Engineering. Verisimilitude Over Realism.

The usual dividing line in flight simulation is between the “full-fidelity realists” and the casual hobbyists. Neither group defines what I am building here. The YenBuilds ecosystem is driven by a different principle:

**This is not about engineering precision for its own sake.  
This is about craft — creating a believable aviation experience where every behaviour fits and makes sense.**

Realism is a narrow concept.  
Verisimilitude is broader: the appearance of truth, the sense that the simulated world behaves in a way the real world would, even if the implementation is not identical.

That is the goal.

---

## It Begins With *Why*  
Any simulation project without a clear *why* becomes pointless and rudderless.  
People get lost chasing fidelity for its own sake — perfect procedures, perfect offsets, perfect checklists — without ever asking what experience they’re actually trying to create.

The *why* of YenBuilds is simple:

**To build a flight environment that feels truthful, behaves coherently, and compels disciplined, meaningful flying.**

Without that *why*, the rest collapses into engineering busywork.  
With it, every system has direction and purpose.

---

## What Verisimilitude Means  
Verisimilitude does not require perfect procedures, accurate models of every system, or a full replication of airline SOP.  
It requires coherence.

If something happens in the simulation, your brain should immediately accept it as plausible.  
If you take an action, the aircraft should react in a way that aligns with aviation logic — energy, physics, aerodynamics, workload, state, consequences.

A simulator can fail to be “realistic” yet still be believable.  
It can be “accurate” yet feel lifeless.  
Verisimilitude is the point at which the experience earns your trust.

---

## Craft Over Engineering  
Engineering focuses on precision, specifications, and strict correctness.  
Craft focuses on intent and outcome.

Engineering asks whether the input matches the manual.  
Craft asks whether the aircraft feels alive and reacts meaningfully to what you do.

Every component in this ecosystem — software bridge, hardware interface, throttle system, overlay, scoring logic — is built to serve the experience, not the technical checklist.

The point is not to recreate a type-rating.  
The point is to create a world that behaves as aviation behaves.

---

## The Simulation Should Push Back  
A believable flight simulation needs consequences and state awareness.

Simply the ability for the sim to know when you have:

- landed badly
- exited the runway  
- stalled  
- tail-struck  
- struck an object  
- exceeded limits  
- mishandled energy  
- violated logic or physics

When a simulator cannot recognise these states — when a crash is indistinguishable from a landing, when a tail strike registers as nothing, when the aircraft can be slammed into the ground without acknowledgement — the experience loses tension. It becomes a toy with aircraft-shaped graphics.

Feedback is what gives flying weight.  
A stable approach algorithm should tell you when you were not stable.  
Weather should expose poor judgment.  
Energy mismanagement should feel uncomfortable because the sim recognises it.  
Configurations should matter because the sim cares what you did.

A system without consequences is not a simulator; it is a sandbox.  
Verisimilitude requires the opposite: a machine that responds honestly.

---

## Integrated Systems, Not Independent Widgets  
A throttle is not an isolated lever.  
An LED annunciator is not decoration.  
A HUD overlay is not a gimmick.

Each component is part of one coherent instrumented environment.

The value comes from how these systems interlock:

- hardware mirroring software state  
- telemetry driving overlays  
- overlays informing decision-making  
- scoring engines shaping pilot discipline  
- physics cues, energy cues, and stability cues reinforcing the same narrative

The result is purposeful integration that strengthens the illusion of flight.

---

## Meaningful Difficulty  
Difficulty is only worthwhile if it teaches something about aviation logic.

A challenging approach should feel challenging because the underlying physics demand precision, not because the code is punishing.

Bad weather, unstable energy states, windshear, poor configuration management — these should create friction because they would in real flying.

Difficulty without meaning is noise.  
Difficulty with meaning creates instinct.

---

## Evolution and Compounding  
None of the systems in this repository are static.  
They are designed to evolve, interlock, and compound into a deeper experience over time.

As new modules emerge, they enrich the existing ones:  
more data, clearer cues, tighter feedback, stronger behavioural logic.

The aim is a cockpit that grows in conviction, not complexity.

---

## Closing  
This entire project rests on a single conviction:

**Realism is a checklist.  
Verisimilitude is an experience.  
Craft is the method that creates it.**

Everything in this repository is built around that philosophy.  
If the outcome strengthens the illusion of flying, it belongs here.  
If it adds technical complexity without improving the experience, it does not.

---

*Written with help from ChatGPT.*
