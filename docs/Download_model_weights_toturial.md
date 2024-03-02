# Download and Prepare LLaMA Model Weight
## 1.1. Clone the LLaMA Repository and Download Model Weights
Ref: https://llama.meta.com/get-started

First, clone the LLaMA repository from GitHub and download the model weights (7b, 7b-chat, 13b, 13b-chat, 70b, 70b-chat choose one or all) using the provided script:
```bash
git clone git@github.com:facebookresearch/llama.git
cd llama
./download.sh
```

## 1.2. Prepare the Directory for the Pretrained Model
After downloading, prepare a directory where the converted Hugging Face model will be stored:
```bash
cd ~/Llama-2-finetune
mkdir llama-2-7b-pretrained-hf
```

# Convert PyTorch Model to Hugging Face Model
## 2.1 Verify transformers Version
Before proceeding, ensure that the transformers library is of version 4.31.0 or higher:
```bash
pip freeze | grep transformers
```

## 2.2 Clone the Hugging Face transformers Repository
Clone the transformers repository from Hugging Face to access the conversion script:
```bash
git clone git@github.com:huggingface/transformers.git
cd ~/Llama-2-finetune/transformers
```

## 2.3 Install Required Dependencies
Some scripts may require additional dependencies. Ensure protobuf is installed:
```bash
pip install protobuf
```

## 2.4 Convert the Model
Use the conversion script provided by Hugging Face to convert the PyTorch model weights to a format compatible with the Hugging Face transformers library:
```bash
python3 src/transformers/models/llama/convert_llama_weights_to_hf.py \
   --input_dir ~/Llama-2-finetune/llama/llama-2-7b --model_size 7B --output_dir ~/Llama-2-finetune/llama-2-7b-pretrained-hf
```