# LangChain-LangGraph-Sequential-Workflow-
LangGraph Sequential Workflows (TypedDict state):BMI: compute_bmi $\to$ generate_adviceQA: process_query $\to$ generate_answer $\to$ evaluate_responseBlog: outline_generator $\to$ content_writer $\to$ editor_polisherStack: LangGraph StateGraph
Repository Overview: LangGraph Sequential Workflows
A collection of stateful, multi-step LLM workflows built using LangGraph and LangChain, focusing on clean data flow, deterministic transitions, and modular node architecture.

1. BMI Calculator Workflow
A structured computational and generative pipeline that processes physical metrics to compute Body Mass Index and deliver personalized health insights.

Core State (TypedDict):
height (float), weight (float), bmi_value (float), category (str), advice (str)

Execution Nodes:calculate_bmi: A deterministic Python function node that computes $BMI = \frac{weight}{height^2}$ and classifies the result (Underweight, Normal, Overweight, Obese).generate_advice: An LLM node that takes the computed category and generates tailored lifestyle recommendations.

Workflow Graph:START $\rightarrow$ calculate_bmi $\rightarrow$ generate_advice $\rightarrow$ END

QA Workflow
A multi-step Question Answering pipeline designed to process queries, retrieve or structure context, and generate grounded, verified responses.

Core State (TypedDict):

question (str), retrieved_context (list/str), draft_answer (str), confidence_score (float)

Execution Nodes:

query_processor: Sanitizes and expands the user prompt for optimal retrieval or reasoning.

generate_answer: Executes the LLM call using the structured prompt and context.

evaluate_response: Performs a validation check on the generated answer against criteria like completeness or grounding.

Workflow Graph:START $\rightarrow$ query_processor $\rightarrow$ generate_answer $\rightarrow$ evaluate_response $\rightarrow$ END

Blog Generator Pipeline
An automated sequential content-creation pipeline that transforms a simple seed topic into a fully polished, structured blog post through dedicated editorial stages.

Core State (TypedDict):

topic (str), outline (list), draft (str), final_post (str)

Execution Nodes:

outline_generator: Takes the seed topic and structures a detailed section-by-section outline.

content_writer: Iterates through the outline to draft the body paragraphs sequentially.

editor_polisher: Refines tone, fixes flow, formats headings, and polishes the final output.

Workflow Graph:START $\rightarrow$ outline_generator $\rightarrow$ content_writer $\rightarrow$ editor_polisher $\rightarrow$ END
