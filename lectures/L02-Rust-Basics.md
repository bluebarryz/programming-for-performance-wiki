---
tags:
  - lecture
  - ECE459
  - rust
lecture: L02
title: Rust Basics
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L02 - Rust Basics

This lecture introduces the Rust programming language, focusing on features relevant to performance. It covers Rust's expression-based syntax and semicolons, immutability by default (and why that helps performance), shadowing, and the `mut` keyword. The core of the lecture is Rust's memory management through ownership: the three ownership rules, move semantics vs copy semantics, the `Copy` and `Drop` traits, and how ownership prevents memory leaks, double-frees, and use-after-free bugs. The lecture also discusses garbage collection costs (with a Discord case study comparing Go vs Rust) and RAII.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Motivates why Rust is used and the performance goals the language serves

## Concepts Covered

- [[immutability-by-default]]
- [[shadowing]]
- [[rust-memory-management]]
- [[ownership]]
- [[move-semantics]]
- [[copy-and-drop-traits]]
- [[raii]]
- [[garbage-collection-vs-ownership]]
- [[rust-motivation]]
