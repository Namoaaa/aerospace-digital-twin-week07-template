# Week 07 Controls Lab — Responses

Answers and recorded model results from `submission.json`. This document does not recompute or independently validate the results.

## Submission status

- Schema: week07.submission/v1

- Record ID: fbea0a10-541c-4b0c-8458-dfcb8bd6d81f

- Record revision: 6

- Model hash: fnv1a-adee3cf8

- Readiness: Marked incomplete or not ready; missing: verification, claim, reflection, aiUse, execution

## Supplied setup (instructor supplied)

### question — instructor supplied
Calculate required control moment, elevator moment, and the change with airspeed. Explain whether the nominal response meets +0.12 rad/s².

### system — instructor supplied
Illustrative planar pitch model. Aircraft geometry, integration, force conversion and constraints are supplied.

### representation — instructor supplied
Body axes forward/right/down. Positive pitch moment nose-up. Positive Fz downward. Positive elevator trailing edge down. Reference/CG X=0 m; tail X=-3 m.

### inputs — instructor supplied
Iy=5000 kg·m²; target=+0.12 rad/s²; competing=-750 N-m; density=1.225 kg/m³; V=40 m/s; S=16 m²; chord=1.5 m; Cmδ=-0.8/rad; elevator=-5°. Inputs are illustrative, not calibrated.

## Student responses

### physics
**Prompt:** Explain why a downward force aft of the CG gives a positive nose-up moment.

**Student response:**
```
Because the tail is aft of the CG (negative X) and the sign convention makes moment = −X×Fz, a downward force (positive Fz) at a negative X location yields a positive M — i.e., nose-up. Physically it's a seesaw: pushing down on the back end lifts the front end (the nose).
```

### assumptions
**Prompt:** Explain one supplied assumption and what could invalidate it: planar motion, fixed reference, local linear effectiveness, no trim or damping.

**Student response:**
```
the model ignores pitch-rate damping and pre-existing trim, which in reality would oppose the rotation and reduce achieved acceleration below what this simplified balance predicts.
```

### model
**Prompt:** Write your demand, dynamic-pressure, coefficient and moment equations. Identify which quantities are supplied and which are unknown.

**Student response:**
```
Demand: M_control + M_competing = Iy·α_target → solve for M_control (Iy, α_target, M_competing supplied)
Dynamic pressure: q∞ = ½ρV² (ρ, V supplied)
Coefficient: ΔCm = Cmδ·δe, δe in rad (Cmδ, δe supplied)
Moment: M_elevator = q∞·S·chord·ΔCm (S, chord supplied) — computed, then compared to required M_control
```

### prediction
**Prompt:** Before running your own implementation, predict the sign of its elevator moment and the effect of halving airspeed. Explain the competing moment.

**Student response:**
```
Sign of elevator moment: With δe = −5° (negative) and Cmδ = −0.8/rad (negative), ΔCm = Cmδ×δe is positive, so M_elevator is positive (nose-up).

Effect of halving airspeed: M_elevator ∝ q∞ ∝ V², so halving V from 40 to 20 m/s cuts M_elevator to ¼ of its value.

Competing moment: M_competing = −750 N·m is a fixed nose-down disturbance (e.g., from pitching moment about the CG unrelated to the elevator) that the control moment must first cancel before any net nose-up acceleration is achieved.
```

### verification
**Prompt:** Show one independent hand calculation with units. Compare it with your model, and explain a sign, unit, or limiting-case check.

**Student response:**
_Missing — no response supplied._

### claim
**Prompt:** What do your computed results support at the stated condition? Include a limitation.

**Student response:**
_Missing — no response supplied._

### reflection
**Prompt:** What additional evidence or missing physics would you investigate next?

**Student response:**
_Missing — no response supplied._

### AI use
**Prompt:** Identify the AI tool and how you used it, what you changed, and how you independently checked the result. State “No AI used” if applicable.

**Student response:**
_Missing — no response supplied._

## Equations and model source

The recorded model JSON/expression source follows exactly as supplied. It is not interpreted or recomputed here.

```
{
  "schemaVersion": "week07.student-model/v1",
  "id": "week07-student-model",
  "version": "1.0.0",
  "slots": [
    {
      "id": "controls.demand",
      "expressions": [
        {
          "name": "requiredMoment",
          "expression": "",
          "unit": "N*m"
        }
      ]
    },
    {
      "id": "controls.effectiveness",
      "expressions": [
        {
          "name": "dynamicPressure",
          "expression": "",
          "unit": "Pa"
        },
        {
          "name": "deltaCm",
          "expression": "",
          "unit": "1"
        },
        {
          "name": "deltaMoment",
          "expression": "",
          "unit": "N*m"
        }
      ]
    }
  ]
}
```

## Recorded verification status

No verification record was supplied.

## Recorded model runs

_Missing — no model runs supplied._

## Submission instructions

Use Save to GitHub in the app to save both files, commit, and push. Submit your fork URL and the saved commit SHA. Manual fallback: save this file beside `student/submission.json`, run `npm run student:prepare` and `npm run student:validate`, then commit and push student/.
