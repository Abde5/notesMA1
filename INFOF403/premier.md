#Practical information
- Prof: Geeraerts
- Evaluation:
  - 12 points written exam
  - 8 points project $\to$ write a compiler (3 parts) [LLVM]
    - scanner
    - parser
    - code generation


# Introduction

Two parts: **Language theory** and **Compilers**.

## Language theory

 **DEFINITION:** An alphabet $\Sigma$ is a *finite* set of symbols/letters. For example, for computers: $\Sigma=\{0,1\}$. For a C source code it could be $\Sigma=\{a,...,z,A,...,Z,0,...,9,-\}$.

 **DEFINITION:** A word is a *finite* sequence of letters from an alphabet $\Sigma$.

 **DEFINITION:** A language is a set of words.

Examples of languages:
 - set of binary words that end with a "1" $\to\{1,11,101,111,...\}$. This can be represented as $(1+0)^*1$
 - $L_{()}$ = set of all words which are well-parenthesised ($\Sigma=\{(,)\}$)
    - Example: good: $(())()$ bad: )(()*

 This language can be checked with a counter, we begin from the left and for each opening parenthesis we increment the counter, and for the closing ones, decrement it. If we go below 0, then we are closing more parenthesis than we're opening, so it's not good.

 More examples:
  - $L_c$ = set of all syntactically correct c programs.
  - $L_{cterm}$ = set of all syntactically correct c programs that always terminate.
  In those examples, a word is a program.


## Compilers

A compler has 2 big phases. The **Analysis** and **Synthesis**. The analysis phase takes a source code in input, the output of the analysis goes to the synthesis and the output of the synthesis is the target code (generally machine code).

The output of the analysis is actually a structured representation of the source code. So all the syntax errors will be caught at the analysis phase.

During the analysis there are some processus:
  - **Scanning** = splitting the input code into *tokens*.
    For exemple:

    ```c
    int f (int j) {
      int i = j;
      return i + 1;
    }
    ```
    Each set of characters are tokens (`int`,`return`, `j` are tokens). This analysis is *local*, so they just read tokens, there will be no errors if there are syntax errors.
    In addition to recognize words we need regular expressions and finite automata.

    The scanner has to have a data structure to remember whether two different tokens have the same identifier (the variable `i` appears twice in the example before). This data structure store all the identifiers of the program. The data structure stocks the identifier of the token and the index of the order in which the token is recognized. It has this form:


    | index        | name  |
    | ----------- | ---- |
    | 0 | i |
    | 1 | j |

  - **Parser** = global analysis (checks the syntax of the code). It captures the    syntax errors and produces an abstract syntax tree. For this expression `3 + 4 * 5` the syntax tree that represents it is in Figure 1:  

    ![Figure 1](http://www.pling.org.uk/cs/lsaimg/parsetreetosyntaxtree.png)

    At the left we have a more precise tree. We also note as `id` the identifiers used in the expression. In this phase we use grammar to describe the syntax and a *pushdown* automata (stack) to recognize the structure. We can then represent the whole structure of the program in a single tree.

  - **Semantic analysis**
      - We have a *scoping analysis*, to check if we are using a variable in the right scope.
      - *Type checking*, to check if at each operation we're using the same value type.
      - *Control flow check*, if the "gotos" or flow statements are logical.
