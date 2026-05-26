2025-10-05T10:07
## Contents
1. AI agent is an LLMs autonomously using tools (either function tools or other agent) in a loop, until the target task is completed. 
2. In the loop of the AI agent, it uses tools to get relevant contents, puts the contents into their context window, to achieve the target. Therefore the context engineering is important
	1. The context window is limited (1M for Claude, for example.)
	2. The context should be relevant; otherwise it is not useful.
	3. The context should be precise; otherwise long context distracts the agent and degrades the performance.
3. How to have a precise and relevant context?
	1. System prompt: Antrhopic suggests write the prompt describing the behavior you want (what), but not describing how to achieve those behavior (how). Antrhopic suggests organizing prompts into distinct sections (like "background information", "instruction", "tool guidance", "output description"). In the end of your system prompt, provide a cover a set of diverse, canonical behavior that effectively portray the expected behavior of the agent.
	2. Tools: tools should be self-contained, robust to error, and extremely clear with respect to their intended use. One of the most common failure modes we see is bloated tool sets that cover too much functionality or lead to ambiguous decision points about which tool to use. 
	3. Providing tool usage example: - **Prioritize descriptions over examples.** While you can include examples of how to use a tool in its description or in the accompanying prompt, this is less important than having a clear and comprehensive explanation of the tool’s purpose and parameters. Only add examples after you’ve fully fleshed out the description. (https://docs.claude.com/en/docs/agents-and-tools/tool-use/implement-tool-use#specifying-client-tools)
4. Context engineering for long-horizon tasks. The blog proposes three strategies to deal with it.
	1. Compaction: summarize the long context into a smaller one. Low-hanging fruit: tool calls results. We only need to keep the agent result after seeing the tool calls results.
	2. Structure note-taking: long-term memory, this is like the note taken from a student for a class. The student can review the notes that serves as an external memory.
		1. For human, when taking notes, they also learns materials in their brain. For LLM it is stateless and no memory.
	3. Sub-agent architectures: separation of concerns. The main agent coordinates with a high-level plan while subagents perform deep technical work and has details in their context window. 

## Reference

https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
https://www.anthropic.com/engineering/writing-tools-for-agents
https://www.anthropic.com/engineering/multi-agent-research-system