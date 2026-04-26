# Secure Cloud Communication using Quantum DNA Cryptography

### **Slide 1: Title Slide**
* **Title:** Secure Cloud Communication using Quantum DNA Cryptography
* **Subtitle:** Unbreakable Security for High-Stakes Environments
* **Footer:** Team Name / Names / "The Unisys Innovation Program Year 15" 

---

### **Slide 2: Problem Statement**
* **Main Points:**
    * In the face of rapid technological advancements, traditional security algorithms, such as RSA and AES, have become increasingly vulnerable to quantum algorithms.
    * Conventional security algorithms are no longer secure against advanced quantum algorithms, raising concerns about the confidentiality and integrity of sensitive data.
    * This poses a critical challenge, especially in sectors involving multiple companies, defense agencies, and high-sensitivity phases.
    * **Primary Objective:** To create secure communication without unbreakable security in highly sensitive phases.

---

### **Slide 3: The Proposed Solution**
* **Main Points:**
    * Introducing a groundbreaking approach that combines DNA-based encryption with Quantum Key Distribution (QKD), offering unparalleled security for sensitive data transmission.
    * The DNA encryption algorithm employs the unique sequences of Adenine, Thymine, Cytosine, and Guanine to encode plaintext data, incorporating mutation processes to enhance encryption strength.
    * Complementing the DNA encryption, QKD facilitates secure key generation and exchange between parties, ensuring that cryptographic keys remain impervious to interception by quantum adversaries.
    * **API Services:** We offer an API service featuring distinct endpoints (`/encrypt` and `/decrypt`) to empower users to securely encrypt and decrypt data seamlessly.

---

### **Slide 4: Algorithm Workflow**
**Encryption Phase:**
1.  Convert the plaintext message into binary format.
2.  Encode binary bits into DNA sequences using the A, C, G, T nucleotide bases.
3.  Apply a chosen quantum algorithm (e.g., Grover's or Shor's).
4.  Apply DNA mutation techniques to add complexity and enhance encryption strength.
5.  Generate a secure key using Quantum Key Distribution (QKD) for secure data transmission.

**Decryption Phase:**
1.  Receive the transmitted DNA sequence.
2.  Use the shared key established via QKD to initiate decryption.
3.  Reverse the mutation and crossover processes.
4.  Decode the DNA sequence back into the original binary format.
5.  Convert the binary values back into the original plaintext message.

---

### **Slide 5: Flowchart Overview & System Architecture**
* **Left Side (Flow Chart):** Data Sends -> Convert into Binary Values -> Convert through DNA Sequences -> DNA Encryption Starts (Reshaping/Crossover/Mutation) -> Quantum Key Distribution -> DNA Decryption Ends. 
* **Right Side (Architecture):** Sender -> Encoding into DNA Sequences -> Quantum Key Generation -> DNA Encryption -> Transmit -> Quantum Key Distribution -> DNA Decryption -> Decoding DNA Sequences -> Receiver.
*(See `flowchart_horizontal.png` included in this repository)*

---

### **Slide 6: Comparative Analysis of QKD Protocols**

| Protocol | QKD Type | Principle | Encoding Basis | Secret Key Rate | Security Rate | Efficiency Rate |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **E91** | Discrete Variable | Basis Selection | Rectilinear & Diagonal | 98.0 | 97.0 | 92.56 |
| **Gaussian Modulated** | Continuous Variable | Gaussian Distribution | Quadrature | 95.0 | 95.0 | 45.0 |
| **Reverse Reconciliation** | Continuous Variable | Error Correction | Post processing | 91.7 | 91.7 | 40.83 |
| **SARG04** | Discrete Variable | Entanglement Distillation | Rectilinear | 69.8 | 90.0 | 77.56 |
| **Square Root** | Discrete Variable | Error Correction | Rectilinear | 89.1 | 82.91 | 41.09 |
| **Time Encode** | Discrete Variable | Time Bin Encoding | Time basis | 89.3 | 78.93 | 41.7 |
| **B92** | Continuous Variable | Entanglement Swapping | Rectilinear | 98.3 | 90.0 | 81.5 |
| **BB84** | Discrete Variable | Conjugate Coding | Rectilinear | 76.0 | 90.0 | 84.44 |
| **BF92** | Discrete Variable | Bell Inequality | Rectilinear | 76.0 | 90.0 | 85.0 |

---

### **Slide 7: Comparative Study of Encryption Algorithms**

| Algorithm | Encryption Time (ms) | Decryption Time (ms) |
| :--- | :--- | :--- |
| **AES** | 2.008 | 1.27 |
| **DNA** | **0.018** | **0.008** |
| **RSA** | 1.446 | 0.947 |
| **DES** | 1.667 | 0.112 |

*(Key Takeaway: The proposed DNA algorithm drastically reduces both encryption and decryption time while maintaining an exceptionally high security rate compared to AES, RSA, and DES).*

---

### **Slide 8: Technical Stack & Benefits**
* **Qiskit:** To generate the quantum circuits for quantum communication, implementing Quantum Key Distribution Protocol.
* **Biopython:** Used to convert binary bits into DNA sequences represented by the nucleotides A, T, C, G and perform mutation techniques for encryption.
* **React.js:** Used to develop the frontend of the web page for viewing and communicating messages.
* **Google OAuth 2.0:** Provides authentication mechanism within our API service, ensuring robust security measures and seamless user authorization processes.
* **Google Cloud Platform:** To ensure the secure storage and management of API keys and messages, and protected database infrastructure.
* **Flask:** Used to develop the backend of the webpage to run the server for communication of the messages.

---

### **Slide 9: Expected Outcomes**
* **Enhanced Security:** Fortify communication channels with layers of impenetrable security, thwarting sophisticated cyber threats.
* **Quantum Cloud Integration:** Seamlessly link with quantum cloud services enabling efficient handling of a large volume of users and data transactions.
* **Unbreakable Keys:** Generate cryptographic keys inherently resistant to decryption by classical or quantum adversaries.
* **Biological Integration (DNA):** Introduce a novel layer of encryption based on DNA sequences adding an extra dimension against unauthorized access.

---

### **Slide 10: Roadmap & Future Plans**
* Scaling the API for broader enterprise integration.
* Expanding compatibility with diverse cloud infrastructure architectures.
* Commercial deployment in defense and satellite communication networks.

---

### **Slide 11: Demonstration**
* *Google Drive link or embedded video demonstrating the working React/Flask prototype securing a message via the Qiskit/Biopython pipeline.*

---

### **Slide 12: Thank You / Q&A**
* Contact information and links to the GitHub repository/documentation.
