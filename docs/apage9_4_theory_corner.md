# Theory corner

TODO

Cool sites and articles:
* [https://robotics-explained.com/](https://robotics-explained.com/)

Describing impedance and admittance control in the context of a robot interacting with its environment can help clarify their differences and applications.

## Impedance Control

**Concept**:
- Impedance control is like controlling how "stiff" or "flexible" the robot feels when it interacts with the environment. It defines how the robot resists motion in response to external forces.
Impedance control regulates the force output of a system based on the position error.

**Analogy**:
- Imagine the robot's end effector is connected to the environment by a virtual spring-damper system. The robot adjusts the force it applies to mimic a specific stiffness, damping, and inertia.

**Implementation**:
- The robot measures its position, velocity, and possibly the force it applies.
- The controller calculates the desired force or torque output based on the difference between the actual and desired position/velocity, considering virtual mass, damping, and stiffness.
- The robot then applies this calculated force/torque to maintain the desired interaction characteristics.

**Example**:
- A robot arm is drilling into a surface. Impedance control ensures the robot maintains a steady drilling force despite variations in the surface hardness. If the surface becomes harder, the robot increases its force to maintain the drilling motion.

**Equation**:
$$F{\text{control}}= \frac{d^2x}{dt^2} + B \frac{dx}{dt} + Kx \$$

### Admittance Control

**Concept**:
- Admittance control is like controlling how easily the robot moves in response to external forces. It defines how the robot adapts its position or velocity based on the forces applied by the environment.
Admittance control regulates the position or velocity of a system based on the force error.

**Analogy**:
- Imagine the robot's end effector is like a balloon tethered to a point. The robot adjusts its position or velocity to move compliantly with the applied forces, mimicking a specific level of compliance and damping.

**Implementation**:
- The robot measures the external force applied to it and its own position and velocity.
- The controller calculates the desired position or velocity based on the measured force, considering virtual compliance and damping.
- The robot then adjusts its motion to match the desired position or velocity.

**Example**:
- A robot arm is holding a tray while a person places objects on it. Admittance control allows the robot to adjust its position smoothly to accommodate the added weight, ensuring the tray remains stable.

**Equation** (for velocity admittance control):
$$v_{\text{desired}} = \frac{F_{\text{ext}} - Kx}{B} \$$

**Equation** (for position admittance control):
$$x_{\text{desired}} = \frac{1}{K} F_{\text{ext}} - \frac{B}{K} v \$$

### Summary

**Impedance Control**:
- **Robot's Role**: The robot reacts to position/velocity changes by applying forces to resist motion.
- **Control Focus**: Force/torque output based on position/velocity error.
- **Interaction Feel**: Defines how stiff or flexible the robot feels (resistance).

**Admittance Control**:
- **Robot's Role**: The robot adjusts its motion in response to external forces.
- **Control Focus**: Position/velocity based on external force input.
- **Interaction Feel**: Defines how easily the robot moves (compliance).

### Choosing the Control Method

- **Impedance Control**: Suitable for tasks requiring precise force regulation and maintaining a specific motion despite external disturbances, such as machining or tasks where consistent force application is critical.
- **Admittance Control**: Suitable for tasks requiring adaptive and compliant motion, especially when interacting with unpredictable environments or humans, such as assisting or collaborating with humans in handling delicate objects.

By understanding these control strategies in terms of how the robot interacts with its environment, one can better appreciate their applications and benefits in various robotic tasks.


## Compliance

Compliance, in the context of control systems and robotics, refers to the ability of a system to yield or deform in response to an applied force. It is the inverse of stiffness (or rigidity), which measures the resistance of a system to deformation. High compliance means the system is easily deformable or flexible, whereas low compliance (high stiffness) means the system is resistant to deformation.

### Key Concepts of Compliance

- **Compliance** (\(C\)): It is defined as the inverse of stiffness (\(K\)). Mathematically, compliance \(C\) can be expressed as:
  \[ C = \frac{1}{K} \]
  Where \(K\) is the stiffness of the system.

- **Stiffness** (\(K\)): It quantifies the resistance of a system to deformation. High stiffness means the system resists deformation strongly when a force is applied.

### Compliance in Control Systems

In control systems, particularly in robotics, compliance is crucial for safe and effective interaction with the environment, especially in tasks that involve human-robot interaction or handling delicate objects.

### Example: Compliance in a Robotic Arm

Imagine a robotic arm equipped with compliance control. Here’s how compliance plays a role:

1. **Interaction with the Environment**:
   - When the robotic arm encounters an obstacle, a compliant control system allows the arm to yield slightly, reducing the risk of damage to both the arm and the obstacle.
   - High compliance makes the arm flexible, allowing it to absorb and adapt to external forces smoothly.

2. **Human-Robot Interaction**:
   - In collaborative tasks where a human and a robot work together, compliance ensures that the robot can adapt to the human’s movements without exerting excessive force, enhancing safety and cooperation.
   - If the human applies a force to the robot, a compliant robot will move or adjust its position in response, preventing injury or discomfort.

### Practical Implementation

Compliance can be implemented in robotic systems through both passive and active means:

- **Passive Compliance**:
  - Achieved using physical elements like springs, dampers, and flexible materials.
  - Example: A robotic gripper with soft, flexible fingers that conform to the shape of the object being held.

- **Active Compliance**:
  - Achieved using control algorithms that adjust the robot's motion or force output in real-time based on sensor feedback.
  - Example: A robotic arm that uses force sensors to detect applied forces and adjusts its position or velocity accordingly, implementing virtual compliance through software.

### Compliance in Control Equations

In control equations, compliance is often reflected in how the system responds to forces. For example, in admittance control, the system's compliance is an integral part of the control law:

$$\ x_{\text{desired}} = C \cdot F_{\text{ext}} \$$

Where:
- \ x_{\text{desired}} \ is the desired position.
- \( C \) is the compliance (inverse of stiffness).
- \( F_{\text{ext}} \) is the external force applied to the system.

This equation shows that the desired position change is directly proportional to the applied force, with the proportionality factor being the compliance.

### Summary

Compliance is a measure of how easily a system deforms in response to an applied force. In robotics and control systems, compliance is crucial for enabling smooth, adaptive, and safe interactions with the environment and humans. It is the inverse of stiffness and can be implemented both passively and actively. Understanding compliance helps in designing control systems that can effectively manage forces and movements, ensuring both precision and safety in robotic operations.