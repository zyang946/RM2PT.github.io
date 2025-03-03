---
layout: page
title: RM2Doc
permalink: /rm2doc/
---

Download and use of RM2Doc can be found [here](https://rm2pt.com/advs/rm2doc).

### Introduction

**RM2Doc** is a tool for automatic generation of a *requirements document* from a *requirements model*. The **benefits** of RM2Doc are as follows:

1. Automatic generation of ISO/IEC/IEEE 29148-2018 conformed requirements documents from UML models without any templates.
2. Automatic generation of the flow description from a use case without additional information.
3. Automatic generation the semantic description of system operations only based on the formal expression of OCL.

<img src="../../imgs/RM2Doc/image-20211126174857182.png" alt="image-20211126174857182" style="zoom: 35%;" />



### Input of RM2Doc — Requirements Model

<img src="../../imgs/RM2Doc/rm.png" alt="rm" style="zoom: 50%;" />

The input to RM2Doc is a UML requirements model with OCL constraints. The model includes: , a use case diagram, system sequence diagrams, contracts of and system operations.

- **A conceptual class diagram:** A conceptual class diagram is a concept-relation model, which illustrates abstract and meaningful concepts and their relations in the problem domain, in which the concepts are specified as classes, the relations of the concepts are specified as the associations between the classes, and the properties of the concepts are specified as the attributes of the classes.

- **A use case diagram:** A use case diagram captures domain processes as use cases in terms of interactions between the system and its users. It contains a set of use cases for a system, actors represented a type of users of the system or external systems that the system interacts with, the relations between the actors and these use cases, and relations among use cases.

- **System sequence diagrams:** A system sequence diagram describes a particular domain process of a use case. It contains the actors that interact with the system, the system and the system events that the actors generate, their order, and inter-system events. Compared with the sequence diagram in design models, a system sequence diagram treats all systems as a black box and contains system events across the system boundary between actors and systems without object lifelines and internal interactions between objects.
- **Contracts of system operations:** The contract of a system operation specifies the conditions that the state of the system is assumed to satisfy before the execution of the system operation, called the pre-condition and the conditions that the system state is required to satisfy after the execution (if it terminated), called the post-condition of the system operation. Typically, the pre-condition specifies the properties of the system state that need to be checked when system operation is to be executed, and the postcondition defines the possible changes that the execution of the system operation is to realize.

### Two main features

#### Generate operations description

<img src="../../imgs/RM2Doc/genopdescription.png" alt="genopdescription" style="zoom: 100%;" />

RM2Doc can **generate natural language operations description** based on the **contracts of system operation** in the requirements model.

- **Definition Section:** In the definition section, the objects used jointly by the precondition section and the post-condition section are defined.
- **Precondition Section:** The precondition specifies the properties of the system state that need to be checked when system operation is to be executed. In addition to the checking of objects and attributes shown in Figure 1 (c), the precondition also includes the checking
  of links between objects.
- **Post-condition Section:** The post-condition defines the possible changes that the execution of the system operation is to realize. In addition to creating and adding objects, adding links between objects, and modifying the attributes of objects as shown in Figure 2, the postconditions include the deletion of objects and the removal of links between objects.

For the different operations, we defined a total of 25 transformation rules for the three sections. Transformation rules are presented in this form:

<img src="../../imgs/RM2Doc/image-20220424142859481.png" alt="image-20220424142859481" style="zoom: 20%;" />

The transformation rule contains two parts: the above section is an OCL expression in the contracts, and the bottom part is the corresponding natural language. By algorithmically matching the OCL expressions to the conversion rules, an operation description can be generated as shown below.

<img src="../../imgs/RM2Doc/nl.png" alt="nl" style="zoom: 80%;" />

#### Generate requirements document

<img src="../../imgs/RM2Doc/image-20220507180457264.png" alt="image-20220507180457264" style="zoom: 100%;" />


#### RM2Doc can generate five parts of a document:

- The **product functions** section and **user characteristics** section are generated from the use case diagram.
- The **use case description** part is generated from the use case diagram and system sequence diagrams.
- The **system operation description** part is generated from contracts of system operations.
- The **entity ananlysis** part  is generated from the conceptual class diagram.

In the rest of the requirements document, we have predefined guidelines for writing in accordance with the **ISO/IEC/IEEE 29148-2018**.

The image below shows a part of CoCoME's requirements document. For more details, please see https://github.com/RM2PT/CaseStudies.
<img src="../../imgs/RM2Doc/doc.png" alt="doc" style="zoom: 80%;" />
