System Boundaries

This document defines the canonical system boundaries and interaction model for Frankendash, FrankEngine, and D.libber.

Components

Frankendash = Bones

Frankendash is the interface and workspace layer.

Responsibilities:

* UI
* Workspace surfaces
* Navigation
* Dashboards
* User interactions
* Workflow visibility
* Project and task presentation
* Status and progress surfaces

Frankendash should present and collect information, but it should not own core reasoning, orchestration logic, or persistent system state.

FrankEngine = Brain

FrankEngine is the reasoning and orchestration layer.

Responsibilities:

* Reasoning
* Workflow orchestration
* Workflow rules
* Project-preparation triggers
* Automation
* Decision logic
* Scope and readiness evaluation
* Coordination between the interface, library layer, and connected tools

FrankEngine decides what should happen next and coordinates execution.

D.libber = Library / Persistence Layer

D.libber is the structured library and persistence layer.

Responsibilities:

* Persistent state
* Structured records
* Relationships
* Project and workspace metadata
* Workflow status and history
* Canonical references and identifiers
* Stored outputs required by FrankEngine and Frankendash
* Searchable workspace knowledge
* Organized project and document references
* Library-style retrieval and organization

D.libber stores and organizes system knowledge and state.

It does not own reasoning or interface behavior.

The underlying database or storage implementation may change later without changing D.libber’s role in the architecture.

Interaction Model

Frankendash
    ↓
FrankEngine
    ↓
D.libber
    ↓
FrankEngine
    ↓
Frankendash

Typical flow:

1. The user interacts with Frankendash.
2. Frankendash sends the action and relevant context to FrankEngine.
3. FrankEngine interprets the request and determines the required workflow.
4. FrankEngine reads from or writes to D.libber as needed.
5. D.libber stores, organizes, and retrieves the required state or knowledge.
6. FrankEngine returns the resulting state, actions, or outputs.
7. Frankendash presents the result to the user.

Brainstorming and Planning Pipeline

Idea Explorer
→ Ready
→ FrankEngine trigger
→ Project-preparation workflow
→ Docs / indexes / tasks
→ Formal planning
→ Build gate
→ Build

Ready State

Ready does not mean “start building.”

Ready means the idea has been refined enough for FrankEngine to begin project preparation.

The project-preparation workflow may include:

* Creating the project record
* Creating the canonical project index
* Generating required project documents
* Creating task structures
* Creating or linking workspace folders
* Linking relevant repositories
* Updating master indexes
* Preserving the source brainstorm
* Recording scope, constraints, unknowns, and next actions
* Registering new project resources in D.libber

Only after project preparation and formal planning should the project be eligible to pass the build gate.

Boundary Rule

Frankendash presents. FrankEngine decides and orchestrates. D.libber stores and organizes.

These boundaries should remain stable even if the underlying implementation of any component changes.