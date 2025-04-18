# Harry Potter Merchandise Production Line - RobotStudio Project

This project simulates an industrial robotic production line for Universal Studios' Harry Potter theme park merchandise, designed to commemorate their 30th anniversary. The system uses two ABB IRB 1600 robots to create decorative plates with Harry Potter-themed designs.

## Project Overview

The production line creates two types of collector plates:
1. Harry Potter Deathly Hallows triangle design
2. Harry Potter Lightning Bolt design

Each plate goes through a multi-step manufacturing process where both robots collaborate to complete the task.

## System Components

- Two ABB IRB 1600 robotic arms
- Dual tool TCPs (vacuum gripper and pen tool)
- Conveyor belt system
- Working desk
- Sorting pallet system

## Process Flow

1. Plates arrive on the conveyor belt
2. **Robot 1**:
   - Detects plate using sensors
   - Picks up the plate using vacuum tool
   - Places plate on the working desk
   - Draws the base square frame design
   
3. **Robot 2**:
   - Detects completion of Robot 1's task
   - Draws the specific design (Deathly Hallows or Lightning Bolt)
   - Picks up the finished plate
   - Sorts plates to the appropriate stack based on design type

## Technical Implementation

### Robot Configuration
- Model: ABB IRB 1600 (6 degrees of freedom)
- Maximum reach: 1.45 meters
- End effector: Dual TCP with vacuum gripper and pen tool

### Work Objects
**Robot 1:**
- Workbox: Referenced to plate corner at conveyor sensor position
- Worktable: Sets the placing point on working desk
- Workpaint_box: References starting point for printing design

**Robot 2:**
- Workdraw_box: References starting point for design printing
- Workvacuum: Positioned at plate center for vacuum pickup
- Workpallet: Located at pallet center for sorting

### Movement Types
- **MoveJ**: Used for fast, non-precision movements when transporting objects
- **MoveL**: Used for precise, straight-line movements during approach sequences
- **MoveC**: Used for curved trajectories in the Deathly Hallows design

### Program Structure
The program contains several PROC routines:

**Robot 1:**
- Move PROC: Transports plates from conveyor to working desk
- PAINT PROC: Draws initial square frame

**Robot 2:**
- PAINT2 PROC: Draws design variants (Deathly Hallows or Lightning Bolt)
- MOVE2 PROC: Transports and sorts plates to appropriate pallets

### Synchronization
- Signal-based communication between robots
- Boolean-based decision making for design selection and sorting
- SmartComponent integration for conveyor control

## Simulation Features
- Fully synchronized dual-robot operation
- Automatic plate generation and conveyor system
- Vacuum gripper simulation with attacher/detacher components
- Design-based sorting logic
- Optimized path planning and robot movements

## Project Team
- Andrea Álvarez Campos
- Álvaro Narváez López
- Laura Pons García

## Usage Instructions
1. Open the project file in RobotStudio
2. Run the simulation to observe the complete production process
3. The program can be modified to change design preferences or process parameters
