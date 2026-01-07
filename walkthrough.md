# Walkthrough - Switch Units to Units from Minutes

I have successfully updated the Production Sequencer to use "Units" as the primary measurement for capacity, batch sizes, and transition penalties, replacing the previous "Minutes" terminology.

## Changes Made

### Terminology & UI Updates
- **Daily Capacity**: Updated label and default value to `1000 Units`.
- **Transition Penalty**: Renamed "Transition Time" to "Transition Penalty" to reflect that it is a capacity-consuming value, not just time.
- **Optimization Goals**: Updated dropdown options:
    - "Minimum Transit Time" -> "Minimum Transit Penalty"
    - "Combined Min Time & Cost" -> "Combined Min Penalty & Cost"
- **Internal Logic**: Renamed variables like `remainingTime` to `remainingCapacity` and `totalTime` to `totalPenalty` to improve code clarity and alignment with the new units.

### Code Refactoring
The following files were updated:
- [script.js](file:///c:/Users/admin/.gemini/antigravity/scratch/production_sequencer_v3/script.js): Renamed state properties and local variables.
- [index.html](file:///c:/Users/admin/.gemini/antigravity/scratch/production_sequencer_v3/index.html): Updated UI labels and default values.
- [test_logic.js](file:///c:/Users/admin/.gemini/antigravity/scratch/production_sequencer_v3/test_logic.js): Updated mock state and logic to match the new property names.

## Verification Results

### Logic Consistency
The optimization logic now treats 1 unit of production as 1 unit of capacity. If a transition has a penalty of `30`, it consumes `30` units of the `1000` units daily capacity. This is consistent across all optimization goals.

### UI Review
All labels in the "Data Entry", "Production Plan", and "Dashboard" views now correctly refer to "Units" or "Penalty".

### Advanced Optimization Engine (V2.0)
- **Multi-day Look-ahead**: Now considers tomorrow's transitions when planning today's batches.
- **Production Leveling**: Automatically smoothes demand spikes to prevent capacity overruns.
- **Simulated Annealing (Search)**: Explores 50 different global sequences to find the true cost/penalty minimum.
- **Auto-Benchmarking**: The app automatically selects the best of these four strategies every time you optimize.

render_diffs(file:///c:/Users/admin/.gemini/antigravity/scratch/production_sequencer_v3/script.js)
render_diffs(file:///c:/Users/admin/.gemini/antigravity/scratch/production_sequencer_v3/index.html)
