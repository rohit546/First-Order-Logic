# First-Order-Logic

Task1:
Resolution with Refutation
Propositional logic, also known as sentential logic or propositional calculus, is a branch of
formal logic that deals with propositions, which are statements that can either be true or false
but not both. Propositional logic studies how these propositions can be combined using
logical operators to form more complex statements.
A proof system of proposition logic can be established as follows for example. Use the same
coding environment used in previous AI Lab 11 and implement the following examples.
Conversion to CNF:
1. Eliminate arrows (implications)
A → B = ¬A ∨ B
2. Drive in negations using de Morgan’s Laws, which are given below
¬(A ∨ B) = (¬A ∧ ¬B)
¬(A ∧ B) = (¬A ∨ ¬B)

3. Distribute OR over AND
A ∨ (B ∧ C) = (A ∨ B) ∧ (A ∨ C)

Example of CNF conversion:
(A ∨ B) → (C → D)
1. ¬(A ∨ B) ∨ (¬C ∨ D)
2. (¬A ∧ ¬B) ∨ (¬C ∨ D)
3. (¬A ∨ ¬C ∨ D) ∧ (¬B ∨ ¬C ∨ D)

Resolution by Refutation:
Now, we will look at a proof strategy call resolution refutation. The steps for proving a
statement using resolution refutation are:
• Write all sentences in CNF
• Negate the desired conclusion
• Apply the resolution rule until you derive a contradiction or cannot apply the rule
anymore.
• If we derive a contradiction, then the conclusion follows from the given axioms
• If we cannot apply anymore, then the conclusion cannot be proved from the given axioms.
Resolution refutation example 1:

![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/f0f8997b-f99d-41b2-87da-2e167cc3655c)


Resolution refutation example 2:
1. (A → B) → B
2. A → C
3. ¬C → ¬B
Prove C
Convert to CNF:
1. (A → B) → B


= (¬A ∨ B) → B
= ¬(¬A ∨ B) ∨ B
= (A ∧ ¬B) ∨ B
= (A ∨ B) ∧ (¬B ∨ B)
= (A ∨ B)
2. A → B = ¬A ∨ C
3. ¬C → ¬B = C ∨ ¬B
Proof:
![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/109d7c94-bb8f-4c8c-8608-0dc284810e61)


Task 2:
First-order logic (FOL), also known as first-order predicate logic or predicate calculus, is an extension
of propositional logic that allows for the representation of more complex relationships and
quantification over variables. In FOL, statements are made about objects and their properties, and
relationships between objects are expressed using predicates and quantifiers.
First-Order Logic:
1. Syntax:
▪ Constants: The constants represent specific object in the domain (e.g., “Alice”, “Bob”).
Variables: The variables represent placeholders for the object (e.g., “x”, “y”).
▪ Predicates: The predicates represent properties or relationships between objects (e.g., “Loves (x,
y)”.
▪ Quantifiers: The quantifiers specify the scope of variables (e.g. “For all x”, “There exists y”).
▪ Connectives: The logical connectives such as ∧ (AND), ∨ (OR), ¬ (NOT), → (IMPLIES), ↔ (IF
AND ONLY IF)

Semantics:
▪ Predicates are interpreted as relations over objects in the domain.
▪ Quantifiers specify the scope over which variable range.
▪ A Sentence is FOL is true or false in a given interpretation (model) and assignment of objects to
constants and variables.

Examples:
▪ ∀x Loves (x, Chocolates): Everyone loves chocolate.
▪ ∃y Parents (Alice, y): Alice has a parent.
▪ ∀x ∃y Parent (x, y): Everyone has a parent.
▪ ¬(∀x Students (x) → Smart (x)): Not all students are smart
Example Solved:
If either C173 or C220 is required for ACS course, then all students will take computer science. C173
and C240 are required. Prove that all students will take computer science.
P1. (C173 OR CS) → ACS
P2. C173
P3. C240
Prove: ACS
We can have the following by employing the capabilities of logic library provided by AIMA
repository.

![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/6e3f8e0e-416d-41d1-a00a-e5055528f6e9)

Example FOL:
Consider the following knowledge base:
1. All humans are mortal.
2. Socrates is a human.
Prove, therefore, Socrates is mortal


![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/daf50563-a99b-460b-8296-8cd14b64e472)

First-Order Logic: Assertions and Queries:
Sentences can be added to a knowledge base using TELL, exactly as in propositional logic. Such
sentences are called assertions. For example, we can assert that John is a king, Richard is a person, and
all kings are persons:
TELL(KB, King(John))
TELL(KB, Person(Richard))
TELL(KB, ∀x King(x) ⇒ Person(x))
We can ask questions of the knowledge base using ASK. For example,
ASK(KB, King(John))
returns true.
Questions asked with ASK are called queries or goals. Generally speaking, any query that is logically
entailed by the knowledge base should be answered affirmatively. For example, given the three
assertions above, the query
ASK(KB, Person(John))
should also return true. We can ask quantified queries, such as
ASK(KB, ∃x Person(x))
The answer is true.

![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/b377b311-afe4-4dc2-b00d-579beb47a43f)

Task 3: Proof with FOL
The law says that it is a crime for an American to sell weapons to hostile nations. The country Nono,
an enemy of America, has some missiles, and all of its missiles were sold to it by Colonel West, who
is American.
Perform the following tasks with by gaining the tutorial above mentioned.
1. Define the predicates American, Hostile, Sell, Missiles, Colonel West, and Nono using expr.
2. Create a first-order logic knowledge base (FolKB) and add the premises to it using the tell method.
3. Define the goal statement using expr.
4. Use the prove method of the knowledge base to attempt to prove the goal using resolution.
5. Proof object contains the resolution proof if the goal is proven, or None if it cannot be proven.
6. Print the proof, if available, and check if the goal is proven.
Apply the resolution rules to find the solution to this problem.
NOTE: Consider Section 7.4 of your course book for understanding and for Simulation purpose you
may use the following link. https://thiagodnf.github.io/wumpus-world-simulator/


Task 4:
Propositiona vs. Frist-Order Inference
One way to do first-order inference is to convert the first-order knowledge base to propositional logic
and use propositional inference, which we already know how to do. A first step is eliminating
universal quantifiers. For example, suppose our knowledge base contains the standard folkloric axiom
that all greedy kings are evil:
∀x King(x) ∧ Greedy(x) ⇒ Evil(x).
From that we can infer any of the following sentences:
King(John) ∧ Greedy(John) ⇒ Evil(John)
King(Richard) ∧ Greedy(Richard) ⇒ Evil(Richard)
King(Father(John)) ∧ Greedy(Father(John)) ⇒ Evil(Father(John))

Apply the given inference to query the knowledge base to answer the questions by employing First-
Order KB the capabilities of logic library of AIMA repository

![image](https://github.com/rohit546/First-Order-Logic/assets/100420859/40fcab62-6586-4e80-b0b3-6e3ef3ccbfc1)



