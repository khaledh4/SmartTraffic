# SmartTraffic
**Smart Traffic Management System Using IoT and AI Technology**

This repository contains the graduation project developed for the Network Engineering and Security Department at Jordan University of Science and Technology (Fall 2026).

---

## Project Overview
Current traffic lights operate on pre-set timers (fixed-time inefficiency), ignoring real-time traffic load, which leads to high latency at intersections and critical delays for emergency responders. 

Our proposed system is a cost-effective, easily deployable Smart Traffic Management System that utilizes **Computer Vision (YOLOv8)**, **IoT infrastructure**, and a mathematically proven **Dynamic Optimization Algorithm** to minimize wait times, maximize intersection throughput, and prioritize emergency vehicles.

## Key Features & Objectives
* **AI Vehicle Detection:** High-accuracy real-time vehicle counting and emergency vehicle recognition using YOLOv8.
* **IoT Connectivity:** Seamless wireless communication between edge/cloud computing, ESP32-CAMs, and Arduino controllers.
* **Dynamic Optimization:** Adaptive traffic signal control utilizing the Lyapunov Max-Pressure algorithm to reduce waiting times.
* **Emergency Vehicle Priority:** Built-in priority mechanisms for ambulances and fire trucks to prevent critical response time failures while maintaining regular traffic flow.
* **Cost-Effective & Scalable:** Replaces expensive wired sensors and heavy construction with cheap wireless cameras and simple microcontrollers, making it ideal for historic and established cities.

## Scientific Foundation
The system abandons static timing in favor of the Lyapunov Max-Pressure control algorithm to guarantee mathematical stability during peak traffic hours. The algorithm calculates a pressure score for each road using the formula:

**`P = Q × W²`**
* **P (Pressure Score):** The calculated priority for the road.
* **Q (Queue Length):** Number of vehicles detected by the YOLOv8 AI.
* **W (Wait Time):** Total time since the road last had a green light.

## AI Model Training
<table>
  <tr>
    <td><img src="Images/posimgs.gif" width="400"></td>
    <td><img src="Images/recg.gif" width="400"></td>
  </tr>
</table>

To achieve accurate vehicle detection and classification, the AI model was trained using a custom dataset prepared through Roboflow. Images were collected from multiple angles and under varying lighting conditions and backgrounds. Each image was carefully annotated to distinguish between regular vehicles and emergency vehicles. The model was trained to accurately recognize and classify vehicles, as well as count them in real time, ensuring reliable performance.

## System Architecture
<img src="Images/digram.png" width="800">

The hardware and software seamlessly communicate to control the intersection:
1. ESP32-CAM captures and streams intersection video.
2. Network Gateway routes the stream to the Cloud Computing/Edge environment.
3. The server runs AI inferences (YOLOv8) and the Control Algorithm.
4. Control commands are forwarded via the Gateway to an Arduino UNO R4 WiFi.
5. The Arduino executes the light switches on the Traffic Light Module and returns status confirmations.

## Simulation & Results
<img src="Images/simulationResult.png" width="800">

Before physical prototyping, the system was extensively benchmarked against static baselines using SUMO (Simulation of Urban MObility) and the LuST (Luxembourg SUMO Traffic) real-world dataset via a TraCI Python controller interface.

**Performance Improvements:**
* **Average Delay:** Reduced by approximately 50% compared to traditional fixed-time systems.
* **Average Travel Time:** Decreased from 779 seconds to 638 seconds.
* **Throughput:** Achieved higher capacity, keeping the intersection stable even under heavy load.

## Future Work
* **Relay-Based Switching Model:** Integrating relays to seamlessly fail-over between smart AI control and normal fixed-time control if the network drops.
* **Ultrasonic Sensors:** Adding hardware fallbacks to detect if a camera lens is blocked or obscured.
* **Advanced Emergency Signaling:** Deploying dedicated smart signals that safely guide emergency vehicles through intersections while optimizing the clearing of civilian traffic.

## Team Members
* Khaled Abdalnasser Aldabet
* Mohammad Iyad Shatarah
* Amine Feras Kiwan
* Saleh Mohammad Talafha

---
*Developed as a graduation project at Jordan University of Science and Technology (JUST).*
