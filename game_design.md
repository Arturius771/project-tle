# Ground Station Ops – Game Design Document (Prototype v0.2)

## 1. Overview
- **Title:** Ground Station Ops  
- **Genre:** Cooperative, Systems-Engineering Puzzle  
- **Theme:** Players are mission control operators at a ground station, coordinating satellite passes to complete mission objectives.  
- **Core Loop:** Draw → Plan → Execute → Assess, over 5 sequential orbital passes.  

---

## 2. Objectives
- **Primary Goal:** Complete mission objectives (e.g., downlink data, perform maneuvers) before the end of Round 5.  
- **Failure States:**  
  - Battery reduced to 0.  
  - Comms permanently offline.  
  - Subsystem failures exceed threshold (e.g., 3).  
  - Mission objectives not completed by end of Round 5.  

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

## 4. Communication & Quarterbacking
- **Hidden Hands:** Players keep their cards hidden from each other.  
- **Open Talk:** Players may discuss intentions, but cannot show cards.  
- **Anti-Quarterbacking Rule:**  
  - Each orbit has 4 slots.  
  - Each player must contribute at least 1 card if there are enough open slots. 
  - No player may fill all 4 slots.  
- This ensures distributed decision-making while maintaining open communication.  

---

## 5. Cross-Pass Interactions
- **Definition:** Effects that occur in one pass but influence the **subsystem event rolls** or state in future passes.  
- **Mechanic:** Certain cards add or modify dice rolls during the **Subsystem Event Phase**, creating delayed consequences.  

**Examples:**
- *Data Capture Overload:* Capture 2+ Data in one pass → add +1 die roll next round.  
- *Aggressive Maneuver:* Perform burn at Battery ≤ 2 → add +1 die roll next round.  
- *Command Uplink Retry:* Failed uplink attempt → auto-retry occupies 1 slot next round.  

---

## 6. Components
- **Shared Deck (20 cards)**  
  - Solar Charge (x4)  
  - Battery Drain (x2)  
  - Data Capture (x3)  
  - Downlink (x3)  
  - Maneuver Burn (x2)  
  - Attitude Change (x2)  
  - Command Uplink (x2)  

- **Role Decks (1 unique card each per player)**  
  - Comms Officer: High-Gain Pass  
  - Power Engineer: Battery Recondition  
  - Flight Dynamics Officer: Precision Burn  
  - Payload Officer: Science Burst  

- **State Board**  
  - Battery (0–5)  
  - Orbit Stability (Nominal / Off-Nominal)  
  - Comms (Online / Offline)  
  - Data Stored (0–3)  

- **Mission Cards**  
  - Define endgame objectives (e.g., “Downlink 2 Data by Round 3,” “Perform 1 Maneuver before Round 5”).  

- **Timeline Board (Playmat)**  
  - 5 rows (one per orbit), each with 4 slots.  
  - Slots filled by cards, left-to-right.  
  - Empty slot = wasted opportunity.  
  - Blocked slot = cannot be filled this orbit (mark with “X”).  

- **Subsystem Event Table (d6)**  
  1. Eclipse → Battery -1  
  2. Solar Flare → Comms Offline next round  
  3. Gyro Drift → Orbit Off-Nominal  
  4. Nominal pass → No effect  
  5. Payload Glitch → Lose 1 stored data  
  6. Ground Station Conflict → Roll 1d4; block that slot next round  

---

## 7. Gameplay Loop
Each round = 1 orbital pass.

1. **Draw Phase**  
   Each player draws 3 cards (mix of shared + role).  

2. **Planning Phase**  
   - Players discuss intentions but cannot reveal cards.  
   - Each player must commit at least 1 card to the 4 available slots.  
   - Cards placed face down into slots.  

3. **Execution Phase**  
   - Reveal and resolve cards left-to-right.  
   - Apply adjacency rules and update spacecraft state.  

4. **Assessment Phase**  
   - Roll subsystem event(s).  
   - Apply cross-pass effects (e.g., additional die rolls, blocked slots).  
   - Check mission progress and failure conditions.  

---

## 8. Example Round (Orbit 2)
- Timeline:  
  1. Solar Charge → Battery +2  
  2. Attitude Change (prep antenna alignment)  
  3. Data Capture → +1 Data  
  4. Downlink → 1 Data sent  

- Result: Battery = 3, Data Stored = 0, Orbit = Nominal, Comms = Online.  
- Subsystem Event Roll: 6 → Ground Station Conflict. Roll 1d4 → result 2.  
- Next orbit: Slot 2 blocked.  

---

## 9. Future Considerations
- Expand role decks with multiple unique cards per role.  
- Test hybrid mechanics where some cards persist across passes.  
- Introduce scenario-based missions (Earth Observation, Lunar Imaging, Deep Space Probe).  
- Scale difficulty by adjusting subsystem event probabilities.  
- Experiment with limited communication (restrict vocabulary, or add a Flight Director role).  

---

## 10. Prototype Status
- Card pool: ~25 total.  
- Player count: 2–4.  
- Rounds: 5.  
- Timeline = 4 slots/orbit.  
- Blocked slots determined by d6 event + 1d4 roll.  
- System ready for **paper playtest** to validate adjacency, slot blocking, and cross-pass interactions.  
