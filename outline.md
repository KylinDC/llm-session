This is the revised Slidev-compatible English outline. It is structured to be technical yet practical, focusing on the mental models a developer needs to build LLM applications.
Presentation: From Autoregression to MCP
Sub: Mastering the Context, Tools, and Skills of LLM Development
Part 1: The Foundations
Page 1: Title Slide
 * Title: Beyond the Chatbox: Autoregression, Context, and MCP
 * Subtitle: A Programmer's Guide to the LLM Stack
 * Footer: [Your Name] | [Date]
Page 2: Agenda
 * The Atom: Tokens & The "Strawberry" Problem
 * The Resource: Context Windows & Management
 * The Hands: Tool Use (Web Search & Code Gen)
 * The Protocol: MCP (Model Context Protocol)
 * The Evolution: From Tools to Skills & Workflows
Page 3: Tokens — The "Atom" of LLMs
 * Why LLMs don't "see" text: Byte Pair Encoding (BPE).
 * The "Strawberry" Case Study:
   * Why can't GPT-4 count 'r's in "strawberry"?
   * Explanation: The tokenizer splits it into straw + berry or str + aw + berry. The model sees IDs, not individual letters.
 * Dev Takeaway: Tokenization affects logic, math, and string manipulation.
Page 4: Autoregression — The Completion Loop
 * Core Logic: P(Token_{n+1} | Context).
 * The Loop: LLM is a recursive function where the output of T_n becomes the input for T_{n+1}.
 * Deterministic vs Probabilistic: Understanding temperature and sampling.
Page 5: Context Window — The Finite Frontier
 * The "Filling Up" Problem: Why 200k tokens vanish quickly.
   * System Instructions + Chat History + RAG Results = Context Exhaustion.
 * The "Lost in the Middle" Phenomenon:
   * Models are better at recalling info from the very beginning or very end of the prompt.
   * Performance dips significantly for data buried in the center.
 * Dev Takeaway: Don't just dump data; prioritize and prune.
Part 2: Interacting with the Model
Page 6: The API Evolution
 * Completion API: The raw "predict the next word" engine.
 * Chat Completion API: Structured roles (system, user, assistant).
 * The Shift: Engineering the Prompt \rightarrow Engineering the Context.
Page 7: Context Engineering
 * RAG (Retrieval Augmented Generation): Bringing external memory.
 * State Management: Summarization, sliding windows, and caching.
Part 3: Extending Capability (Tool Use)
Page 8: Tool Use API — Giving the Model "Hands"
 * Mechanism: The model doesn't "run" code; it generates a structured JSON "intent."
 * Loop: Model (Intent) \rightarrow Client (Execution) \rightarrow Model (Observation).
Page 9: Tool Examples in Practice
 * Web Search Tool: Bringing real-time data into the autoregressive loop.
 * Code Generation Tool:
   * Model writes Python \rightarrow Sandbox executes \rightarrow Result returns to Model.
   * Used for complex math or data visualization where LLM logic fails.
Part 4: The Protocol Era (MCP)
Page 10: MCP — The "USB-C" for AI
 * The Problem: Custom integrations for every tool (Figma, GitHub, Postgres) across every LLM client.
 * The Solution: Model Context Protocol.
 * Architecture: Client \leftrightarrow Host \leftrightarrow Server.
Page 11: MCP in Action
 * Figma MCP: Connecting the model to live design tokens and layers.
 * Context7 MCP: Structured business context and relationship mapping.
 * Key Benefit: Standardizing how models "fetch" context from the real world.
Page 12: Scaling Context & Skills
 * Context Expansion via MCP: Dynamic fetching. Instead of shoving 100 files into a prompt, MCP lets the model "query" only the relevant file.
 * Progressive Disclosure of Skills:
   * Don't tell the model every tool you have at the start.
   * Only expose tool definitions (Skills) based on the user's intent to save context space.
Part 5: Real-world Implementation
Page 13: Case Study: Windsurf IDE Paradigm
 * Rules (.windsurfrules): Global context and constraints for the Agent.
 * Skills: Atomic actions (e.g., list_files, run_test).
 * Workflow: The "Agentic" orchestration.
   * Example: "Refactor this React component" involves: Rule (Coding Style) \rightarrow Skill (Read File) \rightarrow Skill (Execute Linter) \rightarrow Skill (Write File).
Page 14: Summary & Q&A
 * Key Shift: From "Prompting" to "Protocol-driven Engineering."
 * Next Step: Build an MCP server for your own team's internal tools.
Next Step for You:
Would you like me to generate the Mermaid.js sequence diagram code for the MCP Client-Server interaction or the Tool Use Loop to include in these slides?

