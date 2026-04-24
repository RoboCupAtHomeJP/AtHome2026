[日本語](./2026_CML_Rule_ja.md) | [English](./2026_CML_Rule_en.md)

# Carry My Luggage (CML) — BRG 2026

Reference video: https://youtu.be/dzyJ1dHTulc
- https://youtu.be/l17cDwM82ec?si=1r7tf2h-VeWiYSx9 (Last year's CML video)
- https://www.youtube.com/watch?v=6OFh1U-yoo4 (example of collision)
- https://www.youtube.com/watch?v=s2g95Y9Me3c (example of non-collision)

> [!NOTE]
> This video is provided only as a reference from a previous event.
> Please note that the rules for this year are different.

## Main Goal

In this task, the robot is expected to assist the operator by carrying luggage to a parked car outside the arena. The robot must understand the operator’s instruction indicating which bag to take (left or right), follow the operator to the designated outdoor car location, and then autonomously return to the start position inside the arena.

## Focus

This task focuses on pointing recognition, manipulation, mapping and navigation in both known and unknown environments, person following, and task planning.

- Person following
- Indoor/outdoor navigation (known / semi-known environments)
- Passing through narrow spaces
- Obstacle avoidance
- Understanding instructions (left/right, start/stop following, arrival notification)

## Setup

- **Location**: A competition arena simulating a home environment will be used. The task takes place both inside and outside the arena. The `inside of the arena` may be mapped in advance and is treated as a `known environment`.
- **Start location**: The robot starts from a designated mark inside the arena.
- **Luggage (paper bags)**: Two paper bags are placed on the floor near the operator, one on the left and one on the right. The TC will place them.
  - **Size**: To be determined at the TLM.
- **Obstacles**: The following obstacles will be placed along the outdoor route. Their types and placement locations will be shared in advance at the TLM. At present, the layout has not yet been published, so the exact placement locations have not been finalized.
  - Chairs (hard-to-see objects)
  - Small items
  - Barriers
- **Operator**: One operator. Each team may choose any one member of their team.
- **Crowd**: Approximately two people will be placed outdoors.
- **Car location**: No actual car will be used. A fixed point designated by the organizers will be treated as the “car location”.

> [!WARNING]
> The rules may be subject to change. Any changes will be shared with all teams.

## Scenario

### Start Phase

1. **Competition time**: The time limit is **7 minutes**.
1. **Setup time**: Teams are given **5 minutes** for setup before the run.
1. **Placement**: The referee instructs the team to move the robot to the start position.
1. **Start**: The referee gives the start signal and starts the timer. At the same time, the team completes the final simple setup (such as pressing the start button) and leaves the area.
1. **Pointing**: At the start signal, the operator points to the pre-designated bag among the two paper bags.
1. **Confirmation**: The robot detects the operator, recognizes the indicated bag, and provides a confirmation response either verbally or on a screen.
1. **Grasping**: The robot grasps the designated bag (this may be skipped; Deus ex Machina is allowed).

### Follow-Me Phase

1. **Start following**: Once the robot is ready to follow, the operator starts walking from the known environment toward the unknown environment. Gesture-based initiation of following is also allowed.
1. **Walking**: The operator walks naturally at a slow pace without turning back. The robot follows at a safe speed.
1. **Follow me**: The robot follows the operator and moves from the indoor known environment to the outdoor unknown environment.
1. **Arrival at the car location**: When the operator reaches the designated car location, the operator verbally informs the robot of the arrival. The robot must recognize this speech input.
1. **Handover**: The robot hands the bag to the operator (not applicable if grasping was skipped).

> [!WARNING]
> Once the operator starts walking, they must not turn back toward the robot or stop walking.

### Navigation Phase

1. **Return declaration**: The robot makes a verbal return declaration, such as “I’m going back.”
1. **Navigation**: The robot autonomously navigates from the unknown environment back to the `start position` in the known environment. During the return, it must avoid any obstacles placed along the route. Whether to attempt obstacle avoidance is left to each team’s discretion (a bonus is awarded for each obstacle successfully avoided; there is no penalty for skipping them).
1. **Goal**: The task is completed when the robot returns to the `start position` (within a radius of 1 m).

## Manipulation Policy (for BRG)

- Grasping may be **skipped**. If skipped, the corresponding item receives 0 points, but no penalty is applied.
- If the robot is able to lift the bag from the floor in any manner, bonus points will be awarded.
- A grasping failure alone does not result in immediate disqualification, unless it involves a safety violation.
- The robot may verbally ask the operator to move the bag away in order to prevent navigation failure caused by the bag. In that case, the robot must clearly inform the operator that it is requesting the bag to be moved. Moving the bag away is treated as a penalty.
- If grasping is difficult, Deus ex Machina (human assistance) may be used.

## Local Rules

1. The competition time is **7 minutes**.
1. The setup time is **5 minutes**.
1. **One restart** is allowed, and the remaining time continues to run.
1. Skipping grasping is allowed (0 points for the corresponding item, no penalty).
1. Skipping obstacle avoidance is allowed (0 points for the corresponding item, no penalty).
1. The `start position` is defined as the area within a **1 m radius** from the mark placed at the start location.
1. `Re-entry into the arena` is considered valid once the entire robot has entered the arena.
1. The bags will always be placed sideways; they will not be placed upright.
1. If a team wishes to use an alternative signaling method as Deus ex Machina, it must be declared at the **TLM on the previous day**.
1. Safety has the highest priority. Dangerous behavior will result in immediate stoppage and a major penalty.

## Score Sheet

### Scoring Policy

Base score: 80%  
Bonus score: 20%  
Total reference score: **1000 points**

Recommended score distribution: recognition 10%, following 65%, grasping 25%

### Main Goal (800 points)

| No | Action | Score |
|---:|---|---:|
| 1 | Correctly detect and face the operator | 30 |
| 2 | Correctly recognize the target bag (left/right) and provide confirmation | 40 |
| 3 | Reach the designated bag position and stop nearby | 30 |
| 4 | Fully grasp the bag (both handles) *(skippable)* | 150 |
| 5 | Partially grasp the bag (e.g. one handle) *(skippable)* | 100 |
| 6 | Maintain following of the operator indoors (known environment) | 100 |
| 7 | Maintain following of the operator outdoors (unknown environment) | 150 |
| 8 | Successfully hand the luggage to the operator | 50 |
| 9 | Autonomously re-enter the arena | 80 |
| 10 | Autonomously return to the start position (within 1 m radius) | 70 |

### Bonus (maximum 200 points)

| No | Action | Score |
|---:|---|---:|
| B1 | Obstacle avoidance: avoid a hard-to-see object (chair) *(skippable)* | 50 |
| B2 | Obstacle avoidance: avoid a small item *(skippable)* | 50 |
| B3 | Obstacle avoidance: avoid a barrier *(skippable)* | 100 |

### Penalties

| Action | Deduction |
|---|---:|
| Lose sight of the operator for more than 5 seconds (robot re-detects automatically) | -50 |
| Re-detect the operator through interaction without physical contact | -100 |
| Re-detect the operator through direct physical contact | -200 |
| Strongly request the operator to stop or wait | -50 |
| Drop the bag during the task | -50 |
| Ask for the bag to be moved away | -100 |
| Contact with a person or object | -100 |
| Direct human assistance (e.g. guiding by hand) | -200 |
| No participation | -500 |

### Deus ex Machina

| Action | Deduction |
|---|---:|
| Use of an alternative signaling method (must be declared in advance at the TLM) | -100 |

### Restart Rule

- One restart is allowed, and the remaining time continues to run.
- A second or subsequent restart is not allowed.

## Instructions by the Organizing Committee (OC)

- Preparation
  - Select the robot’s `start position`.
  - Select the paper bag positions and assign the competition bag to the operator.
  - Select the obstacles the robot will face outdoors.
  - Select the goal position (designated car location).
- Announcements (TLM)
  - Announce the robot’s `start position`.
  - Announce which bag will be used.
  - Announce the types of obstacles to be used.
  - Coordinate the size and material of the paper bags with each team.

## Referee (TC) Responsibilities

- Gather **30 minutes before** the competition starts, receive instructions, and collect the score sheet.
- Score the run according to the score sheet.
- Cross-check the scoring with other TCs.
- Submit the score sheet to the OC.

## Items to Confirm at the TLM

- Ask each team for their preferred paper bag size, material, color, and texture.
- Share the types and placement locations of the obstacles.
- Share the layout details.
- Accept declarations of alternative signaling methods.