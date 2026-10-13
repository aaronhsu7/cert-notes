# Claude Platform & Model Foundations

## What to expect from Gen AI
There are 5 behavioral properties that apply to Claude regardless of which feature you use.
1. Responses vary: Ask the same question twice and get two different answers, outputs are produced using probability as opposed to retrieved from a fixed database.
2. Confident tone is not a signal of accurracy: Fluency doesn't signal accuracy.
3. Context is a budget: working-memory limit, claude.ai will automatically summarize earlier messages so the session can conitue on.
4. Knowledge has a training boundary: Claude's training data has a cutoff date. Information outside that date is unreliable unless you connect to a current course/online.
5. Configured procedures still produce varied outputs: A skill set to run the same procedure every time reduces output variance but does not eliminate it. You always need to check output.

## 1 interface with 4 distinct working entry points
### Chat:
The default entry point, an unstructured conversation. Doesn't give you a Project's deliberate persistence, standing instructions and a curated knoweldge base. One session use-case.

### Projects:
Persistent workspaces with 3 things:
1. Standing Instructions: What Claude should know and do consistently across every conversation in this space.
2. Knowledge Base: Documents, policies, and reference files uploaded once so Claude can draw on them without re-uploading each session
3. Conversation History: Each project maintains its own conversation list, separate from your global conversation history. Conversations within a project share instruction and knowledge base but not context with each other.
***The task recurs, the background context is stable, and the output format is consistent***

### Artifacts: 
The right output format when the result is a deliverable rather than a conversational reply. Appears as a separate editable block alongside the chat rather than flowing into the convresation thread.

### Research: 
Enables deep multi-source synthesis. Regular Chat can search the web, Team/Enterprise can enable it. 

## 4-layer model:
Projects carry context, skills define procedures, code execution verifies computations, memory persists continuity. All the layers are independent.

### Skills: 
Reusable procesures (editing Excel, word docs, powerpoint), but you can also add custom ones for task-specific workflows. They live at the account level not just inside any one project. 
Skills reduce variance, but do not eliminate. They also require a trust evaluation because they have access to whatever you give Claude access to during the session. 

### Code Execution: 
Sandboxed computation environment. Claude writes and runs code internally and then returns the result. It provides a verified result by running calculations. 

## Memory:
Work-relevant facts across sessions. Make sure to actively curate it to prevent having outtdated memory.
- Project-scoped memory
- Incognito mode to keep a session out of memory and chat history

## Models:

### Haiku:
The fastest and most efficient model (classification, extraction, formatting, straightforward summarization, high-volume routine work) where speed matters and cost of an imperfect output is low. 

### Sonnet:
Balanced tier; full range of tasks with strong quality.

### Opus:
Higher-capability tier, offering more advanced performance. Nuanced judgement, complex multi-step reasoning, and quality outranking speed.

### Context Limit:
Working-memory limit, Claude's context window fills -> stops following instructions it followed correctly earlier, response addresses only the most recent exchange without reference, accuracy drops in ways that are consistent with missing early-session context. 
- Restart: start a new conversation
- Summarize: Produce a summary of the current state
- Persist: Save it to memory or update the Project knowledge base. 

# Prompting and Task Execution
 The component stack:
 1. Role: Who you want Claude to be for this task
 2. Context: The background Claude cannot know unless you provide it
 3. Task: The specific action stated as a clear instruction
 4. Constraints: The boundaries: length, tone, and what to include/avoid.
 5. Output format: THe shape of the result
 
## Task Decomposition for Complex Requests
Decomposition: Splitting a multi-part problem into discrete, ordered steps, then running them in sequence rather than asking for everything at once.
- Iteration: A first draft from Claude rarely lands perfectly; the skill is not rewriting the whole prompt when output disappoints, it is reading hte output to diagnose which component fell short, then fixing that one thing.
- Iteration has converged when each additional round produces marginal change rather than improvement. At that point, further prompting yields less than a quick manual edit. Recognizing diminishing returns is part of the skill.

## Adapting Strategy by Task Type:
1. Analysis: Wants tigh constraints and explicit criteria (what to measure against what standard, and handle ambiguity). Low creative latitude, high specification.
2. Research: Wants clear scope and source discipline. Define the question, the boundaries, and whether current sources are required. Ask for citations.
3. Drafting: Wants audience, tone, and format specified, with room for Claude to find the phrasing. Medium latitude: you control the shape, Claude fills it. 
4. Brainstorming: Wants loose constraints and high latitude. Over-specifying kills the divergence you are after. Give the goal and the boundaries, then ask for volume and range before you narrow. 

# Evaluating and Validating Claude's Output:
2 main competencies from the AI Fluency Framework:
1. Discernment: The skill of critically evaluating output against requirements, sources, and standards. *How you review*
2. Diligence: Deciding when veritifcation is required and taking responsibility for the result. *Why you review*

## Discrenment: Evaluating Accuracy, Completeness, and Fitness
1. Requirements: Does the output reflect what you asked for?
2. Source Material: Where the output relies on the documents you supplied, does it match them? Trace specific claims back to the source rather than trusting that Claude read carefully
3. Professional Standards: Would this pass in your field? Check standards.

Stakes Calibration: How deeply you review depends on the stakes; domain-dependent. 
1. Ready to use: meets requirements, matches sources, professional standards. Ship it.
2. Needs revision: Close, but a specific gap remains to note and iterate.
3. Needs human overried: The stakes, the errors, escalate to human.

Accuracy vs. Completeness: they fail independently. Review for both.

## Hallucination Patterns:
- Plausible-but-unsupported claims: A statement that sounds reasonable and fits the topic, with no basis in the source or in fact.
- Fabricated specifics: Invented stats, reads as authority, and is persuasive.
- Confident tone masking uncertainty: Claude rarely hedges in proportion to its actual certainty. A guess and well-grounded fact arrive in the same assured voice. 

## Inconsistencies and Bias: 
- Internal Contradictions: In a long output, a claim early on can conflict with one later. Long documents are where contradictions hide.
- Confirmation bias in framing: If your prompt implies a preferred answer, Claude may lean towards it.

## Fact-Checking and Grounding Techniques:

Prompt for verifiability
- Permit "I don't know"
- Restrict to provided sources
- Require auditable citations

Grounding techniques
- Quote first then analyze
- Best-of-N comparison: Re-run the same request and compare, when the runs agree confidence rises
- Validate against authoritative sources: For claims that matter, check against a trusted external reference rather than a second claude response

Verbatim Prompts: Each technique is a phrase you can paste, the wording is the skill
- Permission to not know
- Source restriction
- Auditable citation
- Quote-grounding

## Diligence: When Human Review is non-negotiable
Knowing thresholds in advance, so the decision to escalate is made by policy not in the moment after something has already gone wrong. There are 4 risk thresholds
1. Stakes: What is the cost if this is wrong?
2. Reversibility: Can the action be undone?
3. Audience: Who sees it?
4. Regulatory Exposure: Does a rule, contract, or law govern this?

Three escalation scenarios: The fast "yes", the deceptive "looks fine", and the slow creep.

## Editing and Adapting Output for your audience:
1. Clarity: Cut hedging, tighten loose sentences, remove anything that does not earn its place
2. Tone: Match the register to the relationship and the occasion
3. Formatting: Shape the output for how it'll be read
- Note audience calibration
- Comparing outputs before you edit

## Choosing Output formats:
1. Inline: For conversational responses you will act on within the chat (quick, contextual, not standalone)
2. Artifacts: For documents and code: a separate, editable block you will refine and use (Deliverable)
3. Structured Formats: For data: tables and schemas that downstream tools/readers can consume directly

# Workflow Integration and Solution Design
Our workflow uses Claude: Repeatable process, run by a team, where Claude performs specific steps every time
Delegation: Deciding, for each step, whether the work is AI-appropriate, human-retained, or collaborative

## Analyzing Requirements and Use Cases with Claude:
Extraction first pass, pressure-testing next is what makes the output trustworthy

Research and Synthesis: Claude can synthesize across sources to develop a plan

## Solution Design, Development & Iteration:
Treating it as a loop, and keeping the design context stable across iterations. Ideation produces options, prototype makes on concrete, feedback exposes what is wrong; refinement fixes it; and the loop repeats until the solution holds. Running this inside a project keeps the context/constraints so each iteration builds on the last.

## Delegation Mapping: Redesigning workflows with Claude inside:
1. Reversbility: Can it be undone? Reversible tolerate more delegation; irreversible demand human involvement
2. Stakes: What is the cost of an error at this step
3. Accountability: Who is answerable for this step's outcome

- Skill for repeatable procedure steps, code execution for data steps

Describe capability accurately: State what Claude can do for the use case and what it cannot, without inflation or false modesty

# Configuration & Knowledge Management:
Configuration is leverage: you set it up once and benefit from it on every conversation that follows. Maintenance means well-configuring the environment deliberately and reviewing on a cadence.
1. Standing instructions: How Claude should behave across every conversation in the Project: tone, format defaults, verification habits. Behavior, not facts.
2. Knowledge base: The documents, policies, and reference files Claude should draw on without re-uploading. Facts and reference, not behavior. 
3. Skills: REpetable procedures Claude should follow consistentyl for a task type: Procedure, not one-off instruction. Skills live at the accoutn level under customize, not inside any one Project, a Skill you build is reusable across any Project that needs it.
4. Scoped Memory: Continuity within the Project, kept separate from your other Projects so context does not bleed between workstreams.

Connector: Let's Claude reach an external system you authorize
- Each connector has a defined boundary and knowing it prevents wasted time

## System-Level instructions that stick: 
- Write the guardrails once, now the discipline applies to every conversation without anyone remembering it
Anticipate the use cases: format, tone, and guardrail guidance ahead of need

## Maintaining Configurations: