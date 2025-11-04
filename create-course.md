# Course Creation Instructions for LLMs

## Overview

These instructions guide you through creating a structured course for the Lumina Study platform using the official block schema. You will use a **hybrid approach**: first gathering requirements through interactive questions, then generating the course structure based on templates.

**CRITICAL**: Do not assume any schema structure. You must fetch and analyze the current schema before generating any course content. The schema evolves, and what may have been true in previous versions may not be true now.

## Process Overview

The course creation process follows these phases:

1. **Schema Fetching** (Required First Step): Retrieve and analyze the current block schema
2. **Discovery** (Interactive): Ask the user questions about their course requirements
3. **Generation** (Template-Based): Create the course structure following the fetched schema
4. **Validation**: Verify the output conforms to the schema
5. **Refinement**: Iterate with the user based on feedback

## Schema Information

**STEP 1: Always start here.** Before beginning any course creation, fetch and analyze the block schema:

1. **Read the latest schema documentation**:
   - URL: `https://raw.githubusercontent.com/luminastudy/block/main/README.md`
   - Use WebFetch or similar tools to retrieve current schema information

2. **Fetch the JSON schema for validation**:
   - Extract the current version number from the README (look for patterns like "v0.1", "Version 0.1", or similar version indicators)
   - Construct the schema URL: `https://raw.githubusercontent.com/luminastudy/block/main/schema/v<version>/block.schema.json`
   - Replace `<version>` with the version number found in the README
   - **Parse and analyze the schema** to understand:
     - Required properties
     - Property types and structures
     - Validation rules
     - Allowed additional properties
     - Default values
     - Nested object structures

## Understanding the Schema

**Do not assume the schema structure.** Always fetch and analyze the actual JSON schema before generating courses. Key things to extract from the schema:

1. **Required vs Optional Properties**: Check the `required` array in the schema
2. **Property Types**: Understand if properties are objects, arrays, strings, etc.
3. **Nested Structures**: Look for recursive references or nested object definitions
4. **Constraints**: Check for patterns, min/max values, enum restrictions
5. **Bilingual Support**: Identify which fields support multiple languages and how they're structured
6. **Relationship Properties**: Understand how blocks relate to each other (prerequisites, parents, children, etc.)

Once you've analyzed the schema, you'll know exactly how to structure blocks correctly.

## Workflow

### Phase 1: Discovery (Interactive)

Ask the user the following questions to gather requirements:

1. **Course Topic**:
   - "What is the main topic or subject of the course you want to create?"
   - Clarify specific areas of focus if the topic is broad

2. **Course Structure**:
   - "How would you like to structure this course? For example:"
     - "Linear progression (Topic A → Topic B → Topic C)"
     - "Hierarchical (Main topics with subtopics)"
     - "Networked (Topics with multiple prerequisites)"
   - "Approximately how many main topics or blocks should this course have?"

3. **Prerequisites and Relationships**:
   - "Are there any prerequisite relationships? (e.g., Block A must be completed before Block B)"
   - "Should any blocks be grouped under parent blocks?"

4. **Content Depth**:
   - "Should I create a high-level outline or include detailed sub-blocks?"

### Phase 2: Generation (Template-Based)

Based on the user's answers and the schema you've fetched, generate the course structure:

#### Step 1: Analyze the Fetched Schema

Before generating any content:
- Identify all required properties for a block
- Understand the structure of bilingual fields (if applicable)
- Determine how relationships (prerequisites, parents, etc.) are represented
- Note any additional optional properties that might be useful

#### Step 2: Create the Top-Level Course Block

Using the schema structure, create a block with all required properties. Ensure you:
- Include all required fields as defined in the schema
- Use the correct structure for bilingual text fields
- Initialize relationship arrays (prerequisites, parents, etc.) appropriately
- Add any optional properties that enhance the course

#### Step 3: Create Main Topic Blocks

For each main topic identified in Phase 1:
- Create a block following the same schema structure
- Populate bilingual fields with appropriate content
- Establish relationships to parent blocks (if the schema supports this)
- Ensure all required properties are present

#### Step 4: Add Prerequisites and Relationships

If topics have dependencies:
- Use the relationship mechanism defined in the schema
- Ensure prerequisite blocks are properly referenced or included
- Maintain referential integrity between related blocks
- Follow the schema's specification for how blocks reference each other

#### Step 5: Create Nested Sub-Blocks (if applicable)

For hierarchical structures:
- Generate child blocks following the same schema
- Establish parent-child relationships as defined in the schema
- Maintain consistent structure throughout the hierarchy

### Phase 3: Review and Validate

1. **Show the generated structure** to the user in a readable format
2. **Explain the relationships**: which blocks depend on which, and the hierarchy
3. **Offer refinements**: "Would you like to add, remove, or modify any blocks?"
4. **Validate against schema**: Ensure all blocks conform to the required structure

## Example Illustration

**Note**: This is a conceptual example to illustrate the course creation process. The actual structure must match the schema you fetch. Do not copy this structure without first validating it against the current schema.

### Example: "Introduction to Programming" Course

**Concept**: A simple programming course with three sequential topics:
1. Variables and Data Types (foundation)
2. Control Structures (requires Variables)
3. Functions (requires Control Structures)

**Structure Considerations**:
- Each topic is a block with bilingual titles (Hebrew and English)
- Sequential prerequisites create a learning path
- The structure should follow whatever relationship model the schema defines

**Your actual output should**:
- Match the exact property names and structure from the fetched schema
- Include all required properties
- Use the correct nesting and reference mechanism
- Validate against the schema before presenting to the user

## Best Practices

1. **Fetch Before Building**: Always retrieve and analyze the schema before creating any course structure
2. **Start Simple**: Begin with a high-level structure and add detail iteratively
3. **Validate Early**: Check schema compliance after each major addition
4. **Be Consistent**: Use consistent naming conventions across all blocks and in all supported languages
5. **Explain Dependencies**: Clearly communicate why prerequisites and relationships exist
6. **Iterate**: Allow users to refine and adjust the structure
7. **Follow Schema Patterns**: Use the relationship and nesting mechanisms exactly as defined in the schema
8. **Test Structure**: Verify that the generated structure is valid JSON and conforms to the schema

## Tips for LLMs

- **Always fetch first**: NEVER assume you know the schema structure. Always fetch and analyze the schema before generating any content
- **Schema analysis is critical**: Spend time understanding the schema structure, required properties, and relationship mechanisms before creating blocks
- **Version awareness**: The schema evolves. What worked in one version may not work in another. Always use the current version
- **Ask clarifying questions**: If user requirements are ambiguous, ask before generating
- **Show visual representations**: Consider using markdown trees or diagrams to show course structure before generating JSON
- **Validate rigorously**: Validate generated content against the fetched schema. Use schema validation libraries if available
- **Save output**: Offer to save the generated course structure to a JSON file
- **Document your understanding**: When you fetch the schema, briefly explain to the user what structure you found and will be using

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
- **Schema URL Pattern**: `https://raw.githubusercontent.com/luminastudy/block/main/schema/v<version>/block.schema.json`
