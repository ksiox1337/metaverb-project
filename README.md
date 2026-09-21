# MetaVerb

<img src="https://github.com/user-attachments/assets/fe1c10ea-381e-44af-a095-70137628da37" alt="MetaVerb learning device showing a multiple-choice exercise" width="450">

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

## App
Web app (PWA) for translating words, saving them into folders and practising them.

<img src="https://github.com/user-attachments/assets/b85fc0bd-8ea3-4063-9104-ab484b9db39c" alt="MetaVerb app — translation screen" width="250"> <img src="https://github.com/user-attachments/assets/3896535d-c210-48b7-bdad-23a0dd5b5350" alt="MetaVerb app — exercise screen" width="250">

## Hardware
A Game Boy-style offline learning device, designed from scratch:
- custom carrier PCB for an ESP32 module (LOLIN32 Lite), designed in EasyEDA
- SPI OLED display, four buttons and a rotary encoder for input
- hardware debouncing on all inputs (10 kΩ pull-up + 100 nF RC filter)
- firmware in ESP-IDF, enclosure designed in Fusion 360

### From sketch to device

<img src="https://github.com/user-attachments/assets/0fec8bd5-e992-4e42-97e2-ee0727cef904" alt="Early design sketch" width="400">

*Early sketch*

<img src="https://github.com/user-attachments/assets/e38023c4-8856-4ce0-95d7-5ab07865e1b0" alt="Enclosure 3D model in Fusion 360" width="600">

*Enclosure — 3D model in Fusion 360*

<img src="https://github.com/user-attachments/assets/73cc12c7-7cbf-4474-b666-9c26b980af34" alt="PCB render" width="400">

*PCB render*

<img src="https://github.com/user-attachments/assets/ae1a99cc-0774-40e0-8cc8-415d0c59c8ce" alt="Assembled PCB" width="350">

*Assembled PCB*

<img src="https://github.com/user-attachments/assets/b0bf1efd-ad80-4880-9139-a065b697e792" alt="Circuit schematic" width="700">

*Schematic*

## My part
Machine learning (all models and the selection logic) and hardware (PCB, firmware, enclosure).
The website and web app were built by my teammate.

## What I learned
The jury's main question was: *what does the ML add over simple rules?*
I couldn't answer it, because measuring that requires real users and data the project didn't have yet.
Since then I start projects with a different question: **how will I measure that my solution is better than what already works?**
