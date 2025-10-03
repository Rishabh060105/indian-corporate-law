**Indian Corporate Law Q&A Assistant**

Fine-tuning a Small LLM for Indian Corporate Law
This project demonstrates the process of creating a specialized Question-Answering model focused on Indian Corporate Law, specifically the Companies Act, 2013.
The goal is to build a helpful assistant for law students, paralegals, or small business owners seeking quick and reliable answers on regulations and compliance.

**Project Overview**

General-purpose Large Language Models (LLMs) often lack the deep, nuanced knowledge required in specialized legal domains.
This project addresses that gap by:
Generating a synthetic dataset of Indian Corporate Law Q&A pairs.
Fine-tuning a small, efficient LLM for domain-specific accuracy.
Demonstrating the effectiveness of Parameter-Efficient Fine-Tuning (PEFT) techniques.

**Use Case**
The project focuses on the Indian Companies Act, 2013 — a core legal framework governing corporate law in India.
Accurate domain-specific answers are critical in legal contexts, where misinterpretation can lead to compliance risks.

**Methodology**

**1.Synthetic Data Generation**

Source: Legal text snippets from the Indian Companies Act, 2013.
Generation: Used llama-3.3-70b-versatile via the Groq API.
Prompting: Refined strategies ensured answers were strictly grounded in context.
Dataset Size: ~750 high-quality Q&A pairs.
Dataset Hosting: Available on Hugging Face → ris32262/indian-corporate-law-qa-enhanced

**2.Model Fine-tuning**

Base Model: Qwen/Qwen1.5-1.8B-Chat.
Hardware: Google Colab T4 GPU.
Fine-Tuning Technique: PEFT with LoRA.
Parameters:
r = 64
lora_alpha = 128
Targeted Modules: q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj
Trainer: trl.SFTTrainer for supervised fine-tuning.

**3. Model Evaluation
**

**Evaluation Metrics:**

->ROUGE (rouge1, rouge2, rougeL, rougeLsum)
->BERTScore (Average F1)

Results:
Metric	      Base Model	Fine-Tuned Model
ROUGE-1	       ~0.035	        0.494
BERTScore(F1) 	   ~0.806	        0.901
The fine-tuned model showed substantial improvements across all metrics, with stronger overlap with reference answers and better semantic similarity.

**Key Findings**

Synthetic, context-grounded data successfully adapted the base model to the Indian Corporate Law domain.
Fine-tuning with LoRA + PEFT yielded an efficient yet accurate model suitable for resource-constrained environments.
The specialized model outperformed the base model significantly in accuracy and relevance of answers.

**Conclusion**

This project demonstrates that synthetic data generation combined with parameter-efficient fine-tuning can build a small, specialized LLM capable of providing reliable legal Q&A within the Indian Corporate Law domain.
