+++
date = '2026-06-30T00:00:00+02:00'
title = '📜 New Publications'
subtitle = 'Recent papers from the Deeper4AI team accepted for publication'
author = "Deeper4AI @ Melbourne & Prague"
tags = ["Publications", "TheoremProving", "Autoformalization", "MachineLearning", "Isabelle", "Vampire", "EProver"]
+++

We are happy to announce a series of new papers from our team, all accepted for
publication. The work spans two intertwined themes: large-scale LLM-assisted
autoformalization of mathematical textbooks, and machine learning guidance for
higher-order automated theorem proving. See our [Publications](/publications) page for details.

+ **Learning-Guided Higher-Order Automated Reasoning for Isabelle/HOL**.
  We present higher-order extensions of ENIGMA and Deepire — the two prominent
  learning-guided reasoning systems for the E and Vampire provers — and evaluate
  them on a large Isabelle/HOL corpus emulating Sledgehammer, observing consistent
  improvement across the board.

+ **Optimising Metamath Proofs for Human Working Memory**.
  Formal proofs are often ordered for verification efficiency rather than human
  readability. We introduce algorithms that reorder Metamath proof steps to minimise
  peak and cumulative working memory load, modelling proofs as DAGs and their
  execution as a pebbling game, and demonstrate improvements on Metamath's ZFC
  set theory library.

+ **Polymorphism Meets DHOL**.
  DHOL (Dependent Higher-Order Logic) is a powerful logic with dependent types and
  strong ATP support. This paper develops polymorphic DHOL (PDHOL), extending the
  expressivity of DHOL while retaining its simple definition and automation, with a
  sound and complete translation to polymorphic HOL implemented in a logic-embedding tool.

+ **Agent Hunt: Bounty Based Collaborative Autoformalization With LLM Agents**.
  We explore large-scale autoformalization of algebraic topology using a simulated
  bounty marketplace: multiple LLM agents propose formal lemmas, attach bounties, and
  compete to discharge proof obligations, scaling collaborative formalization in a
  decentralized fashion.

+ **Munkres' General Topology Autoformalized in Isabelle/HOL**.
  A complete LLM-assisted autoformalization of all 39 sections of Munkres'
  _Topology_ in Isabelle/HOL, producing over 85,000 lines of code with 806 fully
  proved results and zero unfinished proofs, using a "sorry-first" declarative
  workflow combined with Sledgehammer.
