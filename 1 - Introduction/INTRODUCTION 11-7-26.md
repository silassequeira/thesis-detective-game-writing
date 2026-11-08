# 1. Introduction

Imagine examining a photograph found at a crime scene. One detective game lets you choose how to examine it: enhance the image, send it for lab analysis, or study it under magnification. Each approach reveals different details. Which method you choose shapes what you learn and how you might question the suspect later. Your investigation unfolds based on your reasoning.

Now imagine a different detective game. You collect the same photograph. The game decides what it means. You must find it, present it, and hope you're presenting it at the "correct" moment. If you haven't found the "correct" piece of evidence in the "correct" order, you fail, even if your logical reasoning was sound. The investigation feels like following a checklist rather than thinking.

The core problem is this: many detective games offer investigation as a façade while removing the cognitive work that makes investigation meaningful. They ask you to collect clues, but they dictate what those clues mean. They invite you to deduce, but only along predetermined paths. The player becomes a guided reader executing predetermined conclusions rather than an independent thinker working through a mystery.

This thesis proposes a different approach. Rather than building detective games around branching narratives or predetermined clue sequences, what if we designed systems that treat interpretation itself as the game mechanic? What if the same clue could be examined through multiple investigative lenses, each revealing different information? What if players built their own case notebooks, synthesizing evidence in ways the game respects even when they diverge from what the designer expected? What if dreams and memories functioned as alternative investigative spaces, offering symbolic insights unavailable through waking logic?

The fundamental question is: can we design detective games where players experience investigation as genuine thinking, where solutions emerge from their own reasoning, not from following hidden designer-intended paths?

## 1.1 Project Frame , Motivation (Why Interactive Detective Narratives)

Detective narratives occupy a unique space in interactive media. In traditional media, novels, films, television, the detective is a character we watch solve a puzzle. The pleasure comes from following their reasoning and watching the truth unfold. In tabletop games like Dungeons & Dragons, players become the detective, but a human Game Master controls information flow, deciding what they encounter and what it means.

Digital detective games inherit from both traditions but face a distinct challenge: How do you create a system that feels like genuine investigation while remaining playable and coherent? How do you respect players' reasoning without requiring infinite narrative branches? How do you let them think independently while maintaining narrative integrity?

Some interactive narratives have found partial solutions. Time constraints can create meaningful pressure, if you have limited hours to investigate, you must choose strategically what to pursue. Multiple examination tools for evidence can make investigation feel less like object-clicking and more like reasoning. Portraying detective characters who doubt and experience uncertainty can make investigation feel genuine rather than a puzzle to be "solved correctly."

Yet even these approaches operate within significant limits. In practice, players often discover that their investigative conclusions are validated only if they align with a predetermined solution. Their reasoning might feel free, but it's constrained by invisible rails the player doesn't see. The investigative thinking exists, but it's channeled in directions the designer has already decided.

The motivation for this thesis is straightforward: What if we could design detective games that don't constrain investigation into predetermined paths? What if players could genuinely solve mysteries through their own reasoning, with multiple valid solutions that the game would respect? What would that system look like?

## 1.2 Objectives & Research Questions

Design Objective: Create a playable digital prototype of an interactive detective narrative that distributes investigative agency across multiple interpretive systems, evidence examination tools, social reasoning mechanics, and symbolic dream-based investigation, such that players experience mystery-solving as their own cognitive work rather than following a predetermined path.

Research Questions:

1. How can evidence be designed so that the same clue can be interpreted multiple ways, allowing players to follow different investigative paths while still reaching valid conclusions?

2. What role can NPC interactions play in distributing investigative agency beyond simple dialogue choices, specifically, can constrain social resources like patience create genuine strategic depth?

3. Can dream sequences function as meaningful investigative spaces where symbolic reasoning reveals truths unavailable through waking logic?

4. When players manually construct their case (building their own evidence connections and theories), does this increase their sense of solving the mystery themselves?

5. Can a single mystery be designed to have multiple valid solutions while still delivering a satisfying narrative conclusion?

Expected Outcomes: This work will produce three things: (a) a playable prototype demonstrating these systems in practice, (b) design documentation articulating how interpretive agency can be built into detective game mechanics, and (c) playtesting data revealing how players engage with interpretation-as-gameplay and whether multiple valid solutions enhance or undermine investigative satisfaction.

## 1.3 Methodology Overview

This thesis employs a Research through Design approach. Rather than theorizing detective game design in the abstract, we build a system, observe how players interact with it, observe what works and what fails, and iterate based on those observations. The prototype itself becomes the primary research tool.

The research unfolds across three phases:

Phase 1: Conceptual Validation tests core mechanics through paper prototyping and workshop sessions before digital development begins. We validate whether the two-slot evidence interaction system (where a clue + investigative tool yields interpretation) creates satisfying investigation, whether patience mechanics feel strategic rather than arbitrary, and whether symbolic dream investigation is cognitively coherent. This phase uses physical prototypes, cards, dice, character sheets, to quickly test and refine ideas.

Phase 2: Digital Prototyping translates validated mechanics into a playable game environment. This includes building the evidence-examination engine, patience systems for NPC interactions, and dream sequence logic. Throughout development, iterative playtesting with game studies researchers and experienced detective game players provides feedback on clarity, perceived agency, and narrative coherence.

Phase 3: Analysis and Reflection synthesizes playtesting observations (interaction logs, interviews, notebook construction patterns) against the research questions. Analysis focuses on whether players experienced genuine investigative agency, how multiple valid solutions affected engagement, and which design systems supported or hindered player reasoning.

Throughout all phases, design decisions are documented not as aesthetic choices, but as direct attempts to answer the research questions. Each iteration of the prototype becomes evidence about how detective game mechanics can support interpretive thinking.

## 1.4 Expected Results & Contributions

To Game Design Practice: This work contributes a practical framework for detective games that moves beyond binary "correct answer/incorrect answer" systems. It demonstrates how evidence examination and symbolic reasoning can create investigative complexity without requiring story branches to expand exponentially. The framework is applicable across mystery game genres, from noir detectives to academic investigators to puzzle-mystery hybrids.

To Understanding Interactive Narrative: The thesis directly engages with questions about how players experience agency in digital storytelling. It shows how interpretation-as-mechanic can distribute player agency in ways that both branching narratives and linear stories cannot. The work positions dreams, memories, and evidence-examination as systems equal in narrative weight to dialogue choices or branching paths.

Success Looks Like: The research will be considered successful if playtesting demonstrates that (a) players can reach different valid conclusions using the same evidence set, (b) players report feeling they "solved" the mystery through their own thinking, (c) players can understand and use the two-slot evidence system intuitively, (d) observation of player notebooks shows active theory-building and revision, and (e) players report satisfying narrative conclusions despite multiple valid solutions.

The Prototype Itself: Finally, the playable artifact demonstrates that detective games can treat interpretation as a core mechanic, equal in importance to combat systems, puzzle-solving, or social management. It's both a design proof-of-concept and an argument made through experience rather than theory alone.

## 1.5 Document Structure

This document is structured in the following way:

In Section 2, we establish the theoretical and historical context for why this design problem matters. We trace how participation in storytelling has evolved from ancient theater through literary experimentation to interactive digital media. We examine how different forms of interactive fiction and narrative games have approached the challenge of player agency and interpretation. We pay particular attention to historical precedents that demonstrate different solutions to investigative design, and we analyze the design tensions between giving players interpretive freedom while maintaining narrative coherence. Section 2 concludes by defining what we mean by "investigative agency" and why detective games are a particularly promising space for exploring it.

In Section 3, we present the detailed research methodology, including the structure of paper prototyping workshops, the playtesting process, and the specific metrics by which we'll evaluate whether the design systems succeed in creating genuine interpretive agency.

Section 4 describes the design proposal itself: the systems and mechanics that attempt to operationalize interpretive agency. This includes the two-slot evidence interaction system, the Case Construction Notebook, patience mechanics, dream-based symbolic investigation, and the mystery architecture that allows multiple valid investigative paths.

Throughout, this thesis treats the prototype not as a finished commercial product, but as a research conversation, a way of asking, through design and playtesting, what detective games could be if we genuinely respected players as independent thinkers.
