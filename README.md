# ![](https://github.com/aimacode/aima-java/blob/gh-pages/aima3e/images/aima3e.jpg)`aima-python` (Python 3.5) [![Build Status](https://travis-ci.org/aimacode/aima-python.svg?branch=master)](https://travis-ci.org/aimacode/aima-python)


Python code for the book *Artificial Intelligence: A Modern Approach.* We're loooking for one student sponsored by Google Summer of Code (GSoC) to work on this project; if you want to be that student, make some good contributions here (by looking throush the "Issues" and resolving some), and submit an application. (And we're always looking for solid contributors who are not affiliated with GSoC.)

## Structure of the Project

When complete, this project will have [Python 3.5](https://www.python.org/downloads/release/python-350/) code for all the pseudocode algorithms in the book. For each major topic, such as `logic`, we will have the following  files in the main branch:

- `logic.py`: Implementations of all the pseudocode algorithms, and necessary support functions/classes/data.
- `logic_test.py`: A lightweight test suite, using `assert` statements, designed for use with [`py.test`](http://pytest.org/latest/).
- `logic.ipynb`: A Jupyter notebook, with examples of usage. Does a `from logic import *` to get the code.

Until we get there, we will support a legacy branch, `aima3python2` (for the third edition of the textbook and for Python 2 code). To prepare code for the new master branch, the following two steps should be taken:

## Port to Python 3; Pythonic Idioms; py.test

- Check for common problems in [porting to Python 3](http://python3porting.com/problems.html), such as: `print` is now a function; `range` and `map` and other functions no longer produce `list`s; objects of different types can no longer be compared with `<`; strings are now Unicode; it would be nice to move `%` string formating to `.format`; there is a new `next` function for generators; integer division now returns a float; we can now use set literals.
- Replace old Lisp-based idioms with proper Python idioms. For example, we have many functions that were taken directly from Common Lisp, such as the `every` function: `every(callable, items)` returns true if every element of `items` is callable. This is good Lisp style, but good Python style would be to use `all` and a generator expression: `all(callable(f) for f in items)`. Eventually, fix all calls to these legacy Lisp functions and then remove the functions.
- Create a `_test.py` file, and define functions that use `assert` to make tests. Remove any old `doctest` tests.
In other words, replace the ">>> 2 + 2 \n 4"  in a docstring with "assert 2 + 2 == 4" in `filename_test.py`.

## New and Improved Algorithms

- Implement functions that were in the third edition of the book but were not yet implemented in the code. Check the [list of pseudocode algorithms (pdf)](http://aima.cs.berkeley.edu/algorithms.pdf) to see what's missing.
- As we finish chapters for the new fourth edition, we will share the new pseudocode, and describe what changes are necessary.

- Create a `.ipynb` notebook, and give examples of how to use the code.

# Style Guide

There are a few style rules that are unique to this project:

- The first rule is that the code should correspond directly to the pseudocode in the book. When possible this will be almost one-to-one, just allowing for the syntactic differences between Python and pseudocode, and for different library functions.
- Don't make a function more complicated than the pseudocode in the book, even if the complication would add a nice feature, or give an efficiency gain. Instead, remain faithful to the pseudocode, and if you must, add a new function (not in the book) with the added feature.
- I use functional programming (functions with no side effects) in many cases, but not exclusively (sometimes classes and/or functions with side effects are used). Let the book's pseudocode be the guide.

Beyond the above rules, we use [Pep 8](https://www.python.org/dev/peps/pep-0008), with a few minor exceptions:

- I'm not too worried about an occasional line longer than 79 characters.
- You don't need two spaces after a sentence-ending period.
- Strunk and White is [not a good guide for English](http://chronicle.com/article/50-Years-of-Stupid-Grammar/25497).
- I prefer more concise docstrings; I don't follow [Pep 257](https://www.python.org/dev/peps/pep-0257/).
- Not all constants have to be UPPERCASE.
- [Pep 484](https://www.python.org/dev/peps/pep-0484/) type annotations are allowed but not required. If your
  parameter name is already suggestive of the name of a type, such as `url` below, then i don't think the type annotation is useful.
  Return type annotations, such as `-> None` below, can be very useful.

        def retry(url: Url) -> None:

# Index of Code #

| **Fig** | **Page** | **Name (in book)** | **Code** |
|:--------|:---------|:-------------------|:---------|
| 2       |  32      | Environment        | [Environment](../master/agents.py) |
| 2.1     |  33      | Agent              | [Agent](../master/agents.py) |
| 2.3     |  34      | Table-Driven-Vacuum-Agent | [TableDrivenVacuumAgent](../master/agents.py) |
| 2.7     |  45      | Table-Driven-Agent | [TableDrivenAgent](../master/agents.py) |
| 2.8     |  46      | Reflex-Vacuum-Agent | [ReflexVacuumAgent](../master/agents.py) |
| 2.10    |  47      | Simple-Reflex-Agent | [SimpleReflexAgent](../master/agents.py) |
| 2.12    |  49      | Reflex-Agent-With-State | [ReflexAgentWithState](../master/agents.py) |
| 3.1     |  61      | Simple-Problem-Solving-Agent | [SimpleProblemSolvingAgent](../master/search.py) |
| 3       |  62      | Problem            | [Problem](../master/search.py) |
| 3.2     |  63      | Romania            | [romania](../master/search.py) |
| 3       |  69      | Node               | [Node](../master/search.py) |
| 3.7     |  70      | Tree-Search        | [tree\_search](../master/search.py) |
| 3       |  71      | Queue              | [Queue](../master/utils.py) |
| 3.9     |  72      | Tree-Search        | [tree\_search](../master/search.py) |
| 3.13    |  77      | Depth-Limited-Search | [depth\_limited\_search](../master/search.py) |
| 3.14    |  79      | Iterative-Deepening-Search | [iterative\_deepening\_search](../master/search.py) |
| 3.19    |  83      | Graph-Search       | [graph\_search](../master/search.py) |
| 4       |  95      | Best-First-Search  | [best\_first\_graph\_search](../master/search.py) |
| 4       |  97      | A`*`-Search        | [astar\_search](../master/search.py) |
| 4.5     | 102      | Recursive-Best-First-Search | [recursive\_best\_first\_search](../master/search.py) |
| 4.11    | 112      | Hill-Climbing      | [hill\_climbing](../master/search.py) |
| 4.14    | 116      | Simulated-Annealing | [simulated\_annealing](../master/search.py) |
| 4.17    | 119      | Genetic-Algorithm  | [genetic\_algorithm](../master/search.py) |
| 4.20    | 126      | Online-DFS-Agent   | [online\_dfs\_agent](../master/search.py) |
| 4.23    | 128      | LRTA`*`-Agent      | [lrta\_star\_agent](../master/search.py) |
| 5       | 137      | CSP                | [CSP](../master/csp.py) |
| 5.3     | 142      | Backtracking-Search | [backtracking\_search](../master/csp.py) |
| 5.7     | 146      | AC-3               | [AC3](../master/csp.py) |
| 5.8     | 151      | Min-Conflicts      | [min\_conflicts](../master/csp.py) |
| 6.3     | 166      | Minimax-Decision   | [minimax\_decision](../master/games.py) |
| 6.7     | 170      | Alpha-Beta-Search  | [alphabeta\_search](../master/games.py) |
| 7       | 195      | KB                 | [KB](../master/logic.py) |
| 7.1     | 196      | KB-Agent           | [KB\_Agent](../master/logic.py) |
| 7.7     | 205      | Propositional Logic Sentence | [Expr](../master/logic.py) |
| 7.10    | 209      | TT-Entails         | [tt\_entials](../master/logic.py) |
| 7       | 215      | Convert to CNF     | [to\_cnf](../master/logic.py) |
| 7.12    | 216      | PL-Resolution      | [pl\_resolution](../master/logic.py) |
| 7.14    | 219      | PL-FC-Entails?     | [pl\_fc\_resolution](../master/logic.py) |
| 7.16    | 222      | DPLL-Satisfiable?  | [dpll\_satisfiable](../master/logic.py) |
| 7.17    | 223      | WalkSAT            | [WalkSAT](../master/logic.py) |
| 7.19    | 226      | PL-Wumpus-Agent    | [PLWumpusAgent](../master/logic.py) |
| 9       | 273      | Subst              | [subst](../master/logic.py) |
| 9.1     | 278      | Unify              | [unify](../master/logic.py) |
| 9.3     | 282      | FOL-FC-Ask         | [fol\_fc\_ask](../master/logic.py) |
| 9.6     | 288      | FOL-BC-Ask         | [fol\_bc\_ask](../master/logic.py) |
| 9.14    | 307      | Otter              |          |
| 11.2    | 380      | Airport-problem    |          |
| 11.3    | 381      | Spare-Tire-Problem |          |
| 11.4    | 383      | Three-Block-Tower  |          |
| 11      | 390      | Partial-Order-Planner |          |
| 11.11   | 396      | Cake-Problem       |          |
| 11.13   | 399      | Graphplan          |          |
| 11.15   | 403      | SATPlan            |          |
| 12.1    | 418      | Job-Shop-Problem   |          |
| 12.3    | 421      | Job-Shop-Problem-With-Resources |          |
| 12.6    | 424      | House-Building-Problem |          |
| 12.10   | 435      | And-Or-Graph-Search | [and\_or\_graph\_search](../master/search.py)  |
| 12.22   | 449      | Continuous-POP-Agent |          |
| 12.23   | 450      | Doubles-tennis     |          |
| 13.1    | 466      | DT-Agent           | [DTAgent](../master/probability.py) |
| 13      | 469      | Discrete Probability Distribution | [DiscreteProbDist](../master/probability.py) |
| 13.4    | 477      | Enumerate-Joint-Ask | [enumerate\_joint\_ask](../master/probability.py) |
| 14.10   | 509      | Elimination-Ask    | [elimination\_ask](../master/probability.py) |
| 14.12   | 512      | Prior-Sample       | [prior\_sample](../master/probability.py) |
| 14.13   | 513      | Rejection-Sampling | [rejection\_sampling](../master/probability.py) |
| 14.14   | 515      | Likelihood-Weighting | [likelihood\_weighting](../master/probability.py) |
| 14.15   | 517      | MCMC-Ask           |          |
| 15.4    | 546      | Forward-Backward   | [forward\_backward](../master/probability.py) |
| 15.6    | 552      | Fixed-Lag-Smoothing | [fixed\_lag\_smoothing](../master/probability.py) |
| 15.15   | 566      | Particle-Filtering | [particle\_filtering](../master/probability.py) |
| 16.8    | 603      | Information-Gathering-Agent |          |
| 17.4    | 621      | Value-Iteration    | [value\_iteration](../master/mdp.py) |
| 17.7    | 624      | Policy-Iteration   | [policy\_iteration](../master/mdp.py) |
| 18.5    | 658      | Decision-Tree-Learning | [DecisionTreeLearner](../master/learning.py) |
| 18.10   | 667      | AdaBoost           | [AdaBoost](../master/learning.py) |
| 18.14   | 672      | Decision-List-Learning |          |
| 19.2    | 681      | Current-Best-Learning |          |
| 19.3    | 683      | Version-Space-Learning |          |
| 19.8    | 696      | Minimal-Consistent-Det |          |
| 19.12   | 702      | FOIL               |          |
| 20.21   | 742      | Perceptron-Learning | [PerceptronLearner](../master/learning.py) |
| 20.25   | 746      | Back-Prop-Learning |          |
| 21.2    | 768      | Passive-ADP-Agent  | [PassiveADPAgent](../master/rl.py) |
| 21.4    | 769      | Passive-TD-Agent   | [PassiveTDAgent](../master/rl.py) |
| 21.8    | 776      | Q-Learning-Agent   |          |
| 22.2    | 796      | Naive-Communicating-Agent |          |
| 22.7    | 801      | Chart-Parse        | [Chart](../master/nlp.py) |
| 23.1    | 837      | Viterbi-Segmentation | [viterbi\_segment](../master/text.py) |
| 24.21   | 892      | Align              |          |

# Choice of Programming Languages

Are we right to concentrate on Java and Python versions of the code? I think so; both languages are popular; Java is
fast enough for our purposes, and has reasonable type declarations (but can be verbose); Python is popular and has a very direct mapping to the pseudocode in the book (but lacks type declarations and can be slow). The [TIOBE Index](http://www.tiobe.com/tiobe_index) says the top five most popular languages are:

        Java, C, C++, C#, Python

So it might be reasonable to also support C++/C# at some point in the future. It might also be reasonable to support a language that combines the terse readability of Python with the type safety and speed of Java; perhaps Go or Julia. And finally, Javascript is the language of the browser; it would be nice to have code that runs in the browser, in Javascript or a variant such as Typescript.

There is also a `aima-lisp` project; in 1995 when we wrote the first edition of the book, Lisp was the right choice, but today it is less popular.

What languages are instructors recommending for their AI class? To get an approximate idea, I gave the query <tt>[norvig russell "Modern Approach"](https://www.google.com/webhp#q=russell%20norvig%20%22modern%20approach%22%20java)</tt> along with the names of various languages and looked at the estimated counts of results on
various dates. However, I don't have much confidence in these figures...

|Language  |2004  |2005  |2007  |2010  |2016  |
|--------  |----: |----: |----: |----: |----: |
|[none](http://www.google.com/search?q=norvig+russell+%22Modern+Approach%22)|8,080|20,100|75,200|150,000|132,000|
|[java](http://www.google.com/search?q=java+norvig+russell+%22Modern+Approach%22)|1,990|4,930|44,200|37,000|50,000|
|[c++](http://www.google.com/search?q=c%2B%2B+norvig+russell+%22Modern+Approach%22)|875|1,820|35,300|105,000|35,000|
|[lisp](http://www.google.com/search?q=lisp+norvig+russell+%22Modern+Approach%22)|844|974|30,100|19,000|14,000|
|[prolog](http://www.google.com/search?q=prolog+norvig+russell+%22Modern+Approach%22)|789|2,010|23,200|17,000|16,000|
|[python](http://www.google.com/search?q=python+norvig+russell+%22Modern+Approach%22)|785|1,240|18,400|11,000|12,000|