README.md Content
markdown
Copy code
# Hybrid BERT Compression with HDC and Random Projections

This project demonstrates how to compress large layers of a BERT model using:
1. **Hyperdimensional Computing (HDC)-inspired** binarization and XOR binding.
2. **Sparse Random Projection** for dimensionality reduction.

The goal is to reduce the memory footprint of BERT while maintaining reasonable accuracy for downstream tasks such as sentiment analysis.

---

## Features

- Compress large weight matrices (e.g., `intermediate.dense.weight`) using HDC and random projection.
- Replace the original layers with custom PyTorch layers that decode compressed weights at runtime.
- Evaluate the compressed hybrid model's performance compared to the original model.

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/JesseBrown1980/my-hybrid-bert-project.git
cd my-hybrid-bert-project
2. Install Dependencies
Make sure you have Python 3.7+ installed. Install the required Python packages:

bash
Copy code
pip install torch transformers datasets scikit-learn
If you are using a GPU, ensure you have CUDA installed and use the CUDA-compatible version of PyTorch:

bash
Copy code
pip install torch --extra-index-url https://download.pytorch.org/whl/cu118
3. Run the Scripts
Compress the Model
Run hybrid_bert.py to compress the model's large weight matrices and save the compressed version:

bash
Copy code
python hybrid_bert.py
Perform Inference
Use inference.py to load the compressed model and perform inference on example sentences:

bash
Copy code
python inference.py
Project Structure
bash
Copy code
.
├── hybrid_bert.py           # Script for compressing the BERT model
├── inference.py             # Script for loading and running inference with the compressed model
├── LICENSE                  # License file (MIT)
├── README.md                # Project documentation
├── .gitignore               # Ignore unnecessary files like __pycache__
Key Concepts
CompressedLinear Layer
This project introduces a custom PyTorch layer, CompressedLinear, which:

Stores weights in a compressed form.
Expands weights back to their original shape during inference using a projection layer.
Compression Steps
Binarize weights: Convert matrix values to binary using sign thresholds.
Bind with random vectors: Use XOR to bind the flattened weights with a random binary vector.
Reduce dimensionality: Apply sparse random projection to reduce size further.
Example Usage
Compress the Model
When running hybrid_bert.py, you'll see outputs showing:

The original vs. compressed model performance on the GLUE SST-2 dataset.
Compressed weights saved to compressed_bert_model.pth.
Perform Inference
When running inference.py, the script will load the compressed model and classify input sentences. Example output:

yaml
Copy code
Input: This movie was fantastic!
Predicted label: Positive
Probabilities: [0.02, 0.98]
Contributions
Jesse Daniel Brown, Ph.D. AASU (Project Lead)
Zac Zacharia (Main Builder)
License
This project is licensed under the MIT License. See the LICENSE file for details.

