# Unity Design System + Dyad Integration Checklist

This document outlines the steps needed to configure Dyad to work excellently with the Unity Design System for rapid Angular prototyping with clients.

## Phase 1: Documentation & Knowledge Gathering

### Unity Documentation Audit
- [ ] Export complete component API documentation from Storybook (JSON or Markdown)
- [ ] Document all Unity component props, events, and usage patterns
- [ ] Capture Design Token structure and theme customization approach
- [ ] List all available Unity components with one-line descriptions
- [ ] Document Unity-specific patterns (form validation, layout utilities, accessibility helpers)
- [ ] Capture common component composition patterns from kitchen-sink examples
- [ ] Document Font Awesome integration approach and available icons

### Angular Project Structure
- [ ] Document typical Aptia Angular project structure
- [ ] Identify common module organization patterns
- [ ] Document routing conventions
- [ ] Capture state management approach (signals, RxJS, NgRx, etc.)
- [ ] Document build and deployment patterns

### Accessibility Requirements
- [ ] List WCAG 2.1 requirements Unity enforces
- [ ] Document common a11y patterns in Unity components
- [ ] Capture keyboard navigation patterns
- [ ] Document ARIA usage conventions

---

## Phase 2: Dyad System Prompt Configuration

### Core Prompt Modifications (`src/prompts/system_prompt.ts`)
- [ ] Add Unity Design System overview section
- [ ] Specify Unity component preference over Angular Material
- [ ] Include component naming conventions
- [ ] Add theming and customization guidelines
- [ ] Include accessibility-first development principles
- [ ] Add Font Awesome icon usage patterns
- [ ] Specify standalone component approach
- [ ] Include RxJS and reactive programming patterns
- [ ] Add bundle size optimization reminders
- [ ] Include performance best practices

### Example Code Snippets
- [ ] Create 5-10 "golden examples" of Unity component usage
- [ ] Add form implementation patterns
- [ ] Include layout/grid patterns
- [ ] Add navigation patterns
- [ ] Include data table examples
- [ ] Add modal/dialog patterns
- [ ] Include loading/error state patterns

---

## Phase 3: MCP (Model Context Protocol) Integration

### Option A: File-Based MCP (Simpler)
- [ ] Create curated Unity documentation folder structure
- [ ] Export Storybook docs to Markdown/JSON
- [ ] Set up MCP filesystem server pointing to Unity docs
- [ ] Configure Dyad to use MCP server
- [ ] Test retrieval of component documentation

### Option B: GitHub MCP (More Dynamic)
- [ ] Set up GitHub MCP server with Unity repo access
- [ ] Configure authentication (GitHub token with repo read access)
- [ ] Define which files/folders Claude should access
- [ ] Test retrieval from private Unity repo
- [ ] Set up caching strategy for performance

### MCP Resources to Expose
- [ ] Component library documentation
- [ ] Storybook stories as reference examples
- [ ] Kitchen-sink application code
- [ ] Design tokens configuration
- [ ] Theme customization guide
- [ ] Accessibility testing results/patterns

---

## Phase 4: Dyad Custom Tool Configuration

### Unity-Specific Tools (if needed)
- [ ] Create Unity component scaffolding tool
- [ ] Add Design Token lookup tool
- [ ] Create accessibility checker integration
- [ ] Add Storybook link generator

### Existing Tool Enhancements
- [ ] Configure `<dyad-write>` templates for Unity components
- [ ] Set up linting rules for Unity conventions
- [ ] Configure TypeScript paths for Unity imports

---

## Phase 5: Development Workflow Integration

### Environment Setup
- [ ] Document Font Awesome token setup process
- [ ] Create `.env.example` for Unity project requirements
- [ ] Document Unity npm registry authentication
- [ ] Set up local Unity development environment guide

### Dyad Hooks Configuration
- [ ] Add pre-commit hook for Angular linting
- [ ] Add post-write hook to run TypeScript checks
- [ ] Add hook to validate Unity component imports
- [ ] Add hook to check accessibility violations (if tooling exists)

### Slash Commands (optional custom commands)
- [ ] `/unity-component <name>` - Scaffold Unity component usage
- [ ] `/unity-docs <component>` - Fetch component documentation
- [ ] `/unity-example <pattern>` - Show kitchen-sink example

---

## Phase 6: Knowledge Base Creation

### Quick Reference Materials
- [ ] Create "Unity Cheat Sheet" with most-used components
- [ ] Document 10 most common prototyping patterns
- [ ] Create troubleshooting guide for common issues
- [ ] List Unity vs Angular Material component equivalents
- [ ] Document performance optimization checklist

### Client Prototyping Scenarios
- [ ] Document typical Mercer use cases
- [ ] Document typical Aptia use cases
- [ ] Create starter templates for common prototypes (dashboard, form, data table view)
- [ ] Document rapid iteration workflow with clients

---

## Phase 7: Testing & Validation

### Test Cases
- [ ] Generate simple Unity form component
- [ ] Generate data table with Unity components
- [ ] Generate responsive layout with Unity grid
- [ ] Generate accessible modal dialog
- [ ] Generate themed component variant
- [ ] Test Design Token customization
- [ ] Test Font Awesome icon integration

### Validation Criteria
- [ ] Generated code uses correct Unity imports
- [ ] Components follow Unity API patterns
- [ ] Accessibility attributes are correct
- [ ] TypeScript types are accurate
- [ ] Code follows standalone component pattern
- [ ] Bundle optimization patterns are applied

---

## Phase 8: Documentation for Your Team

### For Designers/PMs
- [ ] Document what Dyad can/can't do with Unity
- [ ] Create workflow guide for client prototyping sessions
- [ ] Document how to request component modifications
- [ ] Create demo video of Dyad + Unity in action

### For Developers
- [ ] Document system prompt customization process
- [ ] Document MCP setup and maintenance
- [ ] Create contribution guide for adding Unity patterns
- [ ] Document troubleshooting common issues

---

## Priority Quick Start (Minimum Viable Integration)

If time is limited, start here:

### Week 1: Foundation
1. [ ] Get complete component list with descriptions from Unity Storybook
2. [ ] Export 10 most-used component examples from kitchen-sink
3. [ ] Add basic Unity overview to Dyad system prompt
4. [ ] Test generation of simple Unity component

### Week 2: MCP Setup
5. [ ] Set up file-based MCP with Unity docs
6. [ ] Configure Dyad to use MCP server
7. [ ] Test retrieval and generation

### Week 3: Refinement
8. [ ] Add 5 golden example patterns to system prompt
9. [ ] Create Unity cheat sheet
10. [ ] Run validation tests with real prototype scenarios

---

## What You Need From Unity Dev Team

### Critical
- Complete component API documentation (ideally Storybook JSON export)
- 10-15 kitchen-sink examples covering common patterns
- Design Token documentation
- Unity project setup guide

### Nice to Have
- Read access to Unity repo (for GitHub MCP)
- Accessibility testing documentation
- Common composition patterns guide
- Performance optimization patterns

### Ongoing
- Feedback channel for when Dyad generates incorrect Unity patterns
- Updates when Unity adds new components or changes APIs
