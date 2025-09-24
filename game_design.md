# Project TLE – Game Design Document (Prototype v0.5)
Designed by Artur Foden

Workshop ID: 3574086791

## 1. Overview
- **Title:** Ground Station Ops  
- **Genre:** Cooperative, Systems-Engineering Puzzle  
- **Theme:** Players are mission control operators at a ground station, coordinating satellite passes to complete mission objectives.  
- **Core Loop:** Draw → Plan → Execute → Assess, over 5 sequential orbital passes.  

---

## 2. Objectives
- **Primary Goal:** Complete mission objectives before the end of Round 5.  
- **Failure States:**  
See card_text.md

---

## 3. Design Philosophy
### Sequential Puzzle (Chosen Approach)
- Each round (orbit) is treated as a self-contained **sequential puzzle**, where players must assemble a valid command timeline.  
- Previous rounds influence the spacecraft state (battery, comms, orbit), but cards do not persist physically across rounds.  
- **Rationale:** Easier to prototype and test adjacency mechanics, while still allowing cascading consequences via state tracking.  

### Persistent Timeline (Deferred Option)
- Alternative approach where cards persist across all rounds, creating a cumulative programming schedule.  
- More authentic to systems engineering but more complex and prone to analysis paralysis.  
- Reserved for later design iterations.  

---

## 4. Pre-Game Phase
At the start of the game, players draw **1 Mission Objective card** to define the win condition. Optionally, draw **1 Scenario Modifier card** to add difficulty or variety.  

### Mission Objectives Deck
All missions require **multiple tasks** to be completed. Difficulty is noted for balance and replayability.  
See card_text.md

### Scenario Modifiers Deck (Optional)
Adds **environmental twists** that change rules for all 5 orbits.  
See card_text.md

### Subsystem Starting State
- Battery = 3  
- Orbit = Nominal  
- Comms = Online  
- Data Stored = 0  

---

## 5. Communication & Quarterbacking
- **Hidden Hands:** Players keep their cards hidden from each other.  
- **Open Talk:** Players may discuss intentions, but cannot show cards.  
- **Anti-Quarterbacking Rule:**  
  - Each orbit has 4 slots (unless modified).  
  - Each player must fill at least 1 slot per orbit, **unless blocked slots reduce the number of available slots**.  
  - Players negotiate who contributes if fewer slots are available.  
- This ensures distributed decision-making while maintaining open communication.  

---

## 6. Cross-Pass Interactions
- **Definition:** Effects that occur in one pass but influence the **subsystem event rolls** or state in future passes.  
- **Mechanic:** Certain cards add or modify dice rolls during the **Subsystem Event Phase**, creating delayed consequences.  

**Examples:**
- *Data Capture Overload:* Capture 2+ Data in one pass → add +1 die roll next round.  
- *Aggressive Maneuver:* Perform burn at Battery ≤ 2 → add +1 die roll next round.  
- *Command Uplink Retry:* Failed uplink attempt → auto-retry occupies 1 slot next round.  

---

## 7. Components
- **Shared Deck (20 cards)**  
See card_text.md

- **Role Decks (1 unique card each per player)**  
See card_text.md

- **Subsystem State Board**  
  - Battery (0–5)  
  - Orbit Stability (Nominal / Off-Nominal)  
  - Comms (Online / Offline)  
  - Data Stored (0–3)  

- **Mission Cards**  
  - Define multi-task win conditions.  

- **Scenario Modifier Cards (Optional)**  
  - Add environmental twists to increase replayability.  

- **Timeline Board (Playmat)**  
  - 5 rows (one per orbit), each with 4 slots.  
  - Slots filled by cards, left-to-right.  
  - Empty slot = wasted opportunity.  
  - Blocked slot = cannot be filled this orbit (mark with “X”).  

- **Subsystem Event Table (d6)**  
See card_text.md

--- 

## 8. Gameplay Loop
Each round = 1 orbital pass.

1. **Draw Phase**  
   Each player draws 3 cards (mix of shared + role).  

2. **Planning Phase**  
   - Players discuss intentions but cannot reveal cards.  
   - Each player must commit at least 1 card to the available slots.  
   - Cards placed face down into slots.  

3. **Execution Phase**  
   - Reveal and resolve cards left-to-right.  
   - Apply adjacency rules and update spacecraft state.  
   - **Apply all Reveal Effects immediately when each card is flipped.**  

4. **Assessment Phase**  
   - Battery -1 (end-of-round drain).  
   - Roll subsystem event(s).  
   - Apply cross-pass effects (e.g., additional die rolls, blocked slots).  
   - Check mission progress and failure conditions.  

---

## 9. Example Round (Orbit 2)
- Timeline:  
  1. Solar Charge → Battery +2  
  2. Attitude Change (prep antenna alignment)  
  3. Data Capture → +1 Data  
  4. Downlink → 1 Data sent  

- Result: Battery = 3, Data Stored = 0, Orbit = Nominal, Comms = Online.  
- Subsystem Event Roll: 6 → Ground Station Conflict. Roll 1d4 → result 2.  
- Next orbit: Slot 2 blocked.  

---

## 10. Future Considerations
- Expand role decks with multiple unique cards per role.  
- Test hybrid mechanics where some cards persist across passes.  
- Introduce scenario-based missions (Earth Observation, Lunar Imaging, Deep Space Probe).  
- Scale difficulty by adjusting subsystem event probabilities.  
- Experiment with limited communication (restrict vocabulary, or add a Flight Director role).  

---

## 11. Prototype Status
- Card pool: ~25 total.  
- Player count: 2–4.  
- Rounds: 5.  
- Timeline = 4 slots/orbit (unless modified).  
- Blocked slots determined by d6 event + 1d4 roll.  
- Mission objectives multi-task (easy → hard).  
- Scenario modifiers optional.  
- System ready for **paper playtest** to validate adjacency, slot blocking, cross-pass interactions, and scenario setup.  
