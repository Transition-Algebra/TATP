# TATP

## Using TATP

The tool can loaded into Maude by executing `maude -no-banner -allow-files run-tatp.maude` from the directory `src`.

A few sample specifications can be found in the directory `src/test`. They can be loaded into the tool using the command `load test/file.ta`.

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
- Axioms of the form **ax L = R**, **ax L = R if COND**
	 **label: ID** for indica