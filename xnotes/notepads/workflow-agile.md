---
Notepad Name: workflow-agile
---
# Agile Workflow Rules

**CRITICAL**: All project memory stored in `.ai/` folder. Follow this EXACT sequence.

## Required Sequence - NO DEVIATIONS ALLOWED

1. FIRST: Verify `.ai/prd.md` exists
   - If missing: Create with user using `.cursor/templates/template-prd.md`
   - MUST include ALL required sections (1-10)
   - MUST define Epics in Section 6 with clear sequence
   - MUST list Stories for current Epic in Section 7
   - STOP all other work until PRD is `status: approved`

2. AFTER PRD approval ONLY: Create `.ai/arch.md`
   - Use `.cursor/templates/template-arch.md` exactly
   - MUST include ALL required sections (1-8)
   - MUST include technology table and mermaid diagrams
   - MUST document project structure
   - STOP all other work until ARCH is `status: approved`

3. AFTER ARCH approval ONLY: Setup epics
   - Create `.ai/epic-{n}/` directories for each Epic in PRD
   - Work on EXACTLY ONE epic at a time, in PRD-defined order
   - Track epic status in PRD Section 6 (Complete, Current, Future)

4. FOR EACH epic (one at a time):
   - Create first story: `.ai/epic-{n}/story-{m}.story.md`
   - Use `.cursor/templates/template-story.md` exactly
   - WAIT for explicit story approval before implementation
   - Work on EXACTLY ONE story at a time
   - Use TDD - ALL tests MUST pass before completion
   - Update story file after EACH subtask completion
   - Only mark story as complete when the user confirms
   - After story completion, create next story in current epic
   - Update ARCH change log for architectural changes
   - Mark epic Complete in PRD ONLY when ALL stories complete
   - Update PRD Section 7 with stories for next Current epic

5. REPEAT until all epics complete

## Automatic Actions (No User Permission Required)

1. Create next story when previous completes
2. Run tests during development
3. Update story tasks as completed
4. Record implementation notes in story files
5. Update epic status in PRD as stories complete
6. Update ARCH change log for architectural changes

## Version Control Integration

- NEVER work directly on `main` or `develop` branches
- ALWAYS create a new branch for each story following pattern:
  - `feature/epic-{n}-story-{m}-{short-name}` for features
  - `fix/epic-{n}-story-{m}-{short-name}` for bug fixes
- Create branch from `develop` before starting any implementation
- ALWAYS follow Git Workflow Standards for ALL code changes
- Update story status when branches are created and merged
- Include Git branch information in story files
