# Ground Station Ops – Prototype Card & Component Text

---

## Shared Deck (TLEs)

| Card Name (TLE)     | Count | Effect                                                                                  | Requirements                                                                                  |
| ------------------- | ----- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Solar Charge**    | 4     | +2 Battery (max 5)                                                                      | Cannot be followed by **Downlink** (charging delay)                                           |
| **Battery Drain**   | 2     | -1 Battery                                                                              | Follows a **Command Uplink** or other Command card                                            |
| **Data Capture**    | 3     | +1 Data Stored (max 3)                                                                  | Requires **Comms Online**; Requires **Downlink** within 2 slots or data is lost               |
| **Downlink**        | 3     | Send 1 Data to Mission Objective                                                        | Follows **Data Capture** (within 2 slots); Cannot be followed by **Maneuver Burn**            |
| **Maneuver Burn**   | 2     | -1 Battery; If Orbit Off-Nominal → restore to Nominal, else counts as Maneuver performed | Requires **Attitude Change**; Cannot be followed by **Solar Charge**                          |
| **Attitude Change** | 2     | Enables **Maneuver Burn** or **Downlink**                                               | Requires follow-up with **Maneuver Burn** or **Downlink**                                     |
| **Command Uplink**  | 2     | If Comms Offline → Reactivate. If Online → Prep Payload (+1 Data Capture effectiveness) | Requires **Battery ≥ 2**; Cannot be followed by **Maneuver Burn**                             |

---

## Role Decks (TLEs)

| Role                      | Card Name (TLE)     | Effect                                        | Requirements                                                      |
| ------------------------- | ------------------- | --------------------------------------------- | ----------------------------------------------------------------- |
| **Comms Officer**         | High-Gain Pass      | Downlink 2 Data at once; costs -1 Battery     | Follows **Data Capture**                                          |
| **Power Engineer**        | Battery Recondition | Reset Battery to exactly 3                    | Cannot be followed by **Maneuver Burn**                           |
| **Flight Dynamics Officer** | Precision Burn    | Restore Orbit to Nominal without Battery cost | Requires **Attitude Change**                                      |
| **Payload Officer**       | Science Burst       | Capture 2 Data in one slot; costs -1 Battery  | Requires **Comms Online**; Requires **Downlink** within 2 slots   |

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
| 2    | Solar Flare             | Comms Offline next round              |
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
