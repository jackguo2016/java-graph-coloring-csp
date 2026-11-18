# Advanced Graph Coloring Solver: A CSP Approach with AC-3, MRV, and LCV Heuristics

## Project Overview
This Java coursework project searches for a coloring that uses a fixed number of colors and gives adjacent vertices different colors. The color budget comes from the input file. The code explores backtracking with AC-3 propagation, minimum remaining values (MRV), and a color-ordering heuristic.

## Key Components
1. **Node Class**: 
   - Represents graph vertices with adjacency information.
   - Manages color assignments and available color choices.

2. **Main Class**:
   - Implements core CSP solving algorithms:
     - AC-3 (Arc Consistency Algorithm #3) for constraint propagation
     - MRV (Minimum Remaining Values) for variable ordering
     - LCV (Least Constraining Value) for value selection
   - Handles graph construction from input files
   - Orchestrates the overall solving process

## Advanced Algorithmic Techniques
1. **AC-3 Algorithm**: 
   - Enhances efficiency by pre-processing and dynamically reducing the domain of variables.
   - Traverses the entire graph to minimize the color options for subsequent nodes.

2. **MRV Heuristic**: 
   - Intelligently selects the next node to color by identifying the uncolored node with the least remaining color options.
   - Optimizes the search process by tackling the most constrained variables first.

3. **LCV Heuristic**: 
   - Prioritizes color selection based on usage frequency.
   - Chooses colors that are most used, potentially leaving more options for future assignments.

4. **Backtracking Search**: 
   - Implements a sophisticated backtracking algorithm that leverages AC-3, MRV, and LCV for pruning and guiding the search process.

## Implementation Details
- **Graph Representation**: Utilizes an adjacency list structure for efficient neighbor access and memory usage.
- **Dynamic Color Domain**: Each node maintains a list of available colors, dynamically updated through constraint propagation.
- **Extensible Design**: The modular structure allows for easy integration of additional CSP techniques or problem-specific heuristics.

## Usage Instructions

The program reads [`src/test4.txt`](src/test4.txt) by default. The file starts with header comments and a color budget such as `colors = 4`, followed by an edge list such as `0,1`. Use JDK 9 or later and run these commands from the repository root. The export flag is needed because the source imports a JDK-internal package.

```bash
mkdir -p build
javac -encoding UTF-8 --add-exports jdk.compiler/com.sun.tools.javac.util=ALL-UNNAMED -d build src/Main.java src/Node.java
java -cp build Main
```

The input path is set in [`src/Main.java`](src/Main.java). The program has no input-path argument. It prints the nodes and then reports a coloring or that its search found none. The bundled `test4.txt` run ends with `There is no solution for this graph input.` Earlier prototypes are in [`CSPZiyan`](https://github.com/jackguo2016/CSPZiyan) and [`CSPZiyan1`](https://github.com/jackguo2016/CSPZiyan1).

## Testing and Validation
- Comprehensive test cases provided in `test#.txt` files.
- The JUnit 5 tests in `MainTest.java` and `NodeTest.java` cover lookup helpers and node initialization.

## Performance Analysis
The integration of AC-3, MRV, and LCV heuristics significantly enhances the solver's efficiency:
- AC-3 reduces the search space by eliminating inconsistent values early.
- MRV minimizes branching factor in the search tree.
- LCV maximizes future solving flexibility.

The repository includes example graphs. It does not contain a performance benchmark.

## Future Enhancements
- Implementation of additional CSP techniques such as forward checking or conflict-directed backjumping.
- Parallelization of the solving process for improved performance on large-scale graphs.
- Development of a graphical user interface for visual representation of the coloring process.

## Author
Ziyan

## Academic References
1. Mackworth, A. K. (1977). Consistency in networks of relations. Artificial Intelligence, 8(1), 99-118.
2. Russell, S. J., & Norvig, P. (2010). Artificial Intelligence: A Modern Approach (3rd ed.). Pearson Education.
3. Kumar, V. (1992). Algorithms for constraint-satisfaction problems: A survey. AI Magazine, 13(1), 32-44.


CSP.AC3 problem:

In this project I have two main java class: Node and Main.

In Node class, I have an array call neb to store all neighbor nodes. and 3 variables representing the information of this node.

In Main class, Most of the work is done here, which mainly includes the main algorithms for solving CSP, AC3, MRV, LCV. The AC3 here is to improve the project by traversing the whole graph and reducing the selectable colors of the subsequent nodes. overall operating speed. MRV is Find the next coloring point in the graph, (uncolored) find the next point with the least alternative color to color, that is, to find the suitable variable forward. LCV is to decide which color should be selected among the alternative colors, the strategy here is to choose the color that is used the most.

I also have all the test case prove by professor in the test#.txt files. to run those test file just need simply change the file name at Main.java line 19(BufferedReader in = new BufferedReader(new FileReader("src/test2.txt"));//  <--------- change here to test different test case)

这个项目是一个针对图着色问题的求解器，采用了约束满足问题（CSP）的方法。开发者使用Java语言实现了几种常见的CSP技术，包括AC-3（弧一致性算法）、MRV（最小剩余值）和LCV（最少约束值）启发式方法。
项目的核心结构包括两个主要类：Node类用于表示图中的节点，Main类则包含了主要的求解算法。AC-3算法被用来预处理和动态减少可选颜色，MRV用于选择下一个要着色的节点，而LCV则用于颜色选择策略。这些方法与回溯搜索相结合，构成了求解器的主体。
代码组织相对简洁，主要功能都集中在Main类中实现。开发者还编写了一些基本的单元测试，以验证关键函数的正确性。项目包含了多个测试用例，用于检验求解器在不同输入下的表现。
虽然这个实现涵盖了CSP的一些基本技术，但仍有改进空间。例如，可以考虑引入更多高级的CSP方法，或者优化大规模图的处理效率。总的来说，这个项目展示了CSP技术在图着色问题上的基本应用，为理解这类算法在实际问题中的运用提供了一个具体示例

## Project history

Former repository name: `CS6511_AI_Project2`. This repository preserves the original coursework and its development history.
