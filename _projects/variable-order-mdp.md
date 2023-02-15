---
title: "Reinforcement Learning for Solving Variable Order MDPs"
excerpt: "Research project about designing an efficient RL algorithm for Markov decision processes of variable order."
collection: projects
teaser: "/images/projects/variable_order_mdp/teaser.png"
teaser_type: "image"
teaser_video_hover: false
dates: "Nov. 2022 - Feb. 2023"
sorting_key: 202302
---

## Context

I chose to do this project as the final research project of the "[Reinforcement Learning](https://www.master-mva.com/cours/reinforcement-learning/)" course that I took during the first semester of my third year (2022-2023).

This project was among a list of interesting research ideas made by my teacher and his team, and as the teacher explicitly asked us not to share the project ideas outside the class, I will focus on the goal of the research project.

This is a research project where I am free to choose the direction I want to take.

## Objective

K-order Markov Decision Processes (MDPs) are a generalization of MDPs where transitions and rewards do not only depend on the current states but also on the past $k$ states and actions. Let $h_t^k = (s_{t+1}| s_{t-k},a_{t-k}, s_{t-k+1}, a_{t-k+1},...,s_t, a_t)$ be the history at $k$ steps. Then $p$ and $r$ are defined as:
$$
P(s_{t+1}|h_t^k) \\
R(h_t^k)
$$

The idea in reinforcement learning (RL) is to find the components in the k-order history that are relevant to learn the policy.

## Approach

Steps of the project:
 1) Formalize the problem and model
 2) Define an algorithm for learning the optimal policy and training the whole model
 3) Test it on some domain (even a simple tabular environment)

The project is ongoing, so I will update this page as I make progress.