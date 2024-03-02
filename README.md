# Setup and Preparation
## 1.1 Clone the repository
Clone the repository, including its submodules:
```bash
git clone --recurse-submodules git@github.com:ARG-NCTU/Llama-2-finetune.git
```

## 1.2 Update the submodule (if needed)
If necessary, update the submodule to ensure it's initialized and up to date:
```bash
git submodule update --init --recursive
```


# Preparing the Model
## 2.1 Download the pretrained model weights
Download the pretrained model weights from the provided NAS link.

Link: http://gofile.me/773h8/uYom43iVm

## 2.2 Extract the model weights
Navigate to the Downloads directory, extract the downloaded zip file, and move it to the designated directory:
```bash
mv Download/path/to/llama-2-7b-pretrained-hf.zip Llama-2-finetune/llama-2-7b-pretrained-hf.zip 
cd ~/Llama-2-finetune
unzip llama-2-7b-pretrained-hf.zip
```

The tree directory will be like:
![Tree Dir](img/tree_dir.png)


# Docker Container Setup
## 3.1 Pull and run the docker image
From the root directory of the cloned repository, pull and run the Docker image:
```bash
cd ~/Llama-2-finetune
source docker_run.sh
```

## 3.2 Log in to Weights & Biases
Log in to your Weights & Biases (wandb) account by running:
```bash
wandb login
```
Follow the prompts to enter your API key.

# Model Fine-tuning
## 4.1 Navigate to the llama-recipes directory
Ensure you're in the llama-recipes directory within the repository:
```bash
cd ~/Llama-2-finetune/llama-recipes
```

## 4.2 Fine-tune the model
Execute the Python script for fine-tuning, including various flags for configuration (default in llama-recipes/src/llama_recipes/configs/training.py):
```bash
python3 -m llama_recipes.finetuning  --batch_size_training 1 --use_peft --peft_method lora --quantization --use_fp16 --model_name ~/Llama-2-finetune/llama-2-7b-pretrained-hf --output_dir ~/Llama-2-finetune/llama-2-7b-finetuned-PERT --use_wandb
```


# Monitoring Training Progress
## 5.1 Access training metrics
After starting the training, a URL will be provided in the terminal. Ctrl + click to view the training curve and other metrics on Weights & Biases.
![Terminal View](img/enter_wandb.png)

![Training Curve](img/training_curve.png)

