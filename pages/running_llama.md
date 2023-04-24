A few tips for running one of the openly available (LLaMA-based) LLMs locally.


# On CPU
https://github.com/ggerganov/llama.cpp is a repository with code that allows you to run LLaMA inference on the CPU.

Setting this up is quite straightforward, the steps should be as follows (on mac/linux anyway):
 - Clone the repository.
 - Run `make` in the repository's root directory from a terminal.
 - Download model weights and move them to the `models/` directory.
    - The easiest approach is to find the weights pre-quantized for whatever model you want to use.
    - The file format you want them in is ggml, although others can work as well by first converting with the `convert.py` script.
    - A lot of the variants you could want can be found on HuggingFace (and probably various other places online).
      - The 4-bit quantized weights of the 13B params version of Koala (see 'Background' section below) can be found [here](https://huggingface.co/TheBloke/koala-13B-GPTQ-4bit-128g-GGML).
      - I haven't yet found 4-bit 13B LLaMA weights in ggml format, but they are available in another format [here](https://huggingface.co/camelids/llama-13b-int4-gptq-groupsize128-safetensors).
 - Everything should be ready, inference works by running `./main`, but you should probably use the scripts in `examples/` which are configured to work well out of the box.
    - For example, if you downloaded the Koala weights, run: `MODEL=models/koala-13B-4bit-128g.GGML.bin examples/chat-13B.sh` which will launch a ChatGPT-like chatbot in your terminal.

In my experience running the 4-bit quantized 13-billion parameter models requires about 12GB of memory, and the 7-billion version about 6.5GB.

For this package there are also python-bindings available [here](https://github.com/abetlen/llama-cpp-python), which also comes with an API that is compatible with the OpenAI API.


# On GPU
It is also possible to run these models on (Nvidia) GPUs, which will allow for faster inference.
However, it does require a GPU with enough RAM.
I have succesfully followed the steps from [this package](https://github.com/oobabooga/text-generation-webui/) to make this too work with [4-bit quantization](https://github.com/oobabooga/text-generation-webui/blob/main/docs/GPTQ-models-(4-bit-mode).md), which allowed me to run the 7b parameter models on my GPU. Although, with my measly GTX1660 Super it's only a bit faster than running on CPU with the method above.



# Background
## LLaMA 
Released in February by Meta, it's the latest and best performing openly available large language model.
It comes in four sizes: 7, 13, 33, or 65 billion parameters.
Officially, the weights are only available for researchers who request and obtain access from Meta, but in practice they are all over the internet.

### ChatGPT-like derivatives
Multiple groups have fine-tuned LLaMA to be a ChatGPT-like chatbot.
These are the ones I looked at in some detail, but many others exist.
The links to the parameters here are the official links, with weight differences. 
In order to use them you would first need to obtain the original LLaMA weights, and then combine them.
- [Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html) ([7b](https://huggingface.co/tatsu-lab/alpaca-7b-wdiff/tree/main)) - released March 13th
  - Data: Self-instruct from davinci-003 API (52K samples, public)
- [Vicuna](https://vicuna.lmsys.org/) ([7b, 13b](https://github.com/lm-sys/FastChat#vicuna-weights)) - released March 31st
  - Data: User-shared conversations from ShareGPT (70K samples, private)
- [Koala](https://bair.berkeley.edu/blog/2023/04/03/koala/) ([7b, 13b](https://drive.google.com/drive/folders/10f7wrlAFoPIy-TECHsx9DKIvbQYunCfl)) - released April 3rd
  - Data: User-shared conversations from ShareGPT (60K samples, public); HC3; OIG; Alpaca data; Anthropic HH; OpenAI WebGPT; OpenAI Summarization.

However, others have combined and quantized the weights already, so for each model you can usually find these pretty easily (see 'Getting started' section).

## Quantization
It turns out that quite a bit of the information in the parameters can be 'thrown away' without affecting the performance of the model much.
So, 'quantization' is used to get the best performance with the computational resources we have.
The sweet spot seems to be 4-bit quantization (down from 16-bit) see for example https://github.com/qwopqwop200/GPTQ-for-LLaMa for some performance comparisons.

