##### exec sequence
> Is there any  execution.order between policy and attention mecanism?

Strictly speaking, the attention mechanism executes first, but the persona and policy shape the query vectors that drive it.
Here is the exact order of operations inside a transformer:
 * Context Initialization (Persona + Policy Injection):
   When you write "You are a tired parent with a short-term resolution policy..." at the start of your prompt, those instructions enter the model's context window first. They establish the active embedding space and bias the model's internal weights.
 * Attention Mechanism Execution (Q, K, V):
   As the model reads the input text (the situation), its attention heads compute dot products between queries (Q) and keys (K). Because the persona/policy instructions were injected first, they alter the query vectors (Q). This forces the attention mechanism to dynamically weight certain keywords (like "exhausted" vs. "4-year-old") over others.
 * Generation:
   The final output is generated based on those weighted tokens, filtered through the behavioral constraints of the policy.
In short: The policy and persona act as the lens that configures the attention mechanism before it scans the text.

##### reaction
> Ok. It is like picking running  shoes before going to work. It does not implies you will be asked to run. But it may help

That is actually a brilliant analogy.
Putting on running shoes (setting the persona and policy) alters your posture, primes your muscles, and changes how you step out the door—making you hyper-aware of shortcuts, stairs, or running paths.
Even if you end up sitting at a desk all day, that initial setup fundamentally changes your readiness and how you navigate the environment if a sprint does happen.
