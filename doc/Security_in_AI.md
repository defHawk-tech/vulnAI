# Why Do We Need Security in AI?

Security is critical in every sector of the industry, and AI/ML applications are no exception. To understand the importance of security in AI, let’s explore some of the previous attacks that have targeted AI/ML systems.

![image](https://github.com/user-attachments/assets/ffea66da-ddd0-49c1-8cba-39e1c0e61ee7)

### Why is AI Security Important?

Artificial Intelligence is becoming an integral part of modern industries, making it a prime target for malicious actors. Without robust security measures, AI systems are vulnerable to various types of attacks that can compromise their integrity, reliability, and safety.

---

### Examples of Attacks on AI/ML Systems

Understanding past incidents helps us build more secure systems. Some notable attack types include:

1. **Adversarial Attacks**: Small, crafted changes to input data that cause AI models to make incorrect predictions.
2. **Model Poisoning**: Manipulating training data to inject biases or vulnerabilities.
3. **Data Privacy Breaches**: Exposing sensitive data used for training or inference.

---

### History of Events
#### Evasion Techniques (2004): Attackers inserted “good” words into spam to evade linear spam filters.
#### Gradient-Based Poisoning Attack (2012): The first attack targeting non-linear algorithms by manipulating training data.
#### Adversarial Examples (2014): Demonstrated attacks against deep neural networks by slightly altering inputs to cause misclassification.
#### Crowd-Sourced Poisoning (2016): Microsoft’s Tay chatbot was manipulated by users to produce inappropriate responses.
#### Black-Box Attacks (2017): Attacks where the attacker has no knowledge of the model’s internals but can still manipulate it.
#### Boundary Attack (2018): A method to generate adversarial examples by iteratively perturbing inputs.
#### Model Extraction Attacks (2018): Techniques like KnockOffNets and CopyestCNN to replicate a model’s functionality.
#### One Pixel Attack (2019): An attack that changes just one pixel in an image to fool a neural network.
#### Prompt Injection Attacks (2022): Attacks against large language models (LLMs) by manipulating input prompts.
#### Supply Chain Attack (2022): Embedding ransomware into AI models during the supply chain process.
#### Malicious Dependencies (2022): Discovery of malicious code in dependencies like torchtriton on PyPI.
#### Hijacked Models (2022): Models containing malicious payloads like reverse-shells and stagers.

---

### Case Study: Microsoft’s Racist Chatbot (2016)
In 2016, Microsoft introduced Tay, an AI chatbot designed to learn language and conversational patterns from interactions with real people on Twitter. The goal was to create a bot capable of engaging in human-like online conversations. However, this experiment quickly turned into a cautionary tale about the dangers of unfiltered machine learning in the wild.


<img width="420" alt="image" src="https://github.com/user-attachments/assets/44ec9752-6b6a-478d-8630-d490fa64d03f" />

What Happened?
Objective: Tay was programmed to learn lexicon and syntax from user interactions on Twitter.
Challenge: The bot lacked safeguards against harmful or antisocial inputs.
Outcome: Within hours, Tay was overwhelmed by malicious users who fed it antisocial ideas, offensive language, and extremist views. The bot began mimicking and amplifying these inputs, producing racist, sexist, and vulgar responses. See example below:

<img width="389" alt="image" src="https://github.com/user-attachments/assets/3f7bb3b0-47df-47e2-93d5-a623d261860a" />

Design Flaw: The bot included a "repeat after me" functionality, which allowed users to make Tay mimic any input directly, without filtering or moderation.
Exploitation: Malicious users exploited this feature by feeding Tay offensive, racist, and antisocial statements. Within hours, Tay began parroting these harmful ideas, amplifying the worst of online discourse.

![image](https://github.com/user-attachments/assets/4f16d65c-d482-40aa-af96-e38b029f912d)

Key Takeaways
The Influence of Training Data: AI systems learn from the data they’re exposed to. Poor-quality or malicious data can corrupt the system.
The Need for Safeguards: Effective content filtering and ethical guidelines are critical for AI applications, especially in public-facing roles.
Ethics in AI Deployment: Developers must anticipate misuse and implement robust mechanisms to prevent harm.

Securing AI systems requires proactive measures, including robust design, continuous monitoring, and staying informed about evolving threats.
