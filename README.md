# 🦾 LeRobot Hackathon: Adaptive Gripper Mounting for Multi-Object Tasks

This repository documents my submission to the **LeRobot Worldwide Hackathon 2025**, under the **Hardware Improvement** challenge.

## 🎯 Objective

To enhance the SO-101 robot's physical capabilities by enabling it to:
1. Dynamically switch between multiple grippers,
2. Select the correct gripper based on the object presented,
3. Perform complex manipulation tasks using the right tool for the job.

---

## 🧪 Task Demonstration

The task was divided into three stages and recorded across [3 demo videos](./videos/):

1. **Pick a dressing bottle** using the **default gripper**.
2. **Mount and use a forklift gripper** to lift a **pallet carrying two water bottles**.
3. **Mount a suction cup gripper**, which connects to a **vacuum motor** that activates via **electrical contact upon closing the gripper**, then **pick and place an egg**.

> 📹 Video durations:
> - `IMG_0104.MOV`: Default Gripper
> - `IMG_0105.MOV`: Forklift Gripper
> - `IMG_0107.MOV`: Suction Cup Gripper

---

## 🧠 Learning Approach

The robot was trained using the **ACT Policy** provided by the `lerobot` library.

- **Training Dataset:** 60 episodes in total
  - 20 per gripper (default, forklift, suction cup)
- **Inference Goal:** Identify the correct gripper based on object type and perform the full mount + pick/drop action.

---

## ⚠️ Important Note

While the robot **successfully inferred the correct gripper** during inference runs, it **failed to mount the gripper and complete the pick/drop** operation. This suggests that:
- Gripper mounting mechanics were not robust enough for inference-stage generalization.
- Additional domain randomization and mounting trajectory supervision may be required.

---

## 🔩 Hardware Enhancements

- Designed and 3D printed **modular gripper mounts**.
- Built a simple **vacuum pump circuit** controlled by the gripper’s closing action.
- All STL and wiring diagrams are included in [`hardware/`](./hardware).

---

## 📁 Folder Overview

| Folder         | Content                                                 |
|----------------|----------------------------------------------------------|
| `dataset/`     | ACT training episodes and label info                    |
| `grippers/`    | 3D models and specs of each gripper used                |
| `hardware/`    | Circuit diagrams, CAD models, and hardware add-ons      |
| `inference/`   | Inference scripts and logs using trained ACT policy     |
| `videos/`      | Task demonstration videos                               |

---

## 🤖 Dependencies

- `lerobot` library
- `gymnasium` for simulation (if extended)
- Python 3.7

---

## 🔮 Future Work

- Add force/torque sensors to validate mount status.
- Train using a larger dataset with failed mounting attempts.
- Include motion primitives for mounting trajectory.

---

## 📜 License

MIT License
