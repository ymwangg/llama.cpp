- Compilation
`make -j LLAMA_CUBLAS=1`

- Use the following command to run on gpu
`CUDA_VISIBLE_DEVICES=0 ./main -m models/Llama-2-7b-chat-hf/ggml-model-f16.gguf -p "What is capitalism?" -ngl 35 -mg 0 -s 0`
