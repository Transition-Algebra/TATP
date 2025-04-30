# TATP

## Using TATP

The tool can loaded into Maude by executing `maude -no-banner -allow-files run-tatp.maude` from the directory `src`.

A few sample specifications can be found in the directory `examples`. They can be loaded into the tool using the command `load ../examples/file.ta`.

## Syntax

TATP uses a syntax inspired by [Maude](https://maude.cs.illinois.edu/wiki/The_Maude_System).

Specifications start with **spec NAME is**, where **NAME** is the specification name, and end with **endspec**. They contain
- Sort declarations, with syntax **sort(s) SORT-LIST .**, where **SORT-LIST** is a comma-separated list of sort identifiers.
- Operator declarations, with syntax **op(s) OP-NAMES : ARITY -> COARITY [attributes] .**, where:
	- **OP-NAMES** is a comma-separated list of operator identifiers. In these identifieres underscores are used as placeholders for mixfix syntax.
	- **ARITY** is a whitespace-separated list of sort identifiers. Note that constants require the use of **()** as arity.
	- **COARITY** is the result sort.
	- **[attributes]** is an optional list of equational attributes. Attributes include **assoc** for associativity, **comm** for commutativity, and **id: TERM** for indicating that **TERM** is the identity of the operator.
- Variable declarations, of the form **var(s) VAR-LIST : SORT-NAME .**, where **VAR-LIST** is a comma separated list of variable identifiers and **SORT-NAME** is the sort of the variables.
- Axioms of the form **ax L = R .**, **ax L = R if COND .**, **ax L = A > R [attributes] .**, and **ax L = A > R if COND [attributes] .**, where:
	- **L** and **R** are terms, the left-hand and the right-hand sides of the sentence, respectively.
	- **COND** is the condition, which consists of a list of equations and transitions put together by means of the **and** operator.
	- **A** is an action. Besides the operators defined by the user, actions support composition (**;**), non-deterministic choice (**+**), and Kleene star (**\***). Action are required to be enclosed in parentheses.
	- **[attributes]** is an optional list of attributes. Attributes include **label: ID** for indicating the axiom label **ID**.

## Commands

TATP supports the following commands:
- **load MOD**, to load the module **MOD**.
- **check SEN**, to check whether the clause **SEN** holds by using narrowing
- **echeck SEN using (LBLS)**, to check whether the clause **SEN** holds by using narrowing. The search is guided by the label list **LBLS**. Besides the labels defined by the user, the following ones are available: (i) **comp** for composition (**;**), (ii) **choice** for non-deterministic choice (**+**), and (iii) **star** for Kleene star (**\***).
- **set narrowing bound BND**, to set the maximum depth used in narrowing when using **check** or **echeck** to **BND**. The special value **infinity** can be used to express that it is unbounded.
- **set unification bound BND**, to set the maximum depth used in unification **check** or **echeck** to **BND**. The special value **infinity** can be used to express that it is unbounded.
- **reduce SEN**, to check whether the clause **SEN** holds by using reduction.
- **set condition bound BND**, to set the maximum depth used for conditions when using **reduce** to **BND**. The special value **infinity** can be used to express that it is unbounded.
- **set rewrite bound BND**, to set the maximum number of steps when using **reduce** to **BND**. The special value **infinity** can be used to express that it is unbounded.
- **eof**, which stands for *end of file*. The text after **eof** will not be considered by the tool.
- **quit**, to exit the system.


