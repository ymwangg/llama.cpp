- Compilation
`make -j LLAMA_CUBLAS=1 LLAMA_PERF=1`

- Use the following command to run on gpu
`CUDA_VISIBLE_DEVICES=0 ./main -m models/Llama-2-7b-chat-hf/ggml-model-f16.gguf -p "What is capitalism?" -ngl 35 -mg 0 -s 0`

- Use lldb to debug
` lldb-15 -f ./main -- -m models/CodeLlama-34b-Python-hf/ggml-model-f16.gguf -p "// Quick-sort implementation in C (4 spaces indentation + detailed comments) and sample usage:\n\n#include" -e -t 4 -n 256 -c 4096 -s 8 --top_k 1`

- LlamaChat
speculative sampling
`CUDA_LAUNCH_BLOCKING=1 CUDA_VISIBLE_DEVICES=0 ./speculative -m ./models/CodeLlama-34b-Python-hf/ggml-model-Q8_0.gguf -md ./models/CodeLlama-7b-Python-hf/ggml-model-Q4_0.gguf -p "// Quick-sort implementation in C (4 spaces indentation + detailed comments) and sample usage:\n\n#include" -e -ngl 1000 -t 4 -n 256 -s 0 --top_k 1 --draft 16 | tee scratch.txt`

normal sampling
`CUDA_LAUNCH_BLOCKING=1 CUDA_VISIBLE_DEVICES=0 ./main -m ./models/CodeLlama-34b-Python-hf/ggml-model-Q8_0.gguf -p "// Quick-sort implementation in C (4 spaces indentation + detailed comments) and sample usage:\n\n#include" -e -ngl 1000 -t 4 -n 256 -s 0 --top_k 1 --draft 16 | tee scratch.txt`
