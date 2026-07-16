# 📥 ICRA BARN Challenge Submission Notes (ROS 1)

## 📌 Quick Summary
* **ROS Version:** ROS 1 Melodic (Ubuntu 18.04 container)
* **Configuration:** Tuned Classical E-Band Elastic Band Local Planner
* **Final Validated Metric Score:** **0.4063** (calculated over a 90-run stratified sample: worlds 0, 30, 60, 120, 150, 180, 210, 240, 270 × 10 runs each)
  * *Note on Evaluation Scope:* This score is based on the 90-run representative stratified sample rather than the full 500-world benchmark due to validation time limits.
* **Primary Submission Launch Point:** `run.py` (which internally executes the fully configured `move_base_EBAND.launch` stack).

---

## 🚀 Execution & Testing Instructions

To run the simulation and test this navigation stack in a standardized Singularity container:

1. **Verify the Container Image:**
   Ensure that the `nav_competition_image.sif` container is present in the repository root directory.

2. **Launch a Single Trial (e.g. World 0):**
   ```bash
   ./singularity_run.sh nav_competition_image.sif python3 run.py --world_idx 0
   ```

3. **Verify the Results Output:**
   Run results (success status, time, and calculated metric score) will be written to `out.txt`.

---

## 🛠️ Configuration Details
All configurations are defined in the ROS standard package folders:
* **Planner configuration:** [move_base_EBAND.launch](file:///home/sankala-mahidhar/jackal_ws/src/the-barn-challenge/jackal_helper/launch/move_base_EBAND.launch)
* **Tuned local planner parameters:** [base_local_planner_params_eband.yaml](file:///home/sankala-mahidhar/jackal_ws/src/the-barn-challenge/jackal_helper/configs/params/base_local_planner_params_eband.yaml)
* **Costmap and resets configuration:** [costmap_common_params.yaml](file:///home/sankala-mahidhar/jackal_ws/src/the-barn-challenge/jackal_helper/configs/params/costmap_common_params.yaml)
