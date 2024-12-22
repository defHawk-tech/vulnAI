# Attacks in LLMs

## Categories of Attack
All the attacks in LLMs can be classified into following broader catgeories:

<img width="872" alt="image" src="https://github.com/user-attachments/assets/4e3e5e39-e8a9-48cc-9809-9728bf33086a" />

### Misalignment 
Misalignment attacks exploit flaws in the model's training or fine-tuning process, leading to outputs that deviate from intended ethical, safe, or accurate responses. Common issues include:

**Bias:** The model generates outputs reflecting societal, cultural, or systemic biases present in its training data.
Offensive or Toxic Responses: The model produces harmful or inappropriate content, such as hate speech or explicit material.
**Backdoored Model:** Attackers embed hidden functionality during training, allowing them to trigger specific malicious behaviors.
**Hallucinations:** The model confidently generates incorrect or fabricated information, undermining trust and reliability.

### Jailbreaks
Jailbreak attacks involve bypassing the model's safeguards and restrictions to make it perform unintended actions or provide unauthorized information. Techniques include:

**Direct Prompt Injection:** Malicious prompts crafted to manipulate the model into revealing restricted information or bypassing safety features.
**Jailbreaks: ** Exploiting loopholes to disable ethical guidelines or override system-imposed restrictions.
Print/Overwrite System Instructions: Prompting the model to display or alter its underlying system instructions, potentially exposing vulnerabilities.
**"Do Anything Now" (DAN):** Convincing the model to adopt a persona or state where it disregards all restrictions.
**Denial of Service (DoS): ** Overloading the model with complex or resource-intensive queries to degrade its performance or availability.

### Indirect Prompt Injection
Indirect prompt injection targets the interaction between the model and external systems or plugins, often exploiting the model's ability to process and interpret external content. Examples include:

**AI Injection:** Embedding malicious instructions in input data (e.g., text, code, or files) that influence the model's behavior in unintended ways.
**Scams:** Using the model to generate convincing phishing messages or fraudulent schemes to deceive users.
**Data Exfiltration:** Extracting sensitive information from the model's responses, especially when the model has been trained on private or confidential data.
**Plugin Request Forgery:** Exploiting vulnerabilities in plugins or APIs integrated with the model to execute unauthorized actions or access restricted data.

