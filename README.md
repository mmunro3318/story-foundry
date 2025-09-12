# Story Foundry

**An AI-Powered Novel Writing Assistant Framework**

Story Foundry is an innovative agentic collaboration system that partners with authors to write novels through a structured, AI-assisted creative process. Unlike traditional writing tools, Story Foundry employs multiple specialized AI subagents working together to guide authors through every stage of novel creation—from initial brainstorming to final manuscript.

## ✨ What Makes Story Foundry Unique

- **Agentic Collaboration**: A team of specialized AI subagents, each expert in different aspects of storytelling
- **Structured Workflow**: A proven three-stage process that transforms ideas into finished novels
- **Story Theory Foundation**: Built on established frameworks from experts like Shawn Coyne's "Story Grid" and other renowned writing methodologies
- **Author-Centric**: Captures and preserves the author's unique voice and intent throughout the process
- **Project Organization**: Manages multiple novel projects with comprehensive story bibles and structured content

## 🎯 The Three-Stage Workflow

### 1. **Capture Stage**
*Brainstorming and idea collection*

- **Purpose**: Exhaust the author's ideas through guided brainstorming sessions
- **Process**: Authors dump ideas, concepts, and inspiration while AI subagents help explore and expand
- **Subagents**: archivist, wildcard-generator, idea-generator, backstory-expert, plot-expert
- **Output**: Raw creative content, character concepts, world-building elements

### 2. **Distillation Stage**  
*Organizing ideas into coherent structure*

- **Purpose**: Transform raw ideas into structured outlines and story architecture
- **Process**: AI subagents analyze and organize content into coherent narrative structures
- **Subagents**: story-architect, scene-architect, archivist, researcher, editor
- **Output**: Story outlines, scene cards, narrative structure documents

### 3. **Production Stage**
*Writing and refining the manuscript*

- **Purpose**: Collaborate on actual prose writing and content refinement
- **Process**: AI subagents assist with scene writing, editing, and maintaining consistency
- **Subagents**: scene-architect, continuity-expert, dialogue-expert, editor, writer-author
- **Output**: Draft scenes, final manuscript sections, editorial feedback

## 🤖 The Subagent Team

Story Foundry employs a team of specialized AI subagents, each with distinct expertise:

| Subagent | Specialty |
|----------|-----------|
| **archivist** | Records and retrieves author's words verbatim from sessions |
| **story-architect** | Distills ideas into coherent vision through outlines and story arcs |
| **scene-architect** | Designs and assesses scene structure for specific narrative moments |
| **plot-expert** | Maintains coherence with ABC plot structure and story development |
| **editor** | Assesses structure and coherence of prose and content |
| **continuity-expert** | Ensures consistency across the growing body of work |
| **dialogue-expert** | Generates and refines character dialogue |
| **writer-author** | Writes actual prose and content for scenes and narrative fragments |
| **backstory-expert** | Develops character backstories using proven story theory |
| **worldbuilder** | Creates immersive settings that serve the story's themes |
| **idea-generator** | Builds upon and interpolates between existing story elements |
| **wildcard-generator** | Provides creative, orthogonal directions for plot development |
| **researcher** | Conducts story theory research and reference gathering |

## 📁 Project Structure

Each novel project follows a standardized organization system:

```
projects/
  [project-name]/
    author-notes/           # Session recordings and raw author input
      session-notes-[###].md
    content/                # Finalized story materials
      outlines/             # Approved story and scene outlines
      drafts/               # Working manuscript drafts
      manuscript/           # Final manuscript files
    workspace/              # Active work area for current session
      # Capture stage files:
      setting.md
      characters.md
      session-notes.md
      # Distillation stage files:
      full-story-outline.md
      full-scene-outline.md
      story-card-[##].md
      # Production stage files:
      agent-draft.md
      critique.md
      fix_spec.md
      agent-draft-rev.md
      editor_log.md
    story-bible.json        # Comprehensive story reference
    README.md               # Project-specific documentation
```

## 📖 Story Bible System

Each project maintains a comprehensive `story-bible.json` that serves as the canonical reference for:

- **Voice Specification**: Writing style guidelines and comparable authors
- **Canon**: Setting, era, technology, and world rules
- **Characters**: Detailed profiles with goals, wounds, and development arcs  
- **Constraints**: POV, tense, and technical writing parameters
- **Plot Elements**: A-story, B-story, C-story tracking
- **Research Notes**: Reference materials and inspiration sources

## 🚀 Getting Started

### Prerequisites
- VS Code with Claude/AI integration
- Access to Claude AI or compatible language model
- Basic familiarity with markdown and JSON

### Starting Your First Project

1. **Initialize a new project:**
   ```
   /init-project [your-novel-title]
   ```

2. **Begin the Capture stage:**
   - Start with your core idea, premise, or inspiration
   - Let the AI subagents guide you through brainstorming
   - Don't worry about organization—just get ideas out

3. **Move to Distillation:**
   - The system will help organize your ideas into structured outlines
   - Review and approve story architecture before proceeding

4. **Enter Production:**
   - Begin collaborative scene writing
   - Use AI assistance for dialogue, pacing, and consistency

### Example Usage Session

```
Author: I want to write a sci-fi novel about orbital habitats after Earth's collapse
AI: Let's start the capture stage. Tell me about your protagonist and the world they inhabit...

[Brainstorming session with idea-generator and wildcard-generator]

AI: Now let's distill these ideas. The story-architect will create a three-act structure...

[Outline development with scene-architect]

AI: Ready for production? Let's write the opening scene together...

[Collaborative writing with writer-author and dialogue-expert]
```

## 📚 Story Theory Foundations

Story Foundry is built upon established writing methodologies:

- **Story Grid** (Shawn Coyne): Genre conventions and story structure analysis
- **Scene & Structure** (Jack Bickham): Scene-sequel narrative construction  
- **Story Genius** (Lisa Cron): Character-driven story development
- **Anatomy of Story** (John Truby): Character development and story architecture

## 🎨 Key Features

- **Voice Preservation**: Maintains author's unique style throughout the process
- **Session Memory**: Comprehensive recording of all creative sessions
- **Multi-Project Support**: Work on multiple novels simultaneously
- **Structured Creativity**: Balances creative freedom with proven story structure
- **Iterative Refinement**: Continuous improvement through editing cycles
- **Research Integration**: Built-in access to story theory resources

## 🔄 Workflow Philosophy

Story Foundry operates on the principle that great novels emerge from a balance of:
- **Creative Inspiration** (Capture stage)
- **Structural Discipline** (Distillation stage)  
- **Collaborative Craftsmanship** (Production stage)

The system respects the author's creative autonomy while providing expert guidance and structure to transform ideas into compelling, publishable novels.

## 📋 Current Status

Story Foundry is in active development with:
- ✅ Core framework and agent system
- ✅ Capture stage workflow
- ✅ Project initialization system
- 🚧 Distillation stage implementation
- 🚧 Production stage implementation
- 🔄 Ongoing refinement based on author feedback

## 🤝 Contributing

Story Foundry welcomes contributions from writers, developers, and story theory experts. Whether you're interested in improving the agent system, expanding story theory integration, or enhancing the user experience, your expertise can help make novel writing more accessible and successful.

---

*Story Foundry: Where AI meets artistry in the craft of storytelling.*