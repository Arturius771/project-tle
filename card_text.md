# Ground Station Ops – Prototype Card & Component Text

---

## Shared Deck (TLEs)

| Card Name (TLE)     | Count | Effect                                                                                  | Conditions                                                                                       | Reveal Effect                                                                                    |
| ------------------- | ----- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Solar Charge**    | 4     | +2 Battery (max 5)                                                                      | Must not precede **Downlink**                                                                    | If Battery already at 5 → energy wasted (no effect).                                             |
| **Battery Drain**   | 2     | -1 Battery                                                                              | Must follow a **Command Uplink** or other Command card                                           | If Battery ≤ 1 → Comms go Offline.                                                               |
| **Data Capture**    | 3     | +1 Data Stored (max 3)                                                                  | Requires **Comms Online**; Must be followed within 2 slots by **Downlink**                       | If Comms go Offline before Downlink → all stored Data lost.                                      |
| **Downlink**        | 3     | Send 1 Data to Mission Objective                                                        | Must follow **Data Capture** (within 2 slots); Must not precede **Maneuver Burn**                | If attempted with Comms Offline → wasted slot and Battery -1.                                    |
| **Maneuver Burn**   | 2     | -1 Battery; If Orbit Off-Nominal → restore to Nominal, else counts as Maneuver performed | Must follow **Attitude Change**; Must not precede **Solar Charge**                              | If Battery ≤ 2 → Orbit becomes Off-Nominal (thruster misfire).                                   |
| **Attitude Change** | 2     | Enables **Maneuver Burn** or **Downlink**                                               | Must be followed by **Maneuver Burn** or **Downlink**                                            | If not followed by a valid card → wasted slot.                                                   |
| **Command Uplink**  | 2     | If Comms Offline → Reactivate. If Online → Prep Payload (+1 Data Capture effectiveness) | Requires **Battery ≥ 2**; Must not precede **Maneuver Burn**                                     | If Battery < 2 → Comms go Offline.                                                               |

---

## Role Decks (TLEs)

| Role                      | Card Name (TLE)     | Effect                                                        | Conditions                                                | Reveal Effect                                                                      |
| ------------------------- | ------------------- | ------------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Comms Officer**         | High-Gain Pass      | Downlink 2 Data **per Data Stored**; costs -1 Battery         | Must follow **Data Capture**                              | If Battery ≤ 2 → Comms go Offline.                                                |
| **Power Engineer**        | Battery Recondition | Reset Battery to exactly 3                                    | Must not precede **Maneuver Burn**                        | If Battery is already 3 → discard and draw 1.                                     |
| **Flight Dynamics Officer** | Precision Burn    | Restore Orbit to Nominal without Battery cost                 | Must follow **Attitude Change**                           | If Orbit is already Nominal → wasted slot.                                        |
| **Payload Officer**       | Science Burst       | Capture 2 Data in one slot; costs -1 Battery                  | Requires **Comms Online**; Must be followed within 2 slots by **Downlink** | If Battery ≤ 2 → Payload Glitch (lose 1 Data Stored).                             |

---

## Advanced Role Cards

| Role                      | Card Name (SE)        | Effect                                                                      | Cost / Restriction                                                               | Reveal Effect                                                                   |
| ------------------------- | --------------------- | --------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Comms Officer**         | Ultra-Gain Pass (SE)  | Downlink all Stored Data                                                    | Costs -2 Battery; Must follow **Data Capture**                                   | If Battery ≤ 2 → Comms go Offline.                                              |
| **Power Engineer**        | Battery Boost (SE)    | Set Battery to 5                                                            | Must not precede **Maneuver Burn** or **Solar Charge**                           | If Battery is already 5 → wasted slot.                                          |
| **Flight Dynamics Officer** | Major Correction (SE)| Restore Orbit to Nominal **and** block Orbit Off-Nominal events next round | Costs -1 Battery; Must follow **Attitude Change**                                | If Orbit is already Nominal → wasted slot.                                      |
| **Payload Officer**       | Mega Science Burst(SE)| Capture 3 Data in one slot                                                  | Costs -2 Battery; Requires **Comms Online**; Must be followed by **Downlink**    | If Battery ≤ 2 → Payload Glitch (lose 1 Data Stored).                           |

---

## Mission Objectives

| Mission Objective         | Difficulty | Card Text                                                                        |
| ------------------------- | ---------- | -------------------------------------------------------------------------------- |
| **Quick Science**         | Easy       | Capture and downlink 2 Data **by Orbit 3**                                       |
| **Sustained Ops**         | Easy       | Downlink 2 Data and finish with Battery ≥ 3                                      |
| **Orbit Adjustment**      | Medium     | Perform 1 Maneuver and downlink 2 Data                                           |
| **System Recovery**       | Medium     | Restore Comms from an Offline state at least once, and finish with Orbit Nominal |
| **Full Mission Success**  | Hard       | Downlink 3 Data, perform 1 Maneuver, and finish with Comms Online                |

---

## Scenario Modifiers (Optional)

| Modifier                  | Card Text                                                               |
| ------------------------- | ----------------------------------------------------------------------- |
| **Solar Maximum**         | +1 to all Subsystem Event rolls (2–6 more likely, fewer Nominal passes) |
| **Extra Slot**            | Each orbit has 5 slots instead of 4                                     |
| **Weak Batteries**        | Max Battery is 4 (instead of 5)                                         |
| **Unreliable Comms**      | Add 1 extra Subsystem Event roll each time a Downlink is attempted      |
| **Backup Ground Station** | Ignore the first *Ground Station Conflict* event (slot not blocked)     |

---

## Subsystem Events (d6)

| Roll | Event                   | Effect                               |
| ---- | ----------------------- | ------------------------------------ |
| 1    | Eclipse                 | Battery -1                           |
| 2    | Solar Flare             | Comms Offline next round             |
| 3    | Gyro Drift              | Orbit Off-Nominal                    |
| 4    | Nominal Pass            | No effect                            |
| 5    | Payload Glitch          | Lose 1 Data Stored                   |
| 6    | Ground Station Conflict | Roll 1d4; block that slot next round |

---

## Subsystem Failures

| Subsystem      | Failure Condition                                                     | Notes                                                                                   |
| -------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Battery**    | Battery reaches **0**                                                 | Immediate mission failure (satellite unpowered).                                        |
| **Comms**      | Comms are **Offline at the end of any orbit**                         | Mission failure (permanent loss of contact).                                            |
| **Orbit**      | Orbit remains **Off-Nominal** at end of game if objective requires it | Only matters if the Mission Objective specifies Nominal orbit at mission end.           |
| **Payload**    | Required Data cannot be captured or downlinked to meet objectives     | Not an instant fail; only causes mission failure if the data objective becomes impossible. |

---

## Failure Conditions Summary

| Condition                                              | Effect                                             |
| ------------------------------------------------------ | -------------------------------------------------- |
| **Battery = 0**                                        | Immediate mission failure.                         |
| **Comms Offline at the end of an orbit**               | Mission failure (permanent loss of contact).       |
| **Subsystem Failures ≥ 3**                             | Mission failure (cumulative unrecoverable issues). |
| **Mission Objectives not completed by end of Orbit 5** | Mission failure (mission deadline passed).         |
