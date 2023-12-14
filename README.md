# Proyecto Integrador

Este proyecto se enfoca en comparar la capacidad de 3 diferentes LLM a la hora de seguir instrucciones en Español y después responder dudas acerca de un tema muy específico en Español. En este repositorio se incluyen todos los recursos necesarios para poder replicar los resultados y experimentos usando la interfaz [text-generation-webui](https://github.com/oobabooga/text-generation-webui).

### Modelos comparados ###

- [Mistral 7B](https://huggingface.co/mistralai/Mistral-7B-v0.1)
- [LLaMA2 Chat 7B](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)
- [FALCON 7B](https://huggingface.co/ybelkada/falcon-7b-sharded-bf16)

### Entrenamiento para instrucciones en español y leyes ecuatorianas en español

Todos los modelos han sido entrenados usando la técnica de QLORA con las librerías provista por [Hugging Face](https://huggingface.co/docs/transformers/index). Las librerías más importantes son:
- [Transformers](https://github.com/huggingface/transformers)
- [PEFT](https://github.com/huggingface/peft)
- [TRL](https://github.com/huggingface/trl)

### LORA Adapters

Los adaptadores LORA listos para aplicar a los modelos antes mencionados se encuentran en la carpeta LORA. Cada modelo tiene 3 adaptadores:
- Un adaptador solo para instrucciones en español
- Un adaptador solo para instruciones acerca de leyes ecuatorianas en español
- Un adaptador fusionado que contiene ambos en uno solo. Este adaptador se creó ya que PEFT (versión 0.6.2) muchas veces tiene problemas al cargar más de un adaptador a la vez en la interfaz de generación.

### Presets de generación

En la carpeta de GENERATION-PRESETS se encuentran los hyperparámetros que se utilizaron en cada modelo para generar las respuestas que se documentaron para el proyecto. Es posible que con diferentes se obtengan diferentes resultados, ya sean mejores o peores. 

Nota: Para los modelos combinados, el preset recomendado es 'Contrastive Search', un preset incluido en la interfaz de manera predeterminada. 

### Instruction templates

En la carpeta INSTRUCTION-TEMPLATES se encuentran los formatos a usar para cada uno de los modelos. Los formatos son diferentes para cada modelos debido a su arquitectura dada por los creadores.

### ¿Cómo usar cada modelo?

Requerimiento: Mínimo 16GB de VRAM en una tarjeta de video NVIDIA con tecnología CUDA (es posible la ejecución en Apple Silicon e Intel CPU, revisar Wiki de la interfaz [text-generation-webui](https://github.com/oobabooga/text-generation-webui). También se requiren aproximadamente 50GB de espacio de disco para descargar todos los modelos y adaptadores. 

1. Seguir las instrucciones en la página de la interfaz para la instalación del ENV y del programa en sí.
2. Ejecutar la interfaz acorde a las instrucciones.
3. En la pestaña "Model", descargar un modelo de acuerdo a las instrucciones de la interfaz. Seleccionar los modelos provistos anteriormente.
4. Cargar el modelo con la función "load in 8 bit" activada para que el modelo pueda ejecutarse en 16GB de VRAM.
5. Colocar los adaptadores, presets y templates en sus respectivas carpetas dentro de la carpeta de instalación de la interfaz.
6. En la sección "LORA" seleccionar el adaptador que se quiera probar para el modelo cargado.
7. En la pestaña "Parameters" seleccionar el preset provisto para el modelo escogido.
8. En la pestaña "Instruction" seleccionar el preset provisto para el modelo escogido.
9. En la pestaña "Chat" seleccionar el modo 'instruct'.
10. El modelo ya está listo para interactuar con el usuario. 
