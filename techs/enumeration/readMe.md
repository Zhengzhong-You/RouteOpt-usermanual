# Enumeration Tree Writing

The Enumeration Tree Writing in RouteOpt is a two-stage approach designed for solving extremely challenging instances
by parallelizing the solution process. Here's an overview of how it works:

### 1. Writing Out Enumeration Trees

- **Activation**:
  To activate the enumeration tree writing process, uncomment the following line in ```techniqueControl.hpp```:
  ```cpp
  //#define WRITE_ENUMERATION_TREES
  ```

- **Differences from Default Solver**:
    1. **Node Selection Rule**: Shifts to a depth-first strategy, primarily to save memory.
    2. **Node Inspection Post-Enumeration**: Even after successful enumeration of a node, we continue inspecting it
       until a 'tail off' in cutting occurs. At this point, the node is written out.

- **Output Folders**:
  The process results in the creation of two folders:
    - `EnuTree` (`#define TREE_FOLDER std::string("EnuTree")`): Stores enumeration tree files, each recording:
        - Node information (refer to the 'main information' part in the output section).
        - Mathematical form of cuts (not the specific coefficients).
        - Index of columns in `EnuColPool` (all tree files share a single column pool, to conserve memory).

    - `EnuColPool` (`#define COL_POOL_FOLDER std::string("EnuColPool")`): Stores the column pool information in a single
      file, which includes the sequence information of all routes (columns).

### 2. Reading Enumeration Trees

- **Activation**:
  To enable the reading of specific enumeration trees, uncomment this line:
  ```cpp
  //#define READ_ENUMERATION_TREES
  ```
  Note: `READ_ENUMERATION_TREES` and `WRITE_ENUMERATION_TREES` cannot be activated simultaneously.

- **Functionality**:
  This stage involves reading a specific enumeration tree and then solving it. As the labeling process is not required,
  the memory typically allocated for labeling isn’t used. Consequently, the memory requirement for this job should be
  significantly lower than a regular job.

