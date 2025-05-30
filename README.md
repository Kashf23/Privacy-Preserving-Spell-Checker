# Privacy Preserving Spell Checker via AES-ECB 128 & LSTM

## Project Overview

A novel spell checker designed to operate directly on **AES-128 ECB encrypted data**, eliminating the need for decryption during the core processing phase. This project demonstrates a proof-of-concept for secure, privacy-preserving text correction using a custom LSTM-based neural network.

## The Problem: Data Privacy in Cloud-Based Services

In an increasingly data-driven world, traditional spell checkers often require user input to be sent to a server in plaintext for processing. This raises significant privacy concerns, especially for sensitive or personal information. This project addresses the challenge of performing essential text operations (like spell checking) while maintaining the confidentiality of the input data throughout the process.

## Our Approach: Encrypted Machine Learning

We propose and implement a unique solution that merges applied cryptography with deep learning to achieve privacy-preserving spell correction:

1.  **Direct Processing on Encrypted Data:** The system ingests words that are already encrypted using AES-128 ECB.
2.  **LSTM-based Neural Network:** A custom Long Short-Term Memory (LSTM) neural network is trained on pairs of encrypted misspelled and encrypted correct words. The network learns to predict the encrypted correction based on the encrypted input, without ever seeing the original plaintext.
3.  **End-to-End Confidentiality:** The entire spell-checking workflow, from input to correction prediction, occurs in the encrypted domain. Decryption is only performed at the very end, optionally, by the user if they wish to view the plaintext correction.

## Key Features & Functionality

* **AES-128 ECB Encryption/Decryption:** Robust functions for encrypting and decrypting individual words using a symmetric key.
* **Encrypted Dataset Preparation:** Processes a plaintext dataset into an encrypted format suitable for neural network training.
* **Custom LSTM Model:** Implements and trains a sequential LSTM model using TensorFlow/Keras tailored to map encrypted typos to encrypted correct words.
* **Base64 Character Vocabulary:** Developed a specialized vocabulary and tokenization method for handling Base64 encoded encrypted strings, enabling them to be processed by the neural network.
* **Proof-of-Concept System:** Demonstrates the core logic via a command-line interface (CLI) for user interaction, showcasing the feasibility of the approach.
* **Direct Correction Lookup:** Includes a mechanism to directly find encrypted correct words for exact encrypted typo matches in the dataset before resorting to neural prediction.

## Research Contributions & Innovations

* **Novel Integration:** This project presents a novel integration of symmetric encryption (AES-ECB) directly into a deep learning pipeline for a practical application (spell checking).
* **Processing in Encrypted Domain:** It demonstrates the ability to perform complex sequence-to-sequence mapping (correction) directly on encrypted data, a step towards more secure AI/ML services.
* **Feasibility Demonstration:** Provides a functional proof-of-concept, validating the hypothesis that deep learning models can learn patterns from encrypted representations without plaintext exposure during inference.

## Technical Stack

* **Programming Language:** Python
* **Environment:** Jupyter Notebook (for `.ipynb` execution)
* **Deep Learning Framework:** TensorFlow, Keras
* **Cryptography Library:** PyCryptodome (for AES-128 ECB)
* **Data Manipulation:** NumPy, Pandas
* **Other Libraries:** `base64`, `pickle`

## How to Run the Project

To set up and run this project locally (or in a compatible environment like Google Colab):

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/privacy-preserving-spell-checker-aes-lstm.git](https://github.com/yourusername/privacy-preserving-spell-checker-aes-lstm.git)
    cd privacy-preserving-spell-checker-aes-lstm
    ```
2.  **Place your dataset:** Ensure your `Final_Dataset.csv` (containing 'typo' and 'correct_word' columns) is in the root directory of the project. (If you moved it from `/content/drive/MyDrive/` as discussed, it should now be directly in your repo.)
3.  **Install dependencies:**
    ```bash
    pip install pandas numpy tensorflow keras pycryptodome jupyter # Add 'jupyter' here
    ```
4.  **Launch Jupyter Notebook/Lab:**
    ```bash
    jupyter notebook  # Or 'jupyter lab'
    ```
5.  **Open the Notebook:** In the Jupyter interface that opens in your browser, navigate to your repository folder and click on `Main Code.ipynb`.
6.  **Run Cells:** Execute all cells in the notebook sequentially. The notebook will handle dataset encryption, model training, and then launch the interactive command-line interface within the notebook output cells for spell checking.
    The script will first perform dataset encryption, model training, and then launch the interactive command-line interface for spell checking.

## Project Structure
``````.
├── main_code.py             # Main script containing data processing, model training, and CLI
├── Final_Dataset.csv        # Input dataset for spell checking 
├── encrypted_dataset.csv    # Generated encrypted encrypted dataset (ignored by .gitignore after first run)
├── vocabulary.pkl           # Saved vocabulary mapping Base64 chars to indices
├── max_len.txt              # File storing the maximum sequence length
├── nlp_model/               # Directory containing the saved TensorFlow/Keras model
└── README.md                # This file
└── .gitignore               # Specifies files/folders to ignore in Git
└── LICENSE                  # Project license details
``````

## Future Work & Expansion Plans

This proof-of-concept lays the groundwork for exciting future developments:

1.  **Document-Level Processing:** Extend the spell checker's capabilities from single word correction to processing entire documents, addressing challenges related to contextual understanding and maintaining encryption across larger text blocks.
2.  **Enhanced Security with AES-CBC:** Transition from AES-ECB 128 to a more robust encryption mode like AES-CBC. This would involve adapting the data handling to incorporate Initialization Vectors (IVs) while still ensuring compatibility with the neural network's input requirements, significantly strengthening the privacy guarantees.
3.  **Advanced Model Architectures:** Explore the use of more sophisticated deep learning architectures (e.g., Bidirectional LSTMs, Transformers) to improve prediction accuracy and efficiency on encrypted data.
4.  **Performance Optimization:** Investigate methods to optimize the training and inference speed for larger datasets and real-time applications.
5.  **Cloud Integration:** Explore deploying the encrypted spell checker backend and web interface on cloud platforms (e.g., Google Cloud Platform, AWS, Azure) to enable scalable and accessible privacy-preserving services.
6. **Enhance Web Interface Robustness:** Focus on refining the existing Flask-based web interface to improve its performance, scalability, and user experience, addressing known limitations and enhancing its production readiness.

## Acknowledgements

* **Supervisor:** Special thanks to Ms. Sehrish Ferdous for providing the initial project idea and offering invaluable guidance and support throughout the development of this research project.
* **Team Member:** This project was developed as a Final Year Project alongside Mr. Haris Iftikahr, who contributed significantly to the comprehensive LaTeX documentation, the conceptual design of the system, data preprocessing efforts.
* **Frontend Assistance:** I am grateful to Mr. Umer Bin Amir for their valuable assistance and insights during the development of the web application's frontend using Flask and Tailwind CSS.

## License

This project is licensed under the [MIT License](LICENSE) 

## Contact

Kashaf Naz
kashaf.naz2302@gmail.com
