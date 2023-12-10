# Outputs

The level of detail in the outputs of RouteOpt is controlled by the `VERBOSE_MODE` parameter in `techniqueControl.hpp`,
similar to other parameters that control the techniques.

```cpp
#define VERBOSE_MODE 2
/**
 * 1. All possible output logs.
 * 2. Highly reduced output log for streamlined information.
 */
```

Currently, we only report outputs in `VERBOSE_MODE 2`. This mode provides a summarized overview of the information
related to the current node in the branch and bound tree. The main components of this output include:

**Node Information:**

```plaintext
nd_ind= 2  nd_col= 2660  nd_val= 30859.9  nd_dep= 1  et= 127.689  lb= 30848  ub= 30972  sub_nd_rmn= 0  ColPool= 1884494
true(92,113)
```

- `nd_ind`: Node index in the branch and bound tree.
- `nd_col`: Number of columns in the current node.
- `nd_val`: Local lower bound of the current node.
- `nd_dep`: Depth of the current node in the branch and bound tree.
- `et`: Elapsed time from the beginning of the solution process.
- `lb`: Global lower bound of the current node.
- `ub`: Global upper bound of the current node.
- `sub_nd_rmn`: Number of remaining nodes in the branch and bound tree.
- `ColPool`: The size of the column pool at the current node.
- `true(92,113)`: Branching decision made at the current node (e.g., must use edge (92, 113)).

**Column Generation Statistics:**

```plaintext
ncol= 6236  ncstr= 200  et= 6.53  lpval= 30492.89  ub= 30972.00
```

- `ncol`: Number of columns after the current round of column generation.
- `ncstr`: Number of constraints after this round.
- `lpval`: Current LP value.

**Cutting Part Analysis:**

```plaintext
rccs= 28 | r1cs= 777 | num_row= 1005
```

- `rccs`: Number of rounded capacity cuts. These are strengthened in the enumeration phase.
- `r1cs`: Number of limited-memory rank-1 cuts. These become full rank-1 cuts in the enumeration phase.
- `num_row`: Number of rows in the current LP.

**Branching Part Details:**

```plaintext
eps= 44.8623 average_t= 0.224311 t_for_one_lp= 0.224311
```

- `eps`: Elapsed time for making a branching decision (applicable if 'best k' technique is enabled).
- `average_t`: Average time for solving one LP (applicable if 'best k' technique is enabled).
- `t_for_one_lp`: Time taken for solving one LP in this branching decision (applicable if 'best k' technique is
  enabled).

**Branching Evaluation:**

```plaintext
Evaluate on ( 92 , 113 )...
ldf= 16.0199  rdf= 5.07102  pd= 81.2373
```

- Evaluating the branching variable (92, 113).
- `ldf`: Enhancement of the LP value between the left node and the parent node.
- `rdf`: Enhancement of the LP value between the right node and the parent node.

**Final Branching Decision:**

```plaintext
brc= ( 98 , 145 )
```

- `brc`: Final branching decision made.

**Enumeration Part Analysis:**

```plaintext
enumeration must be performed!
num_routes_now= 1884494
```

- Signifying the successful start of the enumeration phase.
- `num_routes_now`: Number of routes enumerated.

```plaintext
after clean non-ele routes lpval= 30860.6
after recover rank1c lpval= 30861.7
enumeration time= 12.237 and succeed!
```

- Post enumeration phase, non-elementary routes are removed from the LP.
- Rank-1 cuts are restored to their full form.
- Enumeration time and success status are reported.

```plaintext
nd_ind= 4  nd_col= 2595  nd_val= 30867  nd_dep= 2  et= 210.831  lb= 30848  ub= 30972  sub_nd_rmn= 1  ColPool= 514884
true(92,113) true(7,194) 
```

- Details of node index, columns, values, and depth