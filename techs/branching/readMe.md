# Branching Strategies

In RouteOpt, our branching techniques are primarily controlled through settings in `techniqueControl.hpp`. These
settings dictate how branching candidates are selected and processed.

### Branch Candidates Type

Controlled by:

```cpp
#define BRANCH_CANDIDATES_TYPE 2
/**
* 1. Default: Choose 3 out of 100 candidates, then 1 out of 15
* 2. ML (Machine Learning): Choose 15 out of 100 for ML phase 2 testing, then 2 for heuristic
* 3. 3PB: Choose 2 out of 100 for heuristic
*/
```

### Master Valve for ML

To enable ML-based branching, uncomment:

```cpp
#define MASTER_VALVE_ML
```

Under `MASTER_VALVE_ML`, there are four ML states:

```cpp
#define ML_STATE 4
/**
* 1. Generate phase 1 training data
* 2. Generate phase 2 training data
* 3. Use the model
* 4. Use the model in phase 3 with \hat \theta changing dynamically
*/
```

### Settings

Controlled by:

```cpp
#define SETTING 1
/**
* 1. Default: All functions work
* 2. Forbid enumeration, cutting at non-root, and rollback
*/
```

Our
paper [Two-Stage Learning to Branch in Branch-Price-and-Cut Algorithms for Solving Vehicle Routing Problems Exactly](https://www.researchgate.net/publication/374553305_Two-Stage_Learning_to_Branch_in_Branch-Price-and-Cut_Algorithms_for_Solving_Vehicle_Routing_Problems_Exactly)
introduces the 3PB method, the 2LBB method, and the best k method, with a comparative analysis under settings 1 and 2:

- **Setting 1 (Default Solver)**: Enables both cutting and enumeration.
- **Setting 2**: Disables cutting, enumeration, and rollback.

### Detailed Branching Parameters

The specific parameters for branching are set in `Config.cpp`:

```cpp
int Config::ML_BranchPhase0 = 100;
int Config::BranPhase1 = branchValue({100, 15, 100});
int Config::BranPhase2 = branchValue({3, 2, 2});
int Config::BranPhase1InEnu = branchValue({15, 15, 100});
int Config::BranPhase2InEnu = branchValue({2, 2, 2});
```

### Choosing Branching Type

To activate the 2LBB method, change `BRANCH_CANDIDATES_TYPE` to 2 and uncomment `#define MASTER_VALVE_ML`.

### ML State Options

1. **Generate Stage 1 Training Data**: Prepares the initial training dataset.
2. **Generate Stage 2 Training Data**: Prepares the secondary training dataset.
3. **Use the Model**: Incorporate the trained ML model in branching decisions.
4. **Use the Model with ``best k`` Procedure**: Utilizes the model in conjunction with the ``best k`` procedure, currently
   exclusive to 2LBB.
