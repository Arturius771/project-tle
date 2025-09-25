# Project TLE  
*A Cooperative Systems-Engineering Puzzle Game*  

---

## Introduction  

Welcome to **Project TLE**. You and your fellow players are mission control operators, tasked with guiding a satellite through a critical 5-orbit mission. Your goal is to complete the mission objectives before the final orbit ends — while keeping the spacecraft powered, online, and in stable orbit.  

This is not a game of luck alone — it’s a **systems-engineering puzzle**. Each decision you make has ripple effects. A poor sequence of commands may drain your batteries, leave you without communications, or block future actions. The team must plan carefully, communicate clearly, and react to unexpected subsystem events.  

If you succeed, you’ll prove your mission control team is ready for the toughest challenges in space. If you fail, the satellite is lost — and so is the mission.  

---

## Components  

- **Shared Deck**: ~20 Timeline Event (TLE) cards.  
- **Role Decks**: Each player gets 1 unique card (and may unlock advanced cards).  
- **Mission Objective Cards**: Define win conditions.  
- **Scenario Modifier Cards (optional)**: Environmental twists.  
- **Subsystem State Board**: Tracks Battery (0–5), Orbit Stability, Comms (Online/Offline), Data Stored (0–3).  
- **Timeline Board (Playmat)**: 5 rows (1 per orbit), each with 4 slots (unless modified).  
- **Dice**: 1d6 for subsystem events, 1d4 for slot conflicts.  
- **Tokens/Markers**: To mark subsystem states and blocked slots.  

---

## Setup  

1. Place the **Subsystem State Board** in the center.  
   - Battery = 3  
   - Orbit = Nominal  
   - Comms = Online  
   - Data Stored = 0  

2. Draw **1 Mission Objective card**. This defines your win condition.  
3. (Optional) Draw **1 Scenario Modifier card** to increase difficulty.  
4. Shuffle the **Shared Deck**. Each player draws 3 cards (mix of shared + role).  
5. Place the **Timeline Board** with 5 rows × 4 slots. This is your planning grid.  

---

## Gameplay Overview  

The game lasts **5 orbits**. Each orbit has four phases:  

### 1. Draw Phase  
- Each player draws up to 3 cards.  

### 2. Planning Phase  
- Discuss intentions openly, but you **cannot show your cards**.  
- Each player must commit at least 1 card to the timeline slots (unless blocked).  
- Cards are placed face-down, left-to-right.  

### 3. Execution Phase  
- Reveal cards in order.  
- **Apply all Reveal Effects immediately** when a card is flipped.  
- Resolve card effects, update subsystem states.  
- If a card’s **conditions** are not met, it becomes a wasted slot -> turn it over.  

### 4. Assessment Phase  
- Battery −1 (baseline power drain).  
- Roll **1d6 Subsystem Event** (plus any extra rolls). Apply results.  
- Apply cross-pass effects (delayed consequences).  
- Check for mission progress and subsystem failures.  

Repeat for all 5 orbits.  

---

## Card Rules  

Each card has:  

- **Effect**: The main action (e.g., “+2 Battery”).  
- **Conditions**: Sequencing rules (“Must follow” or “Must precede”) or state requirements (“Requires Battery ≥ 2”).  
- **Reveal Effect**: Immediate impact that applies as soon as the card is revealed, even if the main effect fails.  

**Key Distinctions**:  
- *Must follow / Must precede*: Interaction between timeline cards.  
- *Requires*: A subsystem condition must be true.  
- *Reveal Effect*: Always applied, even if the card is wasted.  

See the card reference sheet for full details.  

---

## Subsystem Events  

At the end of each orbit, roll 1d6:  

| Roll | Event                   | Effect                               |
| ---- | ----------------------- | ------------------------------------ |
| 1    | Eclipse                 | Battery −1                           |
| 2    | Solar Flare             | Comms Offline next round             |
| 3    | Gyro Drift              | Orbit Off-Nominal                    |
| 4    | Nominal Pass            | No effect                            |
| 5    | Payload Glitch          | Lose 1 Data Stored                   |
| 6    | Ground Station Conflict | Roll 1d4; block that slot next round |  

---

## Failure Conditions  

Your mission fails immediately if:  

- **Battery = 0** → Satellite unpowered.  
- **Comms Offline at end of orbit** → Lost contact.  
- **3 or more Subsystem Failures at end of orbit** → Too many irrecoverable issues.  
- **Mission Objectives not complete by end of Orbit 5** → Deadline missed.  

### Subsystem Failures

| Subsystem      | Failure Condition                                                     | Notes                                                                                   |
| -------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Battery**    | Battery reaches **0**                                                 | Immediate mission failure (satellite unpowered).                                        |
| **Comms**      | Comms are **offline**                                                 | Mission failure if offline at end of orbit (permanent loss of contact).                 |
| **Orbit**      | Orbit remains **Off-Nominal**                                         | Only matters if the Mission Objective specifies Nominal orbit at mission end.           |
| **Payload**    | Stored data >= 1                                                      | Not an instant fail; only causes mission failure if the data objective becomes impossible. |

---

## Example Round  

**Orbit 2 Timeline**:  
1. Solar Charge → Battery +2  
2. Attitude Change (preps antenna)  
3. Data Capture → +1 Data  
4. Downlink → Sends 1 Data  

**Results**:  
- Battery = 3, Data Stored = 0  
- Orbit = Nominal, Comms = Online  
- Subsystem Event Roll = 6 → Ground Station Conflict (slot 2 blocked next orbit)  

---

## Tips for Success  

- **Balance Power**: Never let Battery reach 0.  
- **Maintain Comms**: Comms Offline is the most dangerous failure.  
- **Sequence Smartly**: Place cards so “Must follow / Must precede” conditions are satisfied.  
- **Plan Ahead**: Many Reveal Effects punish poor timing — think two orbits ahead.  
- **Cooperate**: Everyone must contribute, but coordination is key.  

---

## Game End  

The game ends after **Orbit 5** or upon immediate subsystem failure.  
- If all Mission Objectives are complete → **Victory!**  
- Otherwise → **Mission Failure.**  
