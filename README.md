# Day 26 — Prior Authorization Workflow Simulator

## Task Overview
Built a complete Prior Authorization (PA) Workflow Simulator as a single self-contained HTML/CSS/JS web application. The app walks a randomized patient case through the real-world prior authorization process used in US healthcare — from order to payer decision — including document assembly, submission, and approval/pend/denial/appeal outcomes.

## What Was Built
- **Patient Scenario Generator** — randomly generates a patient with one of 4 real-world procedure types (MRI Lumbar Spine, Physical Therapy, Specialty Drug/Humira, Bariatric Surgery), each with its own payer, diagnosis, and required documentation set.
- **Drag-and-Drop Workflow Stages** — 6-stage kanban-style journey: Order Received → Insurance Verification → Document Collection → PA Submission → Payer Review → Decision. Patient card can be dragged or clicked through stages.
- **Document Assembly Checklist** — each procedure requires a different, realistic set of documents (clinical notes, step therapy proof, psych evals, etc.); submission is blocked until all required documents are checked off.
- **Payer Submission & Review Engine** — completeness-weighted approval probability, with realistic review-day ranges per procedure type.
- **Full Outcome Handling** — Approved, Pended (with resubmission loop), and Denied (with appeal flow that adds review time and improves next-round approval odds).
- **Journey Tracker & Elapsed Days Counter** — live day counter in the header, incremented realistically at each stage transition.
- **Educational Info Boxes** — plain-language explanation of why each stage exists in the real PA process.
- **Workflow Summary Timeline** — full day-by-day case history with a key-takeaway note on what drove the outcome.
- **Restart** — generates a brand-new random patient scenario for repeat practice.

## Tech Stack
- Pure HTML, CSS, and vanilla JavaScript — no external libraries or CDN dependencies.
- Fully client-side; no patient data is real or transmitted anywhere.

## Files in This Folder
- `prior-authorization-workflow-simulator.html` — the complete application
- `day26.md` — this file
- Screenshots of the completed workflow and dashboard/summary

## Key Learnings
- Modeling a real administrative workflow (rather than a game) means the "fun" comes from realism — payer-specific document requirements and review-day ranges needed to feel authentic, not arbitrary.
- A completeness-weighted probability model (not pure randomness) makes the simulator teach the right lesson: missing documents genuinely cause pends/denials, not bad luck.
- Drag-and-drop UX needed a click-to-advance fallback, since not all users (or devices) interact well with native HTML5 drag events.
- Separating "stage advancement" from "decision logic" made it much easier to support loop-back scenarios like pends and appeals without duplicating code.
