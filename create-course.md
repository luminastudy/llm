# Course Creation Instructions for LLMs

## Overview

These instructions guide you through creating a structured course for the Lumina Study platform using the official block schema. You will use a **hybrid approach**: first gathering requirements through interactive questions, then generating the course structure based on templates.

## Schema Information

Before beginning, familiarize yourself with the block schema:

1. **Read the latest schema documentation**:
   - URL: `https://raw.githubusercontent.com/luminastudy/block/main/README.md`
   - Use WebFetch or similar tools to retrieve current schema information

2. **Fetch the JSON schema for validation**:
   - Current version: v0.1
   - URL: `https://raw.githubusercontent.com/luminastudy/block/main/schema/v0.1/block.schema.json`
   - Note: Check the README for the latest version number and update accordingly

## Block Schema Structure (v0.1)

Each block must contain:

```json
{
  "title": {
    "he_text": "string (Hebrew title)",
    "en_text": "string (English title)"
  },
  "prerequisites": [
    // Array of block objects (blocks that must be completed first)
  ],
  "parents": [
    // Array of block objects (blocks this belongs to)
  ]
}
```

**Key Points**:
- All three properties (`title`, `prerequisites`, `parents`) are required
- Title must have both Hebrew and English text
- Arrays can be empty but must be present
- Blocks support recursive nesting (prerequisites and parents contain block objects)
- Additional properties are allowed for extended metadata

## Workflow

### Phase 1: Discovery (Interactive)

Ask the user the following questions to gather requirements:

1. **Course Topic**:
   - "What is the main topic or subject of the course you want to create?"
   - Clarify specific areas of focus if the topic is broad

2. **Language Preference**:
   - "What language(s) will this course be in?"
   - If bilingual: "Do you have specific content for Hebrew and English, or should I translate?"

3. **Course Structure**:
   - "How would you like to structure this course? For example:"
     - "Linear progression (Topic A → Topic B → Topic C)"
     - "Hierarchical (Main topics with subtopics)"
     - "Networked (Topics with multiple prerequisites)"
   - "Approximately how many main topics or blocks should this course have?"

4. **Prerequisites and Relationships**:
   - "Are there any prerequisite relationships? (e.g., Block A must be completed before Block B)"
   - "Should any blocks be grouped under parent blocks?"

5. **Content Depth**:
   - "Should I create a high-level outline or include detailed sub-blocks?"

### Phase 2: Generation (Template-Based)

Based on the user's answers, generate the course structure:

#### Step 1: Create the Top-Level Course Block

```json
{
  "title": {
    "he_text": "[Hebrew course name]",
    "en_text": "[English course name]"
  },
  "prerequisites": [],
  "parents": []
}
```

#### Step 2: Create Main Topic Blocks

For each main topic identified:

```json
{
  "title": {
    "he_text": "[Hebrew topic name]",
    "en_text": "[English topic name]"
  },
  "prerequisites": [],
  "parents": [
    // Reference to the top-level course block
  ]
}
```

#### Step 3: Add Prerequisites

If topics have sequential dependencies:

```json
{
  "title": {
    "he_text": "נושא ב",
    "en_text": "Topic B"
  },
  "prerequisites": [
    // Include the full block object for Topic A
  ],
  "parents": [
    // Reference to parent course
  ]
}
```

#### Step 4: Create Nested Sub-Blocks (if applicable)

For hierarchical structures:

```json
{
  "title": {
    "he_text": "תת-נושא 1.1",
    "en_text": "Subtopic 1.1"
  },
  "prerequisites": [],
  "parents": [
    // Reference to the parent topic block
  ]
}
```

### Phase 3: Review and Validate

1. **Show the generated structure** to the user in a readable format
2. **Explain the relationships**: which blocks depend on which, and the hierarchy
3. **Offer refinements**: "Would you like to add, remove, or modify any blocks?"
4. **Validate against schema**: Ensure all blocks conform to the required structure

## Example Output

Here's a simple example course on "Introduction to Programming":

```json
{
  "title": {
    "he_text": "מבוא לתכנות",
    "en_text": "Introduction to Programming"
  },
  "prerequisites": [],
  "parents": [],
  "blocks": [
    {
      "title": {
        "he_text": "משתנים וטיפוסי נתונים",
        "en_text": "Variables and Data Types"
      },
      "prerequisites": [],
      "parents": []
    },
    {
      "title": {
        "he_text": "מבני בקרה",
        "en_text": "Control Structures"
      },
      "prerequisites": [
        {
          "title": {
            "he_text": "משתנים וטיפוסי נתונים",
            "en_text": "Variables and Data Types"
          },
          "prerequisites": [],
          "parents": []
        }
      ],
      "parents": []
    },
    {
      "title": {
        "he_text": "פונקציות",
        "en_text": "Functions"
      },
      "prerequisites": [
        {
          "title": {
            "he_text": "מבני בקרה",
            "en_text": "Control Structures"
          },
          "prerequisites": [],
          "parents": []
        }
      ],
      "parents": []
    }
  ]
}
```

## Best Practices

1. **Start Simple**: Begin with a high-level structure and add detail iteratively
2. **Validate Early**: Check schema compliance after each major addition
3. **Be Consistent**: Use consistent naming conventions in both languages
4. **Explain Dependencies**: Clearly communicate why prerequisites exist
5. **Iterate**: Allow users to refine and adjust the structure
6. **Use Nested Objects Wisely**: For complex prerequisites, include full block objects rather than references

## Tips for LLMs

- **Fetch schema dynamically**: Always retrieve the latest schema version to ensure compatibility
- **Ask clarifying questions**: If user requirements are ambiguous, ask before generating
- **Show visual representations**: Consider using markdown trees or diagrams to show course structure
- **Validate JSON**: Ensure all generated JSON is valid and parseable
- **Handle translations**: If user provides only one language, offer to translate (with their approval)
- **Save output**: Offer to save the generated course structure to a JSON file

## Troubleshooting

**Issue**: User doesn't know the structure they want
- **Solution**: Suggest common patterns (linear, hierarchical, modular) with examples

**Issue**: Complex prerequisite relationships
- **Solution**: Create a visual diagram first, then implement in JSON

**Issue**: Schema version mismatch
- **Solution**: Always fetch the latest schema from the GitHub repository and check version number

---

## Quick Reference

- **Schema Repo**: <https://github.com/luminastudy/block>
- **Schema README**: <https://raw.githubusercontent.com/luminastudy/block/main/README.md>
- **Current Schema**: <https://raw.githubusercontent.com/luminastudy/block/main/schema/v0.1/block.schema.json>
