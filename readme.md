# WarePath Documentation

## [1] Starting the Program
You can't use the program without knowing how to start it! Upon importing the github repository or downloading the `final demo.py` file alongside the `layout1.csv`, `layout2.csv`, and `layout3.csv` files, do the following things:

1. Navigate to the `final demo.py` file.
2. Run the file using your IDE.
3. You're in!

Now, let's learn how to navigate through the different functions of the program

## [2] Using the Grid
The central grid (38 x 38) is your interactive warehouse floor. You can draw obstacles, place targets, and move the starting point.

* **Draw Shelves/Walls (Left Click):** Click or drag your mouse to paint white blocks. These represent obstacles (shelves, walls) that the picker cannot walk through.
* **Add Order Item (Right Click):** Click any empty square to place a Teal target. These represent the items the operator needs to pick up.
    * *Note for BFS:* The order in which you place these targets matters!
* **Set Depot/Spawn (Middle Click or 'S' + Left Click):** Sets the Orange starting point. This is where the forklift/operator begins the shift and where they must return.

## [3] Running Simulations

Once your grid is set up with at least one **Spawn Point** and one **Target**, you can run the algorithms using the Left Sidebar.

### Option A: Run Breadth First Search (Sequence)
This runs a standard sequential pickup.
* **Logic:** The operator visits the targets **in the exact order** you placed them on the grid (e.g., Target 1 $\to$ Target 2 $\to$ Target 3).
* **Use Case:** Best for FIFO (First-In-First-Out) logistics or when priority orders must be fulfilled specifically.
* **Visual:** Displays a **Blue** path.

### Option B: Run Greedy Nearest Neighbor
This runs an optimized proximity-based pickup.
* **Logic:** From the current location, the operator calculates which unvisited target is the closest (accounting for walls) and goes there next.
* **Use Case:** Best for minimizing travel time and distance regardless of order priority.
* **Visual:** Displays a **Blue** path.

## [4] Return to Depot

A warehouse loop isn't complete until the operator returns to the start!

1.  Complete a simulation using either algorithm above.
2.  The **"Return to Depot"** button on the left sidebar will become enabled.
3.  Click it to visualize the path from the *last* picked item back to the Orange Spawn point.
4.  **Visual:** Displays a **Green** path to distinguish it from the picking route.

## [5] Configs & Data Metrics

The Right Sidebar provides data analysis tools to measure path efficiency.

* **Distance Config:** enter a number in the "Units per Square" box to simulate real-world scale (e.g., "1" meter per square).
* **The Table:** Logs every step of the journey.
    * **Points:** The ID of the stop (S0, S1, etc.).
    * **Distance:** The number of grid squares traveled.
    * **Units:** The total distance multiplied by your "Units per Square" setting.
    * **SUM:** Displays the total distance for the picking phase and the return phase separately.

## [6] Saving & Loading Layouts

You can save your warehouse layouts to use later (there are 3 available slots).

* **Save:** Writes the current positions of all Walls, Targets, and the Spawn point to the corresponding CSV file (e.g., `layout1.csv`).
* **Load:** Wipes the current grid and reconstructs the layout saved in that file.

*Warning: Clicking "Save" overwrites whatever data is currently in that CSV slot!*

## [7] Controls Cheat Sheet

| Action | Control |
| :--- | :--- |
| **Draw Wall** | Left Click |
| **Add Target** | Right Click |
| **Set Spawn** | Middle Click *or* 'S' + Left Click |
| **Delete Item** | Click the item again (toggles off) |
| **Reset Grid** | Click "Reset Warehouse" |

## Requirements

To run this project locally, you need Python installed along with the following library:

```bash
pip install pygame
