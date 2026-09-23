# Parachute Descent Simulation & Optimization

## Project Overview

![Application](ProjetSIM-Parachute/src/main/images/App%20.png)

### General Description

Parachute descents involve several physical parameters that can significantly affect the trajectory and overall performance of a jump. One of the key factors is the timing of parachute deployment, which influences the parachutist's descent speed, trajectory, control, landing conditions, and total jump time.

However, determining an appropriate deployment time can be difficult without a mathematical and physical model.

This project addresses this problem by developing a **Java-based parachute descent simulation** that models the physical behavior of a parachutist during free fall and after parachute deployment. The program uses user-defined parameters and physics-based calculations to simulate the descent and determine an optimal deployment time according to the model.

### Objective

The main objective of this project is to automatically calculate and simulate the parameters of a parachute jump.

The user provides parameters such as:

* Initial altitude
* Parachutist mass
* Parachute surface area

Based on these inputs, the program performs physics-based calculations to simulate the parachutist's motion and determine the optimal parachute deployment point according to the simulation model.

During the simulation, the application displays real-time information such as:

* Velocity
* Altitude
* Elapsed time
* Forces acting on the parachutist
* Position throughout the descent

The goal is to provide an interactive visualization of how these physical parameters affect a parachute descent.

> **Note:** This project is an educational simulation and is not intended to provide real-world parachuting or safety recommendations.

## Target Users

The project was designed as an educational and simulation tool that could be relevant to:

* Beginner parachutists
* Experienced parachutists
* Skydiving instructors
* Parachuting companies
* People interested in physics-based simulations and extreme sports

---

# Application Architecture

## Model-View-Controller (MVC)

The application follows a **Model-View-Controller (MVC)** architecture to separate the physical simulation, graphical interface, and application control logic.

### Model

The **Model** contains the classes responsible for the simulation logic, physical calculations, and state of the simulated objects.

#### `MoteurPhysique`

`MoteurPhysique` is the core of the physical simulation. It calculates the forces acting on the parachutist and continuously updates their:

* Acceleration
* Velocity
* Position

The calculations take into account factors such as gravity and air resistance.

The class also determines the parachute deployment point based on the simulation parameters, including altitude and terminal velocity.

Supporting classes such as `Gravite` and `ResistanceAir` handle specific force calculations used by the physics engine.

#### `Parachutiste`

`Parachutiste` represents the parachutist and stores their physical state, including:

* Position
* Velocity
* Mass
* Other simulation parameters

The physics engine continuously reads and updates this state throughout the simulation.

#### `ObjetPhysique`

`ObjetPhysique` is an abstract class defining the fundamental properties related to the movement of simulated physical objects.

#### `ObjetEnvironnant`

`ObjetEnvironnant` extends `ObjetPhysique` and provides the structure for environmental objects within the simulation.

Classes such as `Nuage` and `Avion` inherit from this structure. Their positions are calculated by the Model and synchronized with their visual representations in the View.

#### `Simulateur`

`Simulateur` acts as an entry point for the simulation Model. It coordinates the parachutist, environmental objects, and physics engine while maintaining the overall state of the simulation.

---

## View

The **View** contains the graphical components that allow the user to interact with and visualize the simulation.

### `FenetrePrincipale`

`FenetrePrincipale` is the main graphical container of the application. It assembles the different visual components, manages user interactions, loads the FXML files, and coordinates graphical updates.

The main View components include:

### `InterfaceParametres`

Allows the user to enter and validate the jump parameters, including:

* Mass
* Initial altitude
* Parachute surface area

### `VueAnimation`

Handles the visual representation of the parachute descent, including the:

* Parachutist
* Clouds
* Ground
* Movement and animation

### `VueStatistique`

Displays real-time simulation data such as:

* Velocity
* Altitude
* Forces
* Elapsed time

---

## Controller

The **Controller** coordinates communication between the Model and the View.

### `MainJavaFX`

Serves as the application's entry point and launches the JavaFX application.

### `AppController`

Initializes the main View and the `SimulationController`, establishing the necessary connections between the graphical interface and the simulation.

### `SimulationController`

`SimulationController` coordinates the simulation loop.

It uses JavaFX's `AnimationTimer` to continuously update the simulation. At each iteration, it:

1. Retrieves the parameters entered by the user.
2. Sends them to the Model.
3. Updates the physical calculations.
4. Retrieves the updated simulation state.
5. Refreshes the graphical interface.

This structure ensures that the physical calculations and graphical representation remain synchronized throughout the simulation.

---

# UML Diagram

![UML Diagram](ProjetSIM-Parachute/src/main/images/UML%20.png)

---

# Technologies Used

## Programming Environment

### IntelliJ IDEA

**IntelliJ IDEA** was used as the primary Integrated Development Environment (IDE) for writing, debugging, and managing the Java application.

### Java

**Java** is the main programming language used in the project. Its object-oriented programming features were particularly useful for structuring the simulation through classes, inheritance, and encapsulation.

---

## User Interface & Graphics

### JavaFX

**JavaFX** was used to develop the graphical user interface and animations.

It provides the framework for:

* User interface components
* Animations
* Image rendering
* Real-time graphical updates
* User interaction

### Scene Builder

**Scene Builder** was used to visually design the application's interface and generate the corresponding FXML structure.

Its drag-and-drop interface made it easier to create and organize complex UI layouts without manually creating every component in Java code.

---

## Collaboration & Version Control

### GitHub

**GitHub** was used for version control and team collaboration.

It allowed the team to:

* Track changes to the code
* Maintain a history of the project
* Work on different features simultaneously
* Restore previous working versions
* Share code between team members

### Microsoft Teams

**Microsoft Teams** was used for team communication, document sharing, project coordination, and scheduling work sessions.

---

# Scientific Concepts

This project combines concepts from **physics, mathematics, and computer science**.

## Physics

The simulation applies principles of classical mechanics to model the parachutist's motion.

The main forces considered include:

* **Gravity**
* **Air resistance / drag**

These forces are used to calculate the parachutist's acceleration, velocity, and position throughout the simulation.

The model also incorporates the concept of **terminal velocity** and analyzes the effect of parachute deployment on the parachutist's deceleration.

The fundamental relationship:

$$
\sum F = ma
$$

is used to determine acceleration from the net force acting on the parachutist.

## Mathematics

Mathematical concepts are used to translate the physical model into computational calculations.

These include:

* Vector calculations
* Force calculations
* Acceleration
* Velocity
* Position
* Terminal velocity
* Equations of motion
* Time and altitude calculations

These mathematical models allow the program to continuously update the state of the simulation.

## Computer Science

Computer science is essential for implementing the mathematical and physical models as a functional simulation.

The project applies:

* Object-oriented programming
* Inheritance
* Encapsulation
* MVC architecture
* Event-driven programming
* Real-time animation
* Graphical user interface development

Java allows these mathematical models to be implemented as algorithms and visualized dynamically through JavaFX.

---

# Simulation Workflow

The general workflow of the application is:

```text
User Input
    ↓
Simulation Parameters
    ↓
Physics Engine
    ↓
Force Calculations
    ↓
Acceleration
    ↓
Velocity & Position Updates
    ↓
Parachute Deployment
    ↓
Real-Time Visualization
```

### Example Simulation

For example, the user could enter:

* **Parachutist mass:** 90 kg
* **Parachute surface area:** 5 m²
* **Initial altitude:** User-defined

After the simulation starts, the physics engine calculates the forces acting on the parachutist, including gravity and air resistance.

The resulting net force is used to calculate acceleration:

$$
\sum F = ma
$$

The acceleration is then used to update the parachutist's velocity and position over time.

The simulation first estimates the parachutist's terminal velocity during free fall. Based on the model's parameters, an appropriate deployment altitude is determined. When the parachutist reaches this altitude, the parachute is deployed and the resulting change in velocity is simulated.

Throughout the simulation, the calculated values are continuously sent to the JavaFX interface. The user can therefore observe the evolution of:

* Altitude
* Velocity
* Forces
* Elapsed time
* Position

in real time.

---

# Project Structure

The application is organized around three main components:

```text
Model
├── MoteurPhysique
├── Gravite
├── ResistanceAir
├── Parachutiste
├── ObjetPhysique
├── ObjetEnvironnant
├── Nuage
├── Avion
└── Simulateur

View
├── FenetrePrincipale
├── InterfaceParametres
├── VueAnimation
└── VueStatistique

Controller
├── MainJavaFX
├── AppController
└── SimulationController
```

---

# Project Context

This project was developed as a **team-based programming project** combining concepts from mathematics, physics, and computer science.

The project provided an opportunity to apply theoretical concepts to a practical simulation while developing skills in:

* Java programming
* Object-oriented design
* Software architecture
* Graphical user interface development
* Physics-based modeling
* Mathematical modeling
* Team collaboration
* Version control with GitHub
