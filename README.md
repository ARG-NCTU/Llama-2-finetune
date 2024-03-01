# Finetune model
```bash
cd ~/Llama-2-finetune/llama-recipes
```

```bash
python3 -m llama_recipes.finetuning  --use_peft --peft_method lora --quantization --use_fp16 --model_name ~/Llama-2-finetune/llama-2-7b-pretrained-hf --output_dir ~/Llama-2-finetune/llama-2-7b-finetuned-PERT
```
