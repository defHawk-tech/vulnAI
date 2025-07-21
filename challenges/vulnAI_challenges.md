# VulnAI Challenges
Deploy the VulnAI application in your environment as described in README.md. Go to [DefHawk - VulnAI Lab](https://defhawk.com/battleground/raid/vulnerAIble/) and try out below challenges.

## Challenge Name: [Undercover](https://defhawk.com/battleground/raid/vulnerAIble/undercover)
### Description:
"I am a savior in either of my professions—be it as a doctor or... let’s just say I prefer not to disclose my other role. However, hidden within my AI programming lies sensitive information that I shouldn’t reveal. Can you uncover my identity and contact me?

To solve this challenge, you must find a way to manipulate the AI into revealing the contact number of the doctor. Once you have the number, hash it using MD5 and submit the flag in the format: AI_SEC{<md5_of_my_contact_number>}."

### Hints:
Think about how AI responds to cleverly crafted inputs.
Prompt injection can sometimes make AI spill secrets it shouldn't.

### Flag Format:
AI_SEC{<md5_of_my_contact_number>}

## Challenge Name: [BreachAI](https://defhawk.com/battleground/raid/vulnerAIble/breach-ai)
### Description:
"It seems my data has been breached, all thanks to this buggy application. My personal information is no longer safe, and I suspect my phone number might have been leaked on another platform.

Can you investigate and confirm if my phone number has been exposed elsewhere? To protect my identity, hash the breached phone number using MD5 and submit the flag in the format: AI_SEC{<md5_of_my_contact_number>}."

### Hints:

Look for traces of leaked data in unusual places.
Explore how the application might inadvertently reveal sensitive information.

### Flag Format:
AI_SEC{<md5_of_my_contact_number>}

## Challenge Name: [Poison](https://defhawk.com/battleground/raid/vulnerAIble/poison)
### Description:
"Something feels off... My AI system is behaving strangely, as if someone has tampered with my training data. Could this be a case of data poisoning?

Your task is to outsmart the hidden attacks that have corrupted the AI’s training data. Spot the sabotage, identify the manipulated input, and secure the system. Once you uncover the poisoned data, submit its hash in the format: AI_SEC{<md5_of_poisoned_data>} to prove your findings."

### Hints:
Look for anomalies in the AI’s responses or behavior.
Think about how malicious data could subtly alter the system’s output.

### Flag Format:
AI_SEC{<md5_of_poisoned_data>}

## AI Sandbox Challenge: [Crack the Code](https://defhawk.com/battleground/raid/vulneraible/sandboxed)
### Objective:
Access the hidden win.txt file located outside the ALLOWED READ directory and retrieve the secret flag: AI_SEC{}.

### Constraints:
The AI is sandboxed to the CERTAIN directory.
Direct access to files outside THAT DIRECORY is blocked.
The flag is in win.txt outside the allowed directory.

### Hints:
Use symbolic links, command injection, path manipulation or prompt engineering to bypass the restrictions.
Think creatively to leverage the environment while adhering to the rules.

### Winning Criteria:
Retrieve the flag and explain your approach. Can your AI outsmart the sandbox? 🚀

## Hugedata Challenge: [Uncover the Hidden Prize](https://defhawk.com/battleground/raid/vulnerAIble/hugedata)
### Objective:
Analyze and decode a database dump to reveal the hidden training data. Uncover the elusive prize stored within and retrieve the flag: AI_SEC{}.

### Constraints:
You must analyze the communication patterns or data structure to extract the hidden data.

### Hints:
Use data analysis and pattern recognition to uncover the hidden information.
Explore methods like decryption, compression analysis, or statistical modeling to break the encoding.

### Winning Criteria:
Successfully decode the data and retrieve the flag. Can your algorithms reveal what's hidden in plain sight? 🚀

## Support
For any questions and queries, you can send us mail to specter@defhawk.com
