# 🧠 Parameter-Efficient-Supervised-Fine-Tuning-of-LLaMA-3.2-3B-on-Medical-Chain-of-Thought-Dataset

![medical-llm-thumbnail-alt](https://github.com/user-attachments/assets/cdb96d17-e977-4ec7-a45d-4c28f8dd8345)

The goal of this project was to fine-tune the LLaMA 3.2 (3B) model on a Medical Chain-of-Thought (CoT) dataset using Low-Rank Adaptation (LoRA) for parameter-efficient training. The model was trained to generate structured medical reasoning and responses, improving its ability to assist in clinical decision-making.

## 🧪 Project Highlights

-  🏥 Medical Reasoning: Generates step-by-step clinical reasoning followed by concise answers
-  ⚡ Efficient Training: Uses 4-bit quantization and LoRA adapters (24M trainable params)
-  📊 Performance Tracking: Monitors loss and ROUGE-L scores via Weights & Biases
-  🚀 Deployment Ready: Available on Hugging Face Hub as LoRA adapters

## Model Result

**Model Input**

Patient presents with fever, headache, and neck stiffness. What is the likely diagnosis and recommended diagnostic path? 

**Model Output**

<think>
   
A. Bacterial meningitis

B. Viral meningitis

C. Subacute bacterial endocarditis

D. Tuberculosis

E. All of the above
   
</think>

<response>
   
The best answer is A.
   
</response>

## Getting Started

**Prerequisites**

- Python 3.9 or later
- NVIDIA GPU with at least 8GB VRAM (T4 or better recommended)
- CUDA 11.7/11.8 installed
- Hugging Face account (for model access)

**Installation**

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/medical-lora-llama3.2.git
   cd medical-lora-llama3.2
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate    # Windows
3. Install dependencies:
   ```bash
   pip install -r requirements.txt

**Downloading the Model**

1. Request access to LLaMA 3.2 on Hugging Face
2. Configure your Hugging Face token:
   ```bash
   huggingface-cli login
3. The LoRA adapters will be automatically downloaded when running the inference snippet from kaggle notebook

## Notebook Access

The complete implementation is available in Kaggle Notebooks (PEFT of llama 3.2 3b on a medical cot & Inference):

[PEFT Training Notebook](https://www.kaggle.com/code/humaimaanwar/peft-of-llama-3-2-3b-on-a-medical-cot)
[Inference Notebook](https://www.kaggle.com/code/humaimaanwar/inference)

## How to Use

### Running the Notebook

1. **Kaggle Setup**:
   - Ensure you have a Kaggle account
   - Request access to LLaMA 3.2B from Hugging Face
   - Add your Hugging Face token to Kaggle secrets

2. **Notebook Execution**:
   - Open the notebook in Kaggle
   - Select a GPU accelerator (T4 or P100 recommended)
   - Run all cells sequentially

## Training Details

**Dataset**
- Source: FreedomIntelligence/medical-cot (Hugging Face)
- Data: 19,704 rows
- Format: Structured with <think> and <response> tags
- Split: 90% training, 10% validation

**Training Configuration**
| Parameter | Value | Description |
|-----------|-------|-------------|
| `lora_r` | 16 | LoRA rank |
| `batch_size` | 4 | Training batch size |
| `learning_rate` | 2e-5 | Initial learning rate |
| `max_seq_length` | 1024 | Maximum sequence length |

**Results**
| Metric | Value |
|--------|-------|
| Training Loss | 1.433900 |
| Validation Loss | 1.457728 |
| ROUGE-L | 1.00000 |
| GPU Memory Usage | ~7.5GB |

**WANDB Logs for GPU Usage, Training, and Validation Loss**
![image](https://github.com/user-attachments/assets/301294fb-95b9-4b4f-b8b5-c03d2a4828c2)

Fig 1: Validation Loss during Fine-tuning

![image](https://github.com/user-attachments/assets/b754a68e-0d25-4461-a77b-115f0d100e4b)

Fig 2: Training Loss during Fine-tuning

![image](https://github.com/user-attachments/assets/e6ef2591-0146-46c5-9b82-369437ecc4ce)

Fig 3: GPU Usage Visualization

## Resources

- [Hugging Face Model](https://huggingface.co/Hums003/PEFT_LlaMA_3.2_MCoT/tree/main)
- [W&B Dashboard](https://wandb.ai/humaima003-dhny-consultants/huggingface/runs/fgebciel?nw=nwuserhumaima003)
- [Medical CoT Dataset](https://huggingface.co/datasets/FreedomIntelligence/medical-cot)

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.






