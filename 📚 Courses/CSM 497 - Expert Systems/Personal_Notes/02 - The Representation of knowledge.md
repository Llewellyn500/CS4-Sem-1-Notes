---
date: 2025-02-23
course: CSM 497 - Expert Systems
tags:
  - personal
  - study
  - CSM497
---

## **Overview**

#### **What is the study of logic**

- Logic is the study if making inferences given a set of facts and information to reach a true conclusion

**Why Logic Matters for Expert Systems:**

- Expert systems must separate the actual meanings of words (semantics) from the process of logical reasoning.
- The goal is to reach valid conclusions based solely on facts by using formal rules of inference.

**Knowledge vs. Expert Systems:**

- **Knowledge Representation:** How information (data, facts, heuristics) is organized to enable reasoning.
- Expert systems are built around rules of logic (inferences) that drive their decision-making.
- The way knowledge is represented affects the system’s development, efficiency, speed, and ease of maintenance.

-  The way knowledge is structured and stored (basically knowledge represented) is key to the success/effectiveness of an expert system

- **An argument** refers to the formal way facts and rules of inferences are used to reach valid conclusion

- The process of reaching valid conclusion is referred to as **logical reasoning**

- Heuristics refers to using experience to solve problems using precedent.
- What are precedents?
	- They are old cases stored in an expert system for references.
- An expert system have many, hundreds/ thousands of micro-precedents in them 

#### **Epistemology**

- **Epistemology:**
    - The formal study of knowledge, its structure, and origins.
    
- **Categories:**
	- **Philosophy**
    - **A Priori Knowledge:**
	    - *"That which precedes"*
        - Knowledge that exists independently of sensory experience; universally true and self-evident.
        - Its based on Logic, reasoning and definition
    - **A Posteriori Knowledge:**
	    - *"That which follows"*
        - Knowledge derived from sensory experience; can be updated or challenged with new evidence.
    - **Procedural Knowledge:**
        - “Knowing how” to do something (e.g., riding a bicycle, fixing a watch).
    - **Declarative Knowledge:**
        - “Knowing that” something is true or false (e.g., factual statements).
    - **Tacit Knowledge:**
        - Unconscious or hard-to-articulate knowledge (e.g., how to walk or breathe).

#### **Knowledge in Rule-Based Systems**

- **Rule-Based Hierarchies:**
    - Knowledge is often structured as a hierarchy where rules (if–then statements) are activated by facts.
    - Activated rules lead to new facts or conclusions, forming the basis of inferencing in expert systems.
    - Knowledge is a hierarchy of
	    - Data - raw fact
	    - Information - processed data
	    - knowledge - Rules activated by facts
	    - Inference - Logical conclusions drawn from knowledge

- **Expert Systems vs. Human Reasoning:**
    - Expert systems perform inference (applying formal rules to reach conclusions).
    - Humans, however, “reason” in a less structured and more intuitive manner.

- **Expert Systems vs. Artificial Neural Systems (ANS):**
    - **Expert Systems:** Use explicit rules and logical inference.
    - **ANS:** Identify patterns in data without explicitly drawing inferences in a symbolic manner.

- **Metaknowledge and Ontologies:**
    - **Metaknowledge:** Knowledge about knowledge, including how knowledge is structured within a domain.
    - An **ontology** defines the concepts and relationships in a problem domain.


#### **The Pyramid of Knowledge**

![[Pasted image 20250223212429.png]]

#### **How knowledge is represented**

1. Parse Trees
2. Semantic Nets
3. Frames
4. Scripts
5. Logic
6. Conceptual graph

#### **Parse Tree Of A Sentence**

![[Pasted image 20250223213235.png]]

#### **Semantic Nets**

- Represent knowledge as nodes (objects/concepts) connected by arcs (relationships).
- Common links include IS-A (instance) and A-KIND-OF (generic relationships).
- **Limitation:** They require rigorous definitions and can lead to a combinatorial explosion in search.

![[Pasted image 20250223213807.png]]


#### **Prolog**
In prolog, predicate expressions consist of the predicate name, followed by argument, enclosed in parentheses, separated by comma.
	eg. mother (becky, heather) means that becky is the mother of heather
![[Pasted image 20250223214610.png]]

#### **Schemata and Frames**

- **Frames:** Data structures that group related knowledge about a stereotypical object (slots and fillers).
- They are more complex than semantic nets and allow for default information and more structured representation.
- **Schemata:** More ordered collections of knowledge that go beyond the two-dimensional nature of semantic nets.

#### **Logic and Sets**

Automated Reasoning - Logic programming in the context of expert system.

Earliest form of logic was based on the syllogism developed by Aristotle.

Syllogism - Have 2 premises that provide evidence to support a conclusion.

- **Propositional Logic:**
    - Deals with declarative sentences that are either true or false.
    - Uses logical connectives (AND, OR, NOT, implication, biconditional) and truth tables.

- **Predicate Logic:**
    - Extends propositional logic by dealing with predicates and quantifiers (universal  and existential ).
    - Supports more complex statements like “All men are mortal.”

![[Pasted image 20250223220009.png]]

Syllogism can also be defined as a valid argument, having 2 premises and a conclusion

major premise: All M are P
Minor premise: All s is M
conclusion: All s is P

#### **Propositional Logic**

It's concerned with syntax of statement not semantics

Syllogism:
	- All goons are loons
	- Zadok is a goon
	- Zadok is a loon
It's about making valid arguments not sense

#### **Intersecting Set**

![[Pasted image 20250223232613.png]]

##### **Boolean Logic**

Defines a set of axioms consisting of symbols to represent objects / classes

Axions are fundamental truths / assumptions used as a starting point

Using axioms theorems can be  constructed

##### Features of Prepositional Logic

It is also concerned with the subset of declarator sentences that can be classified as True/ False

We call these sentences "statements" or "prepositions"

Paradox: A statement that cannot be classified as true / false

Open sentences: Statements that cannot be answered absolutely

Compound Statement: Formed using logical connections like AND, OR, NOT, conditional / biconditional

Material implication - p -> q
biconditional - p <-> q
Tautology - A statement that is true for all possible cases
Contradiction - A statement that is false for all contradicting cases
Contingent Statement - A statement that is neither a tautology nor a contradiction.

#### **Truth Tables**

![[Pasted image 20250223233759.png]]

![[Pasted image 20250223233807.png]]

#### **Rules of Inference**

Modus Pones (law of detach):
	Direct reasoning, law of detachment assuming
	If A implies B and A is true, then B is true.

**Modus Tollens:** If A implies B and B is false, then A must be false.






















## **Key Concepts**

-

## **References**

-
