# Proyecto Integrador

Este proyecto se enfoca en comparar la capacidad de 3 diferentes LLM a la hora de seguir instrucciones en Español y después responder dudas acerca de un tema muy específico en Español. En este repositorio se incluyen todos los recursos necesarios para poder replicar los resultados y experimentos usando la interfaz [text-generation-webui](https://github.com/oobabooga/text-generation-webui).

### Modelos comparados ###

- [Mistral 7B](https://huggingface.co/mistralai/Mistral-7B-v0.1)
- [LLaMA2 Chat 7B](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)
- [FALCON 7B](https://huggingface.co/ybelkada/falcon-7b-sharded-bf16)

### Entrenamiento para instrucciones en español 

Todos los modelos han sido entrenados usando la técnica de QLORA con las librerías provista por [Hugging Face](https://huggingface.co/docs/transformers/index). Las librerías más importantes son:
- [Transformers](https://github.com/huggingface/transformers)
- [PEFT](https://github.com/huggingface/peft)
- [TRL](https://github.com/huggingface/trl)
