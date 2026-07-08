# Coordination-Aware Task Scheduling Optimizer

This project implements an optimization framework to address the coordination-aware task assignment and scheduling problem. The goal is to determine an optimal assignment of tasks to developers and a corresponding execution schedule that minimizes coordination risks, project makespan, and workload imbalance.

## Project Overview

The model structures the scheduling problem by defining system entities, parameters, decision variables, objective functions, and constraints.

### System Entities
*   **Tasks ($T$):** Units of work to be scheduled.
*   **Developers ($D$):** Resources for task assignment.
*   **Modules ($M$):** Associated with tasks and managed by teams.
*   **Teams ($\mathcal{T}$):** Groups managing modules [cite: 2].
*   **Dependencies ($P$):** Defined as acyclic ($P_{acyc}$) and cyclic ($P_{cyc}$) relationships.

### Parameters
*   **Fibonacci-based story points:** Relative effort scale.
*   **Developer profiles:** Skills, experience levels ($A, I, B$), and availability.
*   **Time adjustment factor ($ eta$):** Adjusts duration based on developer experience.

### Decision Variables
*   **Task assignments ($x_{ij}$):** Binary predicate for assignment.
*   **Timing ($s_i, f_i$):** Start and finish times for tasks.

### Optimization Objectives
*   **Minimize Coordination Risk:** Reduces risks based on sequential vs. parallel scheduling of dependent tasks.
*   **Minimize Makespan:** Minimizes the total project duration ($max(f_i)$).
*   **Minimize Workload Imbalance:** Minimizes the standard deviation of developer workloads.

### Constraints
*   **Assignment:** Each task assigned to exactly one developer.
*   **Skill matching:** Tasks assigned only to qualified developers.
*   **Team-Module ownership:** Developers only work on tasks in their team's modules.
*   **Availability:** Tasks scheduled within developer availability slots.
*   **Dependency Logic:** Enforces timing constraints for both acyclic and cyclic dependencies.