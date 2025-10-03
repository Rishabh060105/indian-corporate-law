# indian-corporate-law
Fine-tuning a Small LLM for Indian Corporate Law Q&A

This project demonstrates the process of creating a specialized Question-Answering model focused on Indian Corporate Law, specifically utilizing synthetic data generation and fine-tuning a small language model. The goal is to build a helpful assistant for law students, paralegals, or small business owners seeking quick and reliable answers on regulations and compliance under the Indian Companies Act, 2013.

Project Overview:

General-purpose Large Language Models often lack the deep, nuanced knowledge required for specialized legal domains. This project addresses this by fine-tuning a smaller, more efficient LLM on a synthetically generated dataset of Indian Corporate Law questions and answers.

Key Steps and Methodology:

Use Case Selection: The project focuses on creating a Q&A assistant for the Indian Companies Act, 2013, chosen due to the need for domain-specific accuracy in legal contexts.
Synthetic Data Generation:
A dataset of question-answer pairs was generated using a powerful external LLM (specifically, llama-3.3-70b-versatile accessed via the Groq API).
Legal text snippets from the Indian Companies Act, 2013, served as context.
A refined prompting strategy was employed to ensure the generation of diverse Q&A pairs where the answers were strictly grounded in the provided context.
Approximately 750 high-quality samples were targeted for generation.
The generated dataset is hosted on Hugging Face Datasets as ris32262/indian-corporate-law-qa-enhanced.
Model Fine-tuning:
The Qwen/Qwen1.5-1.8B-Chat model was selected as the base LLM due to its suitability for running on a Google Colab T4 GPU.
Parameter-Efficient Fine-Tuning (PEFT) was applied using the Low-Rank Adaptation (LoRA) technique.
LoRA was configured with parameters such as r=64, lora_alpha=128, targeting key attention and feed-forward modules (q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj) to efficiently adapt the model.
The fine-tuning was performed using the trl.SFTTrainer for supervised fine-tuning.
Model Evaluation:
The performance of the fine-tuned model was compared against the base model on a held-out test set.
Evaluation metrics included ROUGE (rouge1, rouge2, rougeL, rougeLsum) and BERTScore (Average F1).
Key Findings:
ROUGE Scores: The fine-tuned model showed significant improvements across all ROUGE variants (e.g., ROUGE-1 increased from approximately 0.035 to 0.494), indicating much greater overlap with reference answers.
BERTScore: The average BERTScore F1 increased from approximately 0.806 (Base) to 0.901 (Fine-Tuned), demonstrating enhanced semantic similarity to the ground truth.
These results indicate that fine-tuning with the synthetic dataset successfully adapted the model to the specific legal domain, enabling it to generate more accurate and contextually relevant answers.
Conclusion:

This project successfully demonstrated that generating synthetic data grounded in specific legal texts and using PEFT techniques can effectively fine-tune a small LLM for a specialized Q&A task. The fine-tuned model significantly outperforms the base model in generating relevant and accurate responses within the domain of Indian Corporate Law.
