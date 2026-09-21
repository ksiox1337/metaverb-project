# MetaVerb

Adaptive vocabulary learning platform — submitted to the **Bundeswettbewerb Künstliche Intelligenz 2025** (team "logosmaschine").

> This repository documents the project. The source code is not public.

## The idea
Most vocabulary apps decide what to review with fixed rules ("five correct answers in a row = learned").
MetaVerb replaces this with ML models that estimate what the learner knows, what they are about to forget, and how engaged they are — and uses these estimates to choose the next word and exercise.

## How it works
Three models feed into the selection:

| Model | Estimates | Approach |
|---|---|---|
| Knowledge tracing | probability the learner knows a word | Deep Knowledge Tracing (LSTM) |
| Forgetting model | when a word will be forgotten | neural spaced-repetition model (FSRS-style) |
| Affective model | engagement / frustration | classifier on interaction features |

Models were trained on open research datasets (incl. EdNet).
Explicit rules sit on top of the model outputs and make the final choice, so the system stays predictable.

## Hardware
A Game Boy-style offline learning device, designed from scratch:
- ESP32-based custom PCB (EasyEDA), firmware in ESP-IDF
- enclosure designed in Fusion 360

![PCB](images/pcb.jpg)
![Device](images/device.jpg)

## My part
Machine learning (all models and the selection logic) and hardware (PCB, firmware, enclosure).
The website and web app were built by my teammate.

## What I learned
The jury's main question was: *what does the ML add over simple rules?*
I couldn't answer it, because measuring that requires real users and data the project didn't have yet.
Since then I start projects with a different question: **how will I measure that my solution is better than what already works?**
