---
date: 2025-02-18
course: CSM 497 - Expert Systems
tags:
  - personal
  - study
  - CSM497
---

## **Overview**

- #### **What is an expert System?**

	- It's a computer system that emulates, or acts in all respects, with the decision-making capabilities of a human expert. (by. Professor Edward Feigenbaum - Stanford University)
	
- #### **Areas of Artificial Intelligence**

	![[Pasted image 20250218083833.png]]

#### **Expert system technology may include:**

- Special expert system languages - CLIPS
- Programs
- Hardware designed to facilitate the implementation of those systems.

#### **Expert system Main Components:** 

- Knowledge base - obtainable from books, magazines, knowledgeable persons, etc
- Interface engine - draws conclusions from the knowledge base.

#### **Basic Functions of Expert Systems**

![[Pasted image 20250218084917.png]]

#### **Problem Domain vs Knowledge Domain**

An expert’s knowledge is focused on a specific area (the knowledge domain) within a broader field (the problem domain). For example, a doctor’s expertise is within the knowledge domain of medicine, which is a part of the larger problem domain of healthcare.
![[Pasted image 20250218085237.png]]


#### **Advantages of Expert Systems**
- **Increased availability -** Expert systems can operate 24/7, ensuring that expert knowledge is accessible whenever needed, without being limited by human working hours.

- **Reduced Cost -** Once developed, expert systems can be more cost-effective than hiring human experts, as they reduce labor costs and the need for continuous human intervention.

- **Reduced danger -** In hazardous environments (like deep-sea exploration or nuclear facilities), expert systems can perform tasks without risking human safety.

- **Performance -** They can process information and execute complex reasoning tasks quickly and accurately, often outperforming humans in speed and consistency.

- **Multiple expertise -** An expert system can integrate knowledge from various fields, providing insights that combine several areas of expertise simultaneously.

- **Increased reliability -** Because expert systems follow programmed rules without fatigue or emotional bias, they deliver consistent and dependable results.

- **Explanation -** Many expert systems are designed to provide clear explanations for their decisions, which helps users understand the reasoning behind each conclusion.

- **Fast response -** They can rapidly analyze data and produce outputs, making them highly effective in time-sensitive situations.

- **Steady, unemotional, and complete responses at all times -** Unlike human experts, expert systems are not affected by emotions, fatigue, or distractions, ensuring they always provide a balanced and thorough analysis.

- **Intelligent tutor -** Some expert systems can also function as educational tools, guiding users through complex problems and helping them learn from the system’s reasoning process.

- **Intelligent database -** They often include sophisticated data management, allowing them to store, organize, and retrieve information efficiently, contributing to informed decision-making.

#### **The Process of Building an expert system:**

- **Talking with the Expert:**  
    A knowledge engineer (a person who builds the system) meets with a human expert in a specific field. They ask questions to gather detailed information and understand how the expert makes decisions.
    
- **Putting the Information into the System:**  
    The knowledge engineer then writes down or "codes" the expert's knowledge into the system's knowledge base. This means they organize and input the information so the system can use it to make decisions later.
    
- **Getting Feedback:**  
    Once the system is set up, the human expert tests it out and gives feedback. The expert tells the knowledge engineer what works well and what needs improvement, so the system can be refined and made more accurate.

![[Pasted image 20250218090356.png]]

#### **Role of AI**

AI (Artificial Intelligence) comes into play when a straightforward algorithm isn't enough to solve a problem:

1. **Algorithms vs. AI:**
    
    - An algorithm is a clear, step-by-step procedure that guarantees a solution in a finite amount of time—think of it like a recipe that always works under the right conditions.
    - However, not all problems can be solved with a simple algorithm. When we don’t have a clear set of steps or when the situation is too complex, we turn to AI for a more flexible approach.
    
2. **Expert Systems and Inference:**
    
    - Expert systems are a branch of AI that use reasoning to make decisions. They rely on an “inference engine,” which processes rules and facts to reach a conclusion.
    - Instead of an exact or guaranteed answer, expert systems aim for a “reasonable solution” based on the knowledge they’ve been given, much like a human expert might do.

#### **Uncertainty**

- **Shallow Knowledge** relies on empirical (observed) facts and heuristic (rule-of-thumb) methods, making it easier to program into expert systems.
- **Deep Knowledge** focuses on the fundamental structure, function, and behavior of objects or processes. Although more powerful, it is more challenging to represent in an expert system.

Ultimately, expert systems—like human experts—must handle uncertain situations, and the depth of their knowledge influences both the complexity of their design and the quality of their reasoning.

#### **Limitations of Expert Systems**

- **Limited Ability to Generalize Through Analogy:**
    
    - Expert systems typically rely on specific, pre-programmed rules and knowledge.
    - Unlike humans, they cannot easily draw analogies or apply experience from one situation to a new, unfamiliar scenario.
    
- **Knowledge Acquisition Bottleneck:**
    
    - Building an expert system requires gathering and encoding expertise from human specialists.
    - This process is often time-consuming and labor-intensive, which slows down system development and limits how quickly knowledge can be updated or expanded.

#### **Development of Expert Systems**

- **Rooted in Cognitive Studies**
    
    - Expert systems are inspired by how humans think and process information. They attempt to replicate the reasoning strategies that people use to solve problems.
    
- **Newell/Simon Model (GPS – General Problem Solver)**
    
    - **Long-Term Memory (IF-THEN Rules):**  
        This is where the system stores general knowledge in the form of rules—similar to how humans keep learned facts and methods.
    - **Short-Term Memory (Current Facts):**  
        This represents the immediate data or context the system is currently working with, much like the short-term information people hold in their minds when solving a problem.
    - **Inference Engine/Conflict Resolution:**  
        The inference engine applies the stored rules to the current facts to draw conclusions or decide on actions. When multiple rules could apply, conflict resolution strategies determine which rule to use first.

#### **Expert Knowledge**

- **Base Knowledge vs. Expert Knowledge:**
    
    - _Base Knowledge_ often comes from established sources (like books) and is relatively straightforward, covering basic rules and procedures.
    - _Expert Knowledge_ goes deeper, involving heuristics, personal experiences, and “secrets” of the trade—tacit insights developed over time.
    
- **Experts vs. Novices in New Situations:**
    
    - When faced with entirely new problems, experts may not perform drastically better than novices because their deep, specialized knowledge may not apply directly to unknown scenarios.
    
- **Chess Example:**
    
    - **Chess Rules** represent the base knowledge anyone can learn.
    - **Chess Master Patterns** illustrate the expert knowledge gained from extensive practice and experience, enabling masters to recognize patterns and respond quickly to familiar situations.

#### **Early Expert Systems**

- **DENDRAL:**
    
    - Designed for use in chemical mass spectroscopy.
    - Helps identify the molecular structure of chemical compounds by analyzing spectrometry data.

- **MYCIN:**
    
    - A medical diagnosis system.
    - Specializes in identifying bacterial infections and recommending treatments.

- **DIPMETER:**
    
    - Analyzes geological data to locate oil.
    - Uses well-logging data to interpret subsurface structures.

- **PROSPECTOR:**
    
    - Similar to DIPMETER but focuses on minerals.
    - Assists geologists in mineral exploration by evaluating geological data.

- **XCON (also called R1):**
    
    - Configures computer systems (specifically DEC’s VAX computers).
    - Automates the process of selecting and connecting compatible hardware components.

#### **Expert Systems Applications and Domains**

| **Class (Types)**        | **General Areas**                                                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Configuration            | Focuses on assembling or arranging the right components of a system in a proper way (e.g., selecting and organizing computer parts). |
| Diagnosis                | Identifies underlying problems based on observed evidence (e.g., diagnosing illnesses from patient symptoms).                        |
| Instruction (Teaching)   | Acts as an intelligent tutor, explaining concepts and answering questions (“why,” “how,” “what if”), just like a human teacher.      |
| Interpretation:          | Explains observed data or events (e.g., interpreting geological survey data).                                                        |
| Monitoring               | Compares real-time data to expected performance or values, detecting deviations (e.g., monitoring factory equipment).                |
| Planning                 | Develops strategies or actions to achieve specific goals (e.g., scheduling production processes).                                    |
| Prognosis                | Predicts future outcomes based on current data (e.g., forecasting equipment failure).                                                |
| Remedy (or Prescription) | Recommends solutions or treatments for a given problem (e.g., suggesting medical treatments).                                        |
| Control                  | Regulates processes automatically to maintain desired conditions (e.g., controlling a manufacturing process in real time).           |

#### **Consideration for Building Expert Systems**

- **Suitability of the Problem:**
    
    - Check if the task is too complex or ill-structured for conventional programming.
    - If standard, well-defined algorithms work, an expert system might not be necessary.
    
- **Well-Bounded Domain:**
    
    - The field of application should be clearly defined (e.g., medicine, chemistry, or even more specialized areas).
    - Vague or overly broad domains are harder to capture in an expert system.
    
- **Actual Need for an Expert System:**
    
    - Determine if there is genuine demand or benefit. Some problems may not justify the effort of building an expert system.
    
- **Availability of a Willing Expert:**
    
    - A human expert must be ready to share knowledge and collaborate.
    - Experts might reveal personal methods or “secrets,” and they can have differing opinions.
    
- **Ability to Explain Knowledge:**
    
    - The expert’s reasoning should be explainable to a knowledge engineer.
    - If the expert can’t articulate their methods, it’s harder to encode that expertise.
    
- **Nature of the Knowledge (Heuristic and Uncertain):**
    
    - Expert systems are most helpful when dealing with heuristic (rule-of-thumb) or uncertain knowledge.
    - If the knowledge is strictly procedural or well-defined, simpler solutions might suffice.

#### **Expert Systems Languages, Shells, and Tools**

A few points about the nature of expert system development tools compared to conventional programming:

1. **Conventional Programs Use Algorithms:**
    
    - Typical computer programs solve problems with clearly defined, step-by-step methods (algorithms).
    - They’re best suited for tasks where the process can be precisely outlined.
    
2. **Rigid Control Flow from Tight Data-Knowledge Interweaving:**
    
    - In some programs, data and the logic that processes it are intertwined in a fixed sequence of steps.
    - This can make the program less flexible when dealing with situations that don’t follow a strict procedure.
    
3. **Advanced (Specialized) Languages for Expert Systems:**
    
    - Expert system languages (e.g., Prolog, CLIPS) are designed to handle knowledge representation and inference more easily.
    - However, they may be more limited in scope, focusing on a specific type of problem-solving rather than general-purpose tasks.

**Expert system languages** are tailored for encoding and manipulating expert knowledge, making them ideal for building systems that mimic human decision-making processes. (Post-third generation)

- **Post-Third Generation (Expert System) Languages:**
    
    - Specialized for knowledge representation and reasoning.
    - Example: **CLIPS**, which simplifies creating and managing rules and facts.
    
- **Procedural Languages (e.g., C):**
    
    - Focus on step-by-step instructions and data handling techniques.
    - Best for well-defined, algorithmic problems.
    
- **Modern Object-Oriented Languages (e.g., Java):**
    
    - Emphasize data abstraction, encapsulation, and reuse.
    - Good for complex, large-scale software projects.

#### **Elements of an Expert System**

- **User interface** - mechanism by which user and system communicate.
- **Exploration facility** - explains reasoning of expert system
- **Working memory** - global database of facts used by rules
- **Interface engine** - makes inferences deciding which rules are satisfied and prioritizing.
- **Agenda** - a prioritized list of rules created by the inference engine, whose patterns are satisfied by facts or objects in working memory.
- **Knowledge acquisition facility** - automatic way for the user to enter knowledge in the system bypassing the explicit coding by knowledge engineer
- **Knowledge Base**

#### **Production Rules**

- **Knowledge Base as “Production Memory”:**
    
    - In many rule-based expert systems, the knowledge base is referred to as “production memory.”
    - This is because it stores the rules (or “productions”) that describe how the system should act when certain conditions are met.

- **Production Rules in IF-THEN Format:**
    
    - Rules are typically written as statements like “IF some condition is true THEN perform a specific action.”
    - This format makes it straightforward to encode logical conditions and outcomes.

- **Inference Engine’s Role:**
    
    - The inference engine is the component that checks each rule’s “antecedent” (the IF part) against the current facts.
    - Whenever the conditions match, the inference engine triggers the corresponding actions (the THEN part), guiding the system’s reasoning process.



## **Key Concepts**

-

## **References**

![[chapter01-1.ppt]]
