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

#### **Structure of a Rule-Based Expert System**

![[Pasted image 20250219112233.png]]

#### **General Methods of Inferencing**

- **Forward Chaining (Data-Driven):**
    
    - Begins with known facts and moves forward, applying rules to reach conclusions.
    - Best suited for tasks like prognosis, monitoring, and control, where data continuously drives the reasoning process.

- **Backward Chaining (Goal-Driven):**
    
    - Starts with a hypothesis (or potential conclusion) and works backward to find supporting facts.
    - Commonly used for diagnostic problems, where the system aims to confirm or rule out a specific goal or condition.

#### **Mathematical Roots of Rule Based Systems**

- Post Production Systems
	- Basic Idea: any mathematical / logical system is simply a set of rules specifying how to change one string of symbols into another string of symbols.
	- Limitation: Lack of control mechanism to guide the application of the rules.
	
- Markov Algorithm
	- **Basic Idea:**  A Markov algorithm rewrites an input string using a set of ordered rules. It checks each rule in priority order; if one matches, it’s applied, and the process repeats until no rule can be applied. (An effective algorithm for systems with many rules)
	- **Key Limitations:**
	    - **Rigid Ordering:** Rules are checked in a strict sequence, reducing flexibility.
	    - **Risk of Loops:** Poorly designed rules can lead to infinite rewriting.
	    - **Limited Reasoning:** It focuses on direct string manipulation, lacking advanced inference or handling of uncertainty.

- Rete Algorithm
	- Works like a “net” of information, efficiently storing partial matches to speed up rule checking.
	- Offers much faster response times compared to checking each IF-THEN rule individually.
	- Reuses past match results (exploits temporal redundancy) and groups similar patterns (exploits structural similarity).
	- **Drawback:** Requires a lot of memory.

#### **Programming Paradigms**

- **Procedural (Sequential)** - The Programmer specifies exactly how a problem solution must be coded. 
	- **Functional / Imperative**
		- Emphasizes variables and assignments, treating data as a “modifiable store.”
		- Execution moves from an initial to a final state through a series of intermediate states.
		- Encourages a top-down design approach.
		- Not typically well-suited for building expert systems directly, as it lacks specialized features for knowledge representation and inference.
- **Non Procedural** (OOP - Object Oriented Programming) - Does not depend on the programmer giving exact details how the program is to be solved.

![[Pasted image 20250219114603.png]]

#### **Artificial Neural Systems (ANS)**

A new development in programming paradigms in 1980s. Its based on the way the brain process information. ANS are found in face recognition, medical diagnosis, games, and speech recognition.

![[Pasted image 20250219114931.png]]

This diagram shows a **basic model of an artificial neuron** used in neural networks:

1. **Inputs and Weights:**
    
    - Each incoming signal (I₁, I₂, I₃, etc.) is multiplied by a corresponding weight (Wᵢ1, Wᵢ2, Wᵢ3, etc.). These weights determine the importance of each input.
    
2. **Summation (Total Input):**
    
    - The neuron sums all the weighted inputs to get a **total input**. Mathematically, it’s often written as:
    
$$
    I = \sum_{j} (W_{i,j} \times I_j)
$$

3. **Threshold (θ) or Bias:**
    
    - A threshold (or bias) is then applied. Essentially, the neuron compares the total input against this threshold to decide whether it should “fire” (activate).
    
4. **Activation Function (Sigmoid):**
    
    - The output (O) of the neuron is typically passed through an **activation function**, in this case, a sigmoid: 
    
$$
    O = \frac{1}{1 + e^{- (I - \theta)}}
$$
	
    - This function squashes the output to a range between 0 and 1, making it easier to handle in further layers or computations.

Overall, the neuron takes multiple weighted inputs, sums them, and produces a single output. By adjusting the weights and threshold, the neuron “learns” patterns from data.

![[Pasted image 20250219114942.png]]

![[Pasted image 20250219115001.png]]

##### **Characteristics**

- ANS is similar to an analog computer using simple processing elements connected in a highly parallel manner.
- Processing elements perform Boolean / arithmetic functions in the inputs
- Key feature is associated weights w/each element.

##### **Advantages**

1. **Storage is fault tolerant:**
    
    - The system’s information is stored across many interconnected nodes rather than in a single place.
    - If some nodes or connections fail, the overall system can still function, retaining much of the stored information.
    
2. **Quality of stored image degrades gracefully:**
    
    - Because the data (e.g., an image or pattern) is distributed across the network, losing part of the network doesn’t cause a total loss of the stored information.
    - Instead, the stored content becomes slightly less accurate, but not entirely destroyed.
    
3. **Nets can extrapolate and interpolate from their stored information:**
    
    - Neural networks can generalize from what they’ve learned.
    - They can handle new inputs that are similar (but not identical) to what they’ve seen before, effectively “filling in the gaps” or predicting missing data.
    
4. **Nets have plasticity:**
    
    - They can adapt over time, adjusting weights and connections as they learn new information or receive updated training data.
    - This makes them flexible and able to improve performance or change their behavior as conditions change.
    
5. **Excellent when long-term functionality is needed without repairs in hostile environments:**
    
    - Due to their fault tolerance and minimal maintenance needs, these networks can keep working reliably even under tough conditions, where constant repairs or human intervention aren’t feasible.

##### **Disadvantages**

- **No Explanation Facility:**
    
    - Neural networks (or similar learning systems) are often treated as “black boxes,” providing outputs without showing the reasoning behind them.
    
- **Requires a Lot of Training Examples:**
    
    - Achieving good performance usually demands extensive, high-quality data to teach the system effectively.
    
- **Difficult to Analyze Training Results:**
    
    - Even after training, it can be challenging to interpret or break down the network’s internal workings to understand exactly how it arrived at a particular conclusion.

#### **MACIE (Matrix Controlled Interface Engine)**

- It uses ANS knowledge base
- Designed to classify disease from symptoms into one of the known diseases the system has been trained on
- Uses forward chaining to make inferences and backward chaining to query user for additional data to reach conclusions


## **Key Concepts**

- **Definition of Expert Systems:**
    
    - Computer systems that mimic the decision-making abilities of human experts.
    
- **Areas of Artificial Intelligence:**
    
    - Expert systems are one part of AI, alongside other techniques and paradigms.

- **Expert System Technology:**
    
    - Utilizes specialized languages (e.g., CLIPS), dedicated programs, and even specific hardware to implement expert systems.
    
- **Main Components:**
    
    - **Knowledge Base:** A repository of information gathered from various sources (books, experts, etc.).
    - **Inference Engine (Interface Engine):** Applies logical rules to the knowledge base to draw conclusions.
    
- **Basic Functions:**
    
    - They include reasoning, explanation, and decision-making, supported by components like working memory and an agenda.
    
- **Problem Domain vs. Knowledge Domain:**
    
    - The knowledge domain is the specific area of expertise (e.g., medicine) within a broader problem domain (e.g., healthcare).
    
- **Advantages of Expert Systems:**
    
    - They are available 24/7, reduce costs and dangers, offer high performance, provide consistent and reliable results, and can even serve as intelligent tutors.
    
- **Building an Expert System:**
    
    - Involves gathering knowledge from human experts, coding it into the system, and then refining the system through expert feedback.
    
- **Role of AI:**
    
    - AI provides flexible, reasoning-based approaches when straightforward algorithms aren’t enough, using inference engines to approximate human reasoning.
    
- **Handling Uncertainty:**
    
    - Expert systems deal with both shallow (heuristic, empirical) and deep (fundamental) knowledge, which affects their complexity and accuracy.
    
- **Limitations of Expert Systems:**
    
    - They struggle with generalizing through analogy and face a bottleneck in knowledge acquisition due to the time-intensive process of encoding expert knowledge.
    
- **Cognitive Foundations:**
    
    - Expert systems are influenced by models like the Newell/Simon General Problem Solver, incorporating concepts of long-term (IF-THEN rules) and short-term memory along with conflict resolution in inference.

- **Expert vs. Base Knowledge:**
    
    - Base knowledge covers standard rules and procedures, while expert knowledge involves deeper, often tacit insights developed through experience.
    
- **Historical Examples:**
    
    - Early systems like DENDRAL (chemistry), MYCIN (medicine), DIPMETER and PROSPECTOR (geological exploration), and XCON (computer configuration) illustrate various applications.
    
- **Applications and Domains:**
    
    - Expert systems can be designed for configuration, diagnosis, teaching, interpretation, monitoring, planning, prognosis, remedy, and control.
    
- **Design Considerations:**
    
    - They must be built for well-bounded domains, with genuine need, accessible expert input, and knowledge that can be clearly explained.
    
- **Expert System Languages and Tools:**
    
    - These are specialized for handling knowledge representation and inference, differing from traditional procedural or object-oriented languages.
    
- **Elements of a Rule-Based Expert System:**
    
    - Includes components like the user interface, working memory, inference engine, agenda, knowledge acquisition facility, and the knowledge base itself.
    
- **Inferencing Methods:**
    
    - **Forward Chaining:** Data-driven approach that starts with known facts.
    - **Backward Chaining:** Goal-driven approach that works backwards from a hypothesis.
    
- **Mathematical Foundations:**
    
    - Concepts such as post-production systems, Markov algorithms (string rewriting), and the Rete algorithm (efficient pattern matching) underpin rule-based reasoning.
    
- **Programming Paradigms:**
    
    - Contrasts procedural (sequential, step-by-step) with non-procedural (object-oriented) approaches, noting that traditional procedural methods are less suited for expert systems.
    
- **Artificial Neural Systems (ANS):**
    
    - Inspired by the brain, these systems use interconnected nodes (neurons) with weighted inputs to learn patterns, featuring characteristics like fault tolerance, graceful degradation, and adaptability.
    - They come with advantages (e.g., robustness, ability to generalize) and limitations (e.g., lack of explainability, need for large training datasets).
    
- **MACIE (Matrix Controlled Interface Engine):**
    
    - An example of a system that uses a neural network-based knowledge base combined with forward and backward chaining to classify diseases based on symptoms.

## **References**

![[chapter01-1.ppt]]
