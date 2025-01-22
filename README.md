# Process Scheduling Algorithms Simulation

This repository provides an implementation of various **process scheduling algorithms** in C++. The program simulates the behavior of scheduling algorithms and generates performance statistics and timelines for process execution. It supports multiple scheduling strategies, including both preemptive and non-preemptive techniques.

---

## Table of Contents

1. [Features](#features)
2. [Supported Scheduling Algorithms](#supported-scheduling-algorithms)
3. [How to Use](#how-to-use)
4. [Input File Format](#input-file-format)
5. [Output Format](#output-format)
6. [Build and Run](#build-and-run)
7. [Code Structure](#code-structure)
8. [Contributing](#contributing)
9. [License](#license)

---

## Features

- Supports various scheduling algorithms.
- Provides visual execution timelines.
- Computes and displays statistics such as:
  - Finish time
  - Turnaround time
  - Normalized turnaround time
- Flexible configuration for quantum values (for algorithms like Round Robin and Feedback).
- Modular and extensible code.

---

## Supported Scheduling Algorithms

The following algorithms are implemented:

1. **First-Come, First-Serve (FCFS)**
2. **Round Robin (RR)**
3. **Shortest Process Next (SPN)**
4. **Shortest Remaining Time (SRT)**
5. **Highest Response Ratio Next (HRRN)**
6. **Feedback Queue (FB-1)**
7. **Feedback Queue with Incremental Quantum (FB-2i)**
8. **Aging**

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/process-scheduling-simulator.git
   cd process-scheduling-simulator
   ```

2. Prepare an input file following the format specified in the [Input File Format](#input-file-format) section.

3. Compile and run the program:
   ```bash
   g++ -std=c++17 -o scheduler main.cpp parser.cpp
   ./scheduler
   ```

4. The program will output either the execution timeline or the statistics, depending on the operation mode.

---

## Input File Format

The input file should describe the processes and their attributes. Example format:

```plaintext
<operation> <algorithm> <quantum>
<process_name> <arrival_time> <service_time>
...
```

### Example:

```plaintext
trace 2 4
P1 0 5
P2 2 3
P3 4 2
```

- **Operation**: `trace` for execution timeline or `stats` for performance statistics.
- **Algorithm**: Algorithm ID (1 to 8) as listed above.
- **Quantum**: Time quantum (only applicable for algorithms like Round Robin).
- **Process Details**: Each line specifies a process with its name, arrival time, and service time.

---

## Output Format

### Timeline (`trace` operation):

Visual representation of the process execution timeline.

Example:

```plaintext
0 1 2 3 4 5 6 7 8 9
---------------------------------------
P1   |* * * * *|           
P2       |. . * * *|      
P3               |. * *|  
---------------------------------------
```

### Statistics (`stats` operation):

Tabular representation of finish time, turnaround time, and normalized turnaround time.

Example:

```plaintext
FCFS
Process    |  P1  |  P2  |  P3  |
Arrival    |   0  |   2  |   4  |
Service    |   5  |   3  |   2  |
Finish     |   5  |   8  |  10  |
Turnaround |   5  |   6  |   6  |
NormTurn   |1.00  |2.00  |3.00  |
```

---

## Build and Run

1. Compile the program:
   ```bash
   g++ -std=c++17 -o scheduler main.cpp parser.cpp
   ```

2. Run the program:
   ```bash
   ./scheduler
   ```

---

## Code Structure

- **`main.cpp`**: Main entry point of the program.
- **`parser.h` and `parser.cpp`**: Handles input parsing and validation.
- **`algorithms.cpp`**: Implements the various scheduling algorithms.
- **`timeline.cpp`**: Handles timeline creation and visualization.

---

## Contributing

Contributions are welcome! If you want to add features or fix issues:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a pull request.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

