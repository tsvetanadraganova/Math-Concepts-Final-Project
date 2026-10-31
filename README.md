# The Mathematics Behind Route Optimization: Finding Efficient Delivery Routes with Python

## Project Overview

This project was developed as part of the **SoftUni Math Concepts for Developers** final exam.

The goal is to demonstrate how mathematical concepts and Python algorithms can be used to find efficient delivery routes.

The project considers a simplified delivery scenario with one warehouse and five delivery locations. A delivery vehicle must start at the warehouse, visit each delivery location exactly once, and return to the warehouse.

The main objective is to find the route with the shortest total distance.

Three different approaches are implemented and compared:

1. **Random Route**
2. **Nearest Neighbor**
3. **Brute Force**

The project focuses on mathematical understanding, algorithm implementation, and result comparison. It does not use Machine Learning or Data Science techniques.

## Mathematical Concepts

The project applies several mathematical concepts covered in the course.

### Coordinates and Vectors

The warehouse and delivery locations are represented as points in a two-dimensional coordinate system.

Vectors describe the displacement between two locations.

### Euclidean Distance

The distance between two points is calculated using the Euclidean distance formula:

$$
d(A,B) = \sqrt{(x_2-x_1)^2 + (y_2-y_1)^2}
$$

This formula is based on the Pythagorean theorem.

### Total Route Length

The total length of a delivery route is calculated by adding the distances between consecutive locations, including the return to the warehouse.

### Permutations and Factorials

Permutations represent the different possible orders in which delivery locations can be visited.

For five delivery locations, the number of possible visit sequences is:

$$
5! = 5 \times 4 \times 3 \times 2 \times 1 = 120
$$

The warehouse remains fixed as the starting and ending location.

### Mathematical Optimization

The optimization objective is to minimize the total route distance while ensuring that every delivery location is visited exactly once.

This is a simplified version of the **symmetric Travelling Salesperson Problem (TSP)**.

The project uses straight-line Euclidean distances rather than real road distances, traffic conditions, or travel times.

## Delivery Scenario

The project uses one warehouse and five delivery locations with fixed example coordinates.

| Location | X | Y |
|---|---:|---:|
| Warehouse (W) | 0 | 0 |
| Delivery A | 2 | 3 |
| Delivery B | 5 | 1 |
| Delivery C | 6 | 5 |
| Delivery D | 3 | 7 |
| Delivery E | 8 | 3 |

All routes start and end at warehouse W.

Distance values are expressed in coordinate distance units, not real-world kilometers.

## Implemented Algorithms

### 1. Random Route

The Random Route algorithm generates a random ordering of the five delivery locations.

Python's standard `random` library is used to select a valid permutation.

The algorithm then calculates the total distance of the generated route.

**Advantages:**
- Simple to understand and implement.
- Always produces a valid route when the delivery locations are correctly defined.
- Provides a baseline for comparing other algorithms.

**Limitations:**
- Does not guarantee a short route.
- Different random selections can produce different distances.

A fixed random seed is used in the final demonstration to make the example reproducible.

### 2. Nearest Neighbor

The Nearest Neighbor algorithm starts at the warehouse and repeatedly selects the closest unvisited delivery location.

When all locations have been visited, the vehicle returns to the warehouse.

**Advantages:**
- Easy to implement.
- Makes decisions using Euclidean distance.
- Can find an efficient route without evaluating every possible permutation.

**Limitations:**
- Makes locally optimal decisions.
- Does not guarantee the globally shortest route.

Nearest Neighbor is a greedy heuristic algorithm.

### 3. Brute Force

The Brute Force algorithm evaluates all 120 permutations of the five delivery locations.

For each permutation, it constructs a complete route, calculates its total distance, and compares the result with the shortest distance found so far.

**Advantages:**
- Evaluates every possible visit sequence.
- Guarantees a globally optimal result within the simplified mathematical model.

**Limitations:**
- The number of permutations grows factorially.
- Becomes computationally expensive as the number of delivery locations increases.

For the five delivery locations used in this project, evaluating all 120 permutations is manageable.

## Algorithm Comparison

The three algorithms were implemented and tested using the same warehouse and delivery coordinates.

### Route Length Results

| Algorithm | Total Distance |
|---|---:|
| Random Route — Single Example | 29.59 |
| Nearest Neighbor | 24.87 |
| Brute Force | **22.87** |

The Brute Force algorithm found the globally shortest route within the simplified model:

**W → A → D → C → E → B → W**

Exact distance: **22.867206090348603**

Rounded distance: **22.87 distance units**

Compared with the optimal route:

- The Random Route example is approximately **29.39% longer**.
- The Nearest Neighbor route is approximately **8.74% longer**.

These comparisons use the Brute Force result as the reference.

### Statistical Analysis of Random Routes

A single random route does not describe the full range of possible random outcomes.

To provide a more meaningful comparison, the project evaluates 100 randomly generated routes using a fixed seed.

| Statistic | Route Distance |
|---|---:|
| Number of random routes | 100 |
| Mean | 31.05 |
| Minimum | 22.87 |
| Maximum | 37.16 |

The statistical experiment uses a fixed seed of `42`, while the reproducible single Random Route demonstration uses `144`.

The mean, minimum, and maximum describe this particular sample of 100 randomly generated routes. Different random samples may produce different results.

This analysis uses basic descriptive statistics to support the algorithm comparison.

## Visualizations

The project includes five PNG images generated using Matplotlib.

| Image | Description |
|---|---|
| `example_delivery_route.png` | Example delivery route and location coordinates |
| `random_delivery_route.png` | Randomly generated delivery route |
| `nearest_neighbor_route.png` | Route generated by the Nearest Neighbor algorithm |
| `brute_force_route.png` | Globally optimal route found by Brute Force |
| `algorithm_comparison.png` | Comparison of the algorithm route distances |

All images are stored in the `images/` directory.

The visualizations are also presented and explained in the Jupyter Notebook.

## Technologies Used

- **Python** — mathematical calculations and algorithm implementations.
- **Jupyter Notebook** — code execution, mathematical explanations, and results.
- **Matplotlib** — route and comparison visualizations.
- **Python Standard Library** — including `math`, `itertools`, and `random`.
- **Visual Studio Code** — development environment.
- **Git and GitHub** — version control and project repository.

No Machine Learning frameworks are required.

## Project Structure

```text
Math-Concepts-Final-Project/
├── data/
├── images/
│   ├── example_delivery_route.png
│   ├── random_delivery_route.png
│   ├── nearest_neighbor_route.png
│   ├── brute_force_route.png
│   └── algorithm_comparison.png
├── notebooks/
│   └── route_optimization.ipynb
├── .gitignore
└── README.md
```

The `data/` directory is reserved for optional project data. The implemented example uses coordinates defined directly in the Notebook and does not require an external dataset.

## How to Run the Project

### Requirements

- Python 3
- Visual Studio Code with the Python and Jupyter extensions, or another Jupyter-compatible environment
- Jupyter support and Matplotlib installed in the selected Python environment

### Steps

1. Clone or download this GitHub repository.
2. Open the `Math-Concepts-Final-Project` folder in Visual Studio Code.
3. Open `notebooks/route_optimization.ipynb`.
4. Select a Python environment with the required packages installed.
5. Restart the Jupyter kernel and select **Run All** to execute the Notebook from beginning to end.
6. Review the mathematical explanations, algorithm outputs, and visualizations.

For an environment where the required packages are missing, they can be installed using:

```bash
python -m pip install notebook matplotlib
```

The Notebook uses the Python standard library for the main mathematical and algorithmic operations.

**Note:** Route image files are saved using paths relative to the Notebook's `notebooks/` directory. Run the Notebook in an environment that preserves this working-directory structure.

## Verification and Reproducibility

The project was tested by restarting the Jupyter kernel and executing the Notebook from beginning to end.

The final verification included:

- Successful execution of all 49 code cells.
- Consistent mathematical and numerical results.
- Evaluation of all 120 permutations by Brute Force.
- Validation of the generated routes.
- Comparison of algorithm distances.
- Reproducible random-route examples using fixed seeds.
- Verification of the five generated PNG visualizations.

The mathematical explanations and printed results were checked for consistency.

## Project Limitations

The project uses a simplified symmetric route optimization model.

It does not account for:

- Real road networks and one-way streets.
- Traffic and travel times.
- Vehicle capacity.
- Delivery time windows.
- Fuel consumption or transportation costs.
- Multiple warehouses or delivery vehicles.

These limitations keep the project focused on the mathematical concepts and algorithms studied in the course.

The results demonstrate route optimization using Euclidean distances and should not be interpreted as actual road-driving routes.

## Conclusion

The project demonstrates how mathematical concepts can be translated into practical Python algorithms for route optimization.

The Random Route algorithm provides a simple baseline but cannot guarantee an efficient result.

The Nearest Neighbor algorithm improves route selection by choosing the closest available destination at each step, although its local decisions do not guarantee the global optimum.

The Brute Force algorithm evaluates every possible route and identifies the globally shortest solution within the simplified model.

For this example, the shortest route has a total length of approximately **22.87 distance units**.

The comparison demonstrates the relationship between algorithm simplicity, solution quality, and computational complexity.

## References

The mathematical explanations and implementations are supported by the SoftUni Math Concepts for Developers course materials and the official Python documentation.

The Jupyter Notebook contains the project's references, including relevant materials on high-school mathematics, linear algebra, probability and combinatorics, statistics, and the Python standard library.

## Author

**Tsvetana Draganova**

SoftUni — Math Concepts for Developers

Final Exam Project — Algorithm Implementation and Analysis
