# Table of Contents: Secure AI/ML Development Reference

## 1. Building a Model and Securing It
- [Code Injection in Pickle Model - Attack Scenario](#code-injection-in-pickle-model---attack-scenario)
  - [Malicious Model File (`Model.pkl`)](#malicious-model-file-modelpkl)
    - [Description](#description)
    - [Attack Vector](#attack-vector)
    - [Potential Impact](#potential-impact)
  - [Supporting Scripts](#supporting-scripts)
    - [`Torch_steg_loader.py`](#torch_steg_loaderpy)
      - [Role](#role)
      - [Attack Vector](#attack-vector-1)
      - [Potential Impact](#potential-impact-1)
    - [`Torch_stegno.py`](#torch_stegnopy)
      - [Role](#role-1)
      - [Attack Vector](#attack-vector-2)
      - [Potential Impact](#potential-impact-2)
  - [Payload Script (`Payload.py`)](#payload-script-payloadpy)
    - [Description](#description-1)
    - [Attack Vector](#attack-vector-3)
    - [Potential Impact](#potential-impact-3)
  - [Expanded Attack Workflow](#expanded-attack-workflow)
    - [Model Distribution](#1-model-distribution)
    - [Model Loading](#2-model-loading)
    - [Payload Activation](#3-payload-activation)
    - [Persistence and Propagation](#4-persistence-and-propagation)
  - [Mitigation Strategies](#mitigation-strategies)
    - [Secure Model Handling](#secure-model-handling)
    - [Code Audits](#code-audits)
    - [Input Validation](#input-validation)
    - [Sandboxing](#sandboxing)
    - [Monitoring and Logging](#monitoring-and-logging)

## 2. Insecure Model Serialization (Pickle Vulnerabilities)
- [Issue](#issue)
- [Example](#example)
- [Best Practice](#best-practice)

## 3. TensorFlow Serialization
- [SavedModel Format](#savedmodel-format)
- [Security Implications](#security-implications)
- [Best Practices](#best-practices-1)

## 4. Preventing Model Inference Exploits
- [Issue](#issue-1)
- [Best Practices](#best-practices-2)

## 5. Preventing Adversarial Attacks
- [Issue](#issue-2)
- [Best Practices](#best-practices-3)

## 6. Hardcoded Secrets
- [Issue](#issue-3)
- [Best Practices](#best-practices-4)

## 7. Broken Authentication and Authorization
- [Issue](#issue-4)
- [Best Practices](#best-practices-5)

## 8. Lack of Input Validation
- [Issue](#issue-5)
- [Example](#example-1)
- [Best Practices](#best-practices-6)

## 9. Insecure Preprocessing Pipelines
- [Issue](#issue-6)
- [Example](#example-2)
- [Best Practices](#best-practices-7)

## 10. Exposing Sensitive Model Details (Model Inference Attacks)
- [Issue](#issue-7)
- [Example](#example-3)
- [Best Practices](#best-practices-8)

## 11. Insecure Deployment Configurations
- [Issue](#issue-8)
- [Example](#example-4)
- [Best Practices](#best-practices-9)

## 12. Lack of Explainability and Interpretability
- [Issue](#issue-9)
- [Example](#example-5)
- [Best Practices](#best-practices-10)

## 13. Overly Broad Permissions
- [Issue](#issue-10)
- [Example](#example-6)
- [Best Practices](#best-practices-11)

## 14. Failure to Monitor and Update Models
- [Issue](#issue-11)
- [Example](#example-7)
- [Best Practices](#best-practices-12)

## 15. Insecure Handling of AI/ML Logs
- [Issue](#issue-12)
- [Example](#example-8)
- [Best Practices](#best-practices-13)

# Secure AI/ML Development Reference

## Building a Model and Securing It

### Code Injection in Pickle Model - Attack Scenario

#### Malicious Model File (`Model.pkl`)
           
<img width="718" alt="image" src="https://github.com/user-attachments/assets/158f71e8-e657-4d2e-91b8-deef914964e8" />

##### Description
The model file (`Model.pkl`) contains a pre-trained or serialized machine learning model. In this scenario, it has been tampered with to include malicious code or hidden payloads.

<img width="522" alt="image" src="https://github.com/user-attachments/assets/f648ed42-7eca-428c-900e-c08667ee13e7" />

##### Attack Vector
- During deserialization or loading, the model executes arbitrary code embedded within it.
- Attackers may use frameworks like `pickle` or similar serialization tools to embed malicious code.

##### Potential Impact
- Execution of unauthorized code.
- Compromise of the system running the model.

---

#### Supporting Scripts

##### `Torch_steg_loader.py`

####### Role
A loader script that handles the deserialization and initialization of the malicious model.

###### Attack Vector
- This script could be designed to obfuscate the malicious payload embedded in the model.
- It might use steganographic techniques to extract hidden code from the model.

###### Potential Impact
- Acts as a bridge to activate the payload during the loading process.
- Can execute additional commands or download further malicious components.

---

##### `Torch_stegno.py`

<img width="495" alt="image" src="https://github.com/user-attachments/assets/edd10df6-145f-4d71-9a3b-9e43de4a0ac0" /> <img width="495" alt="image" src="https://github.com/user-attachments/assets/0a9b3e9a-8ab9-4b1f-8e76-c436f7f01e59" />
<img width="472" alt="image" src="https://github.com/user-attachments/assets/dfdb337a-aeed-41f3-b726-cc8fa0c07550" />



###### Role
A helper script that might handle the steganographic operations, such as hiding or extracting malicious code from the model file.

###### Attack Vector
- Uses advanced techniques to conceal malicious payloads within the model, making detection harder.
- Could be used to dynamically modify or inject code into the model at runtime.

###### Potential Impact
- Increases the stealth of the attack.
- Makes traditional scanning or auditing tools less effective.

---

#### Payload Script (`Payload.py`)

##### Description
The actual malicious payload that performs the attacker's intended operations.

##### Attack Vector
The payload could include operations like:
- Data exfiltration (e.g., stealing sensitive data or model predictions).
- System compromise (e.g., installing backdoors or malware).
- Denial of Service (DoS) attacks targeting the AI/ML system.
- Triggered by the malicious loader or model file.

##### Potential Impact
- Complete compromise of the system running the model.
- Exposure of sensitive data or intellectual property.
- Potential lateral movement within the organization’s infrastructure.

---

#### Expanded Attack Workflow

##### 1. Model Distribution
The attacker distributes the malicious model file (`Model.pkl`) through legitimate channels, such as open-source repositories, collaboration platforms, or via phishing attacks targeting AI/ML developers.

##### 2. Model Loading
A victim downloads and loads the malicious model using `Torch_steg_loader.py`. During this process, the loader extracts and executes the hidden payload embedded in the model.

##### 3. Payload Activation
The payload script (`Payload.py`) is executed, performing the attacker's objectives, such as stealing data or compromising the system.

##### 4. Persistence and Propagation
The attacker ensures persistence by embedding additional backdoors or propagating the malicious model to other systems.

---

#### Mitigation Strategies

##### Secure Model Handling
- Avoid loading models from untrusted or unauthenticated sources.
- Use secure serialization formats (e.g., avoid `pickle` for untrusted data).

##### Code Audits
- Regularly review and audit scripts like loaders for potential malicious behavior.
- Use static and dynamic analysis tools to detect anomalies.

##### Input Validation
- Validate all inputs and files being processed by the pipeline.
- Use hashing or cryptographic signatures to verify model integrity.

##### Sandboxing
- Load and execute models in isolated environments to prevent system-wide compromise.

##### Monitoring and Logging
- Monitor runtime behavior of models and scripts for unusual activities.
- Log all actions related to model loading and execution for forensic analysis.
  
---

## Insecure Model Serialization (Pickle Vulnerabilities)

### Issue
Many AI/ML frameworks, such as PyTorch and TensorFlow, use serialization methods (e.g., Python pickle, `torch.save()`) to save and load models. If attackers tamper with serialized models or the deserialization process, they can inject malicious code.

### Example
Loading a model file that contains a malicious payload could execute arbitrary code (Remote Code Execution, RCE).

### Best Practice
- Use secure formats like ONNX or TensorFlow’s SavedModel format instead of pickle or similar serialization techniques for models.

---

## Building a Model and Securing It

### Pickle Variants
- **Pickle** and its variants (e.g., `cloudpickle`, `dill`, `joblib`) are widely used for serializing Python objects.
- Commonly used in:
  - **Classic ML models** (e.g., scikit-learn, XGBoost)
  - **PyTorch models** (via the built-in `torch.save` API)

- **Pickle for storing vectors/tensors:**
  - Numpy: `numpy.save(.., allow_pickle=True)`
  - PyTorch: `torch.save(model.state_dict(), ..)`

### Security Implications
- **Risks:** Pickle files can execute arbitrary Python code during deserialization, making them vulnerable to code injection attacks.
- **Recommendation:** Avoid using pickle for production models and prefer safer serialization formats.

---

## TensorFlow Serialization

### SavedModel Format
- TensorFlow’s SavedModel format is based on the Protocol Buffer format.
- This approach is generally secure as most TensorFlow operations are limited to ML computations and transformations.

### Security Implications
While TensorFlow’s SavedModel format is secure, there are exceptions:

1. **Operations Vulnerable to Exploitation:**
   - `io.write_file`
   - `io.read_file`
   - `io.MatchingFiles`

2. **Custom Operators:**
   - Allow arbitrary code execution.
   - Require explicit loading during inference as a library.
   - High-risk in supply chain attacks.

### Best Practices
- Treat TensorFlow models with custom operators with high scrutiny.
- Perform thorough validation and restrict access to serialized models.

### Malicious Lambda Layer in Keras
![Malicious Lambda Layer Example](https://github.com/user-attachments/assets/feef38b9-12a3-4516-a9ec-f522a2463c77)

![Malicious Lambda Layer Code](https://github.com/user-attachments/assets/edd395fe-9b5-4723-b0fb-87c395069cab)

---

## Preventing Model Inference Exploits

### Issue:
Attackers can exploit vulnerabilities in model inference APIs to extract sensitive data or reverse-engineer the model.

### Best Practices:
- Use API authentication and rate limiting.
- Implement model obfuscation techniques.
- Apply differential privacy to protect training data.

---

## Preventing Adversarial Attacks

### Issue:
Adversarial examples can trick AI models into making incorrect predictions.

### Best Practices:
- Use adversarial training to harden the model against such attacks.
- Apply robust input validation and sanitization techniques.
- Monitor for unusual patterns in input data.

---

## Hardcoded Secrets
![Hardcoded Secrets Example](https://github.com/user-attachments/assets/1e817705-4ee3-4a53-90d5-dc1c07a45922)

### Issue:
Embedding secrets (e.g., API keys, passwords) in code exposes them to unauthorized access.

### Best Practices:
- Use environment variables or secure vaults for managing secrets.
- Regularly rotate and audit credentials.

---

## Broken Authentication and Authorization
![Broken Auth Example](https://github.com/user-attachments/assets/fea7c271-41b7-445d-8533-7f9779b4d070)

### Issue:
Weak or missing authentication and authorization can lead to unauthorized access.

### Best Practices:
- Enforce strong authentication mechanisms (e.g., OAuth2, JWT).
- Apply role-based access control (RBAC).

---

## Lack of Input Validation

### Issue:
AI/ML models often accept user inputs, and improper validation can lead to adversarial examples or malicious data injection.

### Example:
Image classification models can misclassify adversarial images designed to fool the model.

![Adversarial Input Example](https://github.com/user-attachments/assets/b118b41e-00bd-44a0-98b8-376cb30bc8db)

### Best Practices:
- Validate and sanitize inputs.
- Use adversarial training to improve robustness.

---

## Insecure Preprocessing Pipelines

### Issue:
Data preprocessing steps can expose vulnerabilities like insecure file handling or data leakage.

### Example:
Allowing arbitrary file uploads without proper checks can compromise the system.

### Best Practices:
- Implement input checks and secure file handling.
- Use proper error handling mechanisms.

---

## Exposing Sensitive Model Details (Model Inference Attacks)

### Issue:
Overexposing model prediction details can lead to reverse-engineering or sensitive data inference.

### Example:
APIs can be exploited to reconstruct training data via model inversion or membership inference attacks.

### Best Practices:
- Use model obfuscation and rate limiting.
- Implement differential privacy techniques.

---

## Insecure Deployment Configurations

### Issue:
Insecure configurations in cloud or edge environments expose models to threats.

### Example:
Hosting a model on an open server without authentication.

### Best Practices:
- Securely configure environments with firewalls and encryption.
- Use cloud security best practices and container security.

---

## Lack of Explainability and Interpretability

### Issue:
Black-box models are hard to interpret, making it easier for attackers to exploit biases or introduce adversarial data.

### Example:
A biased model may show discriminatory results due to unexplainable features.

### Best Practices:
- Use explainable AI techniques.
- Ensure model decisions are based on legitimate features.

---

## Overly Broad Permissions

### Issue:
Granting models unnecessary permissions increases security risks.

### Example:
A model with access to a production database could expose sensitive data if compromised.

### Best Practices:
- Apply the principle of least privilege (PoLP).
- Audit and restrict permissions regularly.

---

## Failure to Monitor and Update Models

### Issue:
Unmonitored models become outdated and vulnerable to new attack techniques.

### Example:
Models may become biased or outdated, leading to model evasion or poisoning attacks.

### Best Practices:
- Continuously monitor model performance.
- Retrain models regularly and apply security patches.

---

## Insecure Handling of AI/ML Logs

### Issue:
Logs containing sensitive information can be exploited if improperly stored.

### Example:
Logs with sensitive data could allow attackers to infer confidential information or reverse-engineer models.

### Best Practices:
- Securely store logs and obfuscate sensitive information.
- Restrict log access to authorized personnel only.
