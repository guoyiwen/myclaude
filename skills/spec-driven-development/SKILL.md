---
name: spec-driven-development
description: Systematic three-phase approach to feature development using Requirements, Design, and Tasks phases. Transforms vague feature ideas into well-defined, implementable solutions that reduce ambiguity, improve quality, and enable effective AI collaboration.
license: MIT
compatibility: Claude Code, Cursor, VS Code, Windsurf
metadata:
  category: methodology
  complexity: intermediate
  author: Kiro Team
  version: "1.0.0"
---

# Spec-Driven Development

A comprehensive methodology for systematic software feature development that ensures quality, maintainability, and successful delivery through structured planning.

## Workflow Overview

This skill guides you through creating a structured specification in the `.kiro/specs` directory:

```
.kiro/specs/
└── <feature-name>/
    ├── requirements.md
    ├── design.md
    └── tasks.md
```

**File Creation Rules:**
- All spec files are created under `.kiro/specs/<feature-name>/` in the current project directory
- `<feature-name>` should be a kebab-case identifier for the feature being developed
- Each phase creates its corresponding markdown file when completed

## When to Use This Skill

**Ideal scenarios:**
- Complex features with multiple components, integrations, or user interactions
- High-stakes projects where rework costs are significant
- Team collaboration requiring shared understanding
- AI-assisted development where clear structure improves output quality
- Knowledge preservation for future maintainers

**Less suitable:**
- Simple bug fixes with obvious solutions
- Experimental prototypes for rapid iteration
- Time-critical hotfixes requiring immediate action
- Well-established patterns with minimal ambiguity

## The Three-Phase Workflow

### Phase 1: Requirements Gathering

**Purpose:** Transform vague feature ideas into clear, testable requirements

**Process:**
1. Capture user stories expressing value and purpose
2. Define acceptance criteria using EARS format (Easy Approach to Requirements Syntax)
3. Identify edge cases and constraints
4. Validate completeness and feasibility

**EARS Format Patterns:**
```
WHEN [event] THEN [system] SHALL [response]
IF [precondition] THEN [system] SHALL [response]
WHEN [event] AND [condition] THEN [system] SHALL [response]
```

**Example:**
```markdown
**User Story:** As a new user, I want to create an account, so that I can access personalized features.

**Acceptance Criteria:**
1. WHEN user provides valid email and password THEN system SHALL create new account
2. WHEN user provides existing email THEN system SHALL display "email already registered" error
3. WHEN user provides password shorter than 8 characters THEN system SHALL display "password too short" error
4. WHEN account creation succeeds THEN system SHALL send confirmation email
```

### Phase 2: Design Documentation

**Purpose:** Create a comprehensive technical plan for implementation

**Process:**
1. Research technical approaches and constraints
2. Define system architecture and component interactions
3. Specify data models and interfaces
4. Plan error handling and testing strategies

**Design Document Structure:**
```markdown
## Overview
[High-level summary of approach]

## Architecture
[System components and their relationships]

## Components and Interfaces
[Detailed component descriptions]

## Data Models
[Data structures and validation rules]

## Error Handling
[Error scenarios and response strategies]

## Testing Strategy
[Testing approach for different layers]
```

**Decision Documentation:**
```markdown
### Decision: [Title]
**Context:** [Situation requiring decision]
**Options Considered:**
1. [Option 1] - Pros: [benefits] / Cons: [drawbacks]
2. [Option 2] - Pros: [benefits] / Cons: [drawbacks]
**Decision:** [Chosen option]
**Rationale:** [Why this was selected]
```

### Phase 3: Task Planning

**Purpose:** Break design into actionable, sequential implementation steps

**Process:**
1. Convert design elements into specific coding tasks
2. Sequence tasks to enable incremental progress
3. Define clear objectives and completion criteria
4. Reference requirements for traceability

**Task Structure:**
```markdown
- [ ] 1. [Epic/Major Component]
- [ ] 1.1 [Specific implementation task]
  - [Implementation details]
  - [Files/components to create]
  - _Requirements: [Requirement references]_
```

**Task Sequencing Strategies:**
- **Foundation-First:** Core interfaces before dependent components
- **Feature-Slice:** End-to-end vertical slices for early validation
- **Risk-First:** Tackle uncertain areas early
- **Hybrid:** Combine approaches based on project needs

## Quality Checklists

### Requirements Checklist
- [ ] All user roles identified and addressed
- [ ] Normal, edge, and error cases covered
- [ ] Requirements are testable and measurable
- [ ] No conflicting requirements
- [ ] EARS format used consistently

### Design Checklist
- [ ] All requirements addressed in design
- [ ] Component responsibilities well-defined
- [ ] Interfaces between components specified
- [ ] Error handling covers expected failures
- [ ] Security considerations addressed

### Tasks Checklist
- [ ] All design components have implementation tasks
- [ ] Tasks ordered to respect dependencies
- [ ] Each task produces testable code
- [ ] Requirements references included
- [ ] Scope is appropriate (2-4 hours each)

## Integration with AI Workflows

**For Claude Code / AI Assistants:**

1. **Start with context:** Provide project background, constraints, and goals
2. **Work in phases:** Complete requirements before design, design before tasks
3. **Create files:** Each phase should create/update its corresponding markdown file in `.kiro/specs/<feature-name>/`
4. **Iterate:** Refine outputs through conversation rather than single requests
5. **Validate:** Ask AI to review outputs against checklists
6. **Trace:** Maintain links between requirements, design, and tasks

**Example prompt for starting a spec:**
```
I'm working on [project context]. We need to add [feature description].

Context:
- Technology: [stack]
- Users: [target audience]
- Constraints: [key limitations]

Please help me develop requirements using the EARS format, starting with user stories and acceptance criteria. Create the spec files in .kiro/specs/<feature-name>/ directory.
```

## File Creation Instructions

### Starting a New Spec

When beginning a new feature specification:

1. **Create the spec directory:**
   ```
   .kiro/specs/<feature-name>/
   ```

2. **Phase 1 - Requirements:**
   - Create `.kiro/specs/<feature-name>/requirements.md`
   - Document user stories, acceptance criteria (EARS format), edge cases, and constraints

3. **Phase 2 - Design:**
   - Create `.kiro/specs/<feature-name>/design.md`
   - Document architecture, components, data models, error handling, and testing strategy

4. **Phase 3 - Tasks:**
   - Create `.kiro/specs/<feature-name>/tasks.md`
   - Break down implementation into actionable, sequential tasks with requirement references

### Template: requirements.md

```markdown
# Requirements: [Feature Name]

## 用户故事

### [故事标题]
**作为** [用户角色]
**我想要** [操作/功能]
**以便** [价值/收益]

## 验收标准（EARS 格式）

1. 当 [事件] 发生时，系统 应当 [响应]
2. 如果 [前置条件]，系统 应当 [响应]
3. 当 [事件] 发生且 [条件] 满足时，系统 应当 [响应]

## 边界情况

- [边界情况 1]
- [边界情况 2]

## 约束条件

- [约束 1]
- [约束 2]

## 非功能性需求

- 性能：[需求说明]
- 安全性：[需求说明]
- 兼容性：[需求说明]
```

### Template: design.md

```markdown
# Design: [Feature Name]

## Overview
[High-level summary of approach]

## 架构
[系统组件及其关系]

## 组件与接口

### [组件名称]
- **用途：** [描述]
- **接口：** [方法/API]
- **依赖：** [其他组件]

## 数据模型

### [模型名称]
```typescript
[类型定义]
```

## 错误处理
[错误场景和响应策略]

## 测试策略
- 单元测试：[方法]
- 集成测试：[方法]
- 端到端测试：[方法]

## 设计决策

### 决策：[标题]
**背景：** [需要决策的情况]
**考虑的选项：**
1. [选项 1] - 优点：[优势] / 缺点：[劣势]
2. [选项 2] - 优点：[优势] / 缺点：[劣势]
**决策：** [选择的选项]
**理由：** [选择该选项的原因]
```

### Template: tasks.md

```markdown
# Tasks: [Feature Name]

## Implementation Tasks

- [ ] 1. [史诗/主要组件]
  - [ ] 1.1 [具体实现任务]
    - 详情：[实现说明]
    - 文件：[要创建的文件/组件]
    - 需求：[需求引用]
  - [ ] 1.2 [另一个任务]
    - 详情：[实现说明]
    - 文件：[要创建的文件/组件]
    - 需求：[需求引用]

- [ ] 2. [另一个史诗]
  - [ ] 2.1 [任务]
    - 详情：[实现说明]
    - 文件：[要创建的文件/组件]
    - 需求：[需求引用]

## 任务说明

- **排序：** 任务按依赖关系排序
- **估算：** 每个任务设计为 2-4 小时完成
- **追溯：** 每个任务关联相关需求
```

## Common Pitfalls to Avoid

1. **Skipping phases:** Each phase builds on the previous; shortcuts create problems
2. **Vague requirements:** "System should be fast" vs specific, measurable criteria
3. **Implementation details in requirements:** Focus on what, not how
4. **Over-engineering design:** Solve current requirements, not hypothetical future ones
5. **Monolithic tasks:** Break down into 2-4 hour increments
6. **Missing error cases:** Always consider what happens when things go wrong

## Next Steps

After completing a spec:
1. The spec files are ready in `.kiro/specs/<feature-name>/`
2. Begin implementation following the task sequence in `tasks.md`
3. Track progress by marking tasks complete in `tasks.md`
4. Update spec files if implementation reveals gaps
5. Validate completed work against `requirements.md`
6. Document learnings for future specs
