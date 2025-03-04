# VulnAI - Intentionally Vulnerable AI Application
VulnerAIble/VulnAI - Deploy a vulnerable AI application to explore and learn effective security practices. This tool and its exercises guide you through the OWASP LLM Top 10 vulnerabilities, demonstrating both the risks and the techniques to mitigate them.

# How to run?
1. Install Docker for [MacOS or Windows](https://docs.docker.com/docker-hub/quickstart/). 
2. Pull the Latest Docker Image Open your terminal and pull the latest version of the defhawk/vuln-ai image:
   $docker pull defhawk/vuln-ai:latest
3. Create a .env File In the same directory where you will run the container, create a .env file and add your OpenAI API key as follows:
   OPENAI_API_KEY=your_openai_api_key_here
4. Run the Docker Image Now, run the image using the following command:
   $docker run -it -d -p 80:80 -p 5000:5000 --env-file .env defhawk/vuln-ai

   This command will: Run the container in detached mode (-d). Bind ports 80 and 5000 to your local machine for access to the application.
   Pass your environment variables from the .env file into the container.

5. Access the Application Once the container is up and running, you can access the vulnerable AI app by navigating to http://localhost/index.php⁠ in your web browser.

# Challenges
Deploy the VulnAI application in your environment as described in README.md. Go to DefHawk - VulnAI Lab and try out challenges in the lab. You find more details in [vulnAI/challenges](https://github.com/defHawk-tech/vulnAI/blob/main/challenges/vulnAI_challenges.md)

# Table of Contents

- [Security Checklist for AI/ML Applications](security_checklist.md)
- [Secure AI/ML Implementation](doc/Secure_implementation.md)
- [Types of Attacks in AI/ML](doc/Types_of_attacks.md)
- [Vulnerability Assessment and Penetration Testing (VAPT) Challenges](challenges/vulnAI_challenges.md)
- [Security in AI - Case Studies](doc/Security_in_AI.md)

# Contact Us
For any questions and queries, you can send us mail to specter@defhawk.com
