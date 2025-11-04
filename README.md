# Lumina Study - LLM Instructions Repository

Welcome to the Lumina Study LLM Instructions Repository. This repository contains structured instructions and guidelines for Large Language Models (LLMs) to assist in creating educational content using the Lumina Study platform.

## About

This repository serves as a central hub for LLM-consumable instructions that enable AI assistants to help users build courses, curricula, and educational materials that conform to the [Lumina Study block schema](https://github.com/luminastudy/block).

## Table of Contents

### Course Creation

#### [create-course.md](./create-course.md)
**Purpose**: Interactive instruction set for building structured courses using the Lumina Study block schema.

**What it does**:
- Guides LLMs through a hybrid workflow combining interactive questioning and template-based generation
- Dynamically fetches the latest block schema version from the official repository
- Walks through course topic discovery, structure planning, and block hierarchy design
- Ensures all generated content validates against the official JSON schema (v0.1+)
- Supports bilingual content creation (Hebrew and English)
- Handles prerequisite relationships and parent-child block hierarchies

**When to use**: When a user wants to create a new course, curriculum, or structured learning path for the Lumina Study platform.

---

## Quick Start for LLMs

1. **Identify the user's goal**: Determine which instruction file matches their request
2. **Read the instruction file**: Follow the step-by-step workflow provided
3. **Execute interactively**: Use the hybrid approach (ask questions, then generate)
4. **Validate output**: Ensure all generated content conforms to the referenced schemas

## Schema Resources

- **Block Schema Repository**: https://github.com/luminastudy/block
- **Latest Schema README**: https://raw.githubusercontent.com/luminastudy/block/main/README.md
- **Current Version**: v0.1
- **Schema Location**: https://raw.githubusercontent.com/luminastudy/block/main/schema/v0.1/block.schema.json

## Contributing

This repository is designed to grow with additional instruction sets. Future additions may include:
- Curriculum mapping instructions
- Assessment creation guidelines
- Content migration workflows
- Multi-language content generation

---

**Repository**: https://github.com/luminastudy/llm
