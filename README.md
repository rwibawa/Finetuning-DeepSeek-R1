# Finetuning DeepSeek R1
Finetune DeepSeek R1 | Build a Medical Chatbot

Reference:
* [YT Tutorial](https://youtu.be/qcNmOItRw4U?si=8jWCTKtw_h4XIdvy)
* [Tutorial](https://www.datacamp.com/tutorial/fine-tuning-deepseek-r1-reasoning-model)
* [kaggle](https://www.kaggle.com/)
* [Weight and Biases](https://wandb.ai/)

> Get an API token from `kaggle` and `wandb`.


## 1. Setup
[Install Unsloth](https://github.com/rwibawa/FineTune)
```shell
$ conda activate unsloth_env
```

## 2. Use the model with `ollama`
### 2.1. Install `ollama`
```shell
$ curl -fsSL https://ollama.com/install.sh | sh
```

### 2.2. Run `ollama`
```shell
$ ollama serve
$ ollama help
Large language model runner

Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model from a Modelfile
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information

Use "ollama [command] --help" for more information about a command.
```

### 2.3. Pull & run a model with `ollama`
```shell
$ ollama run 
--verbose hf.co/rwibawa/DeepSeek-R1-Distill-Llama-8B-unsloth-bnb-4bit-Medical-COT
>>> A 61-year-old woman with a long history of involuntary urine loss during activities like coughing
...  or sneezing but no leakage at night undergoes a gynecological exam and Q-tip test. Based on thes
... e findings, what would cystometry most likely reveal about her residual volume and detrusor contr
... actions?
<think>
Alright, so let's think about this 61-year-old woman with a history of involuntary urine loss 
during activities like coughing or sneezing but no leakage at night. She undergoes a 
gynecological exam and Q-tip test. We need to figure out what cystometry would show regarding 
her residual volume and detrusor contractions.

First, let's break down the scenario. She has urinary incontinence that triggers specifically 
when she coughs or sneezes, which sounds like stress incontinence. But it's important to note 
that she's not wetting herself at night, so that suggests that there's a specific issue that's 
only happening during these activities. 

Now, during the gynecological exam, they probably checked her pelvic area and noted that there 
was some involuntary leakage when they examined her for conditions like pelvic relaxation or 
urethral problems. That's usually part of a typical examination to spot issues related to 
incontinence.

Then, we come to the Q-tip test. This test is typically used to assess if there’s urethral 
obstruction. So during this test, they insert a Q-tip catheter and measure how high it rises 
when you push it up. If it doesn't go higher than 2 centimeters without being pushed up by the 
examiner, that might indicate some sort of urethral obstruction.

If the Q-tip test result suggests an obstruction, we're likely dealing with urethral 
obstruction or maybe not enough muscle tone in the urethra to keep it open. This could mean 
there's a functional problem at the urethral level, contributing to her symptoms.

Now, considering these findings together: during activities like coughing, perhaps she can't 
control her sphincter properly because of the obstruction, leading to loss of urine even though 
at night her bladder is likely not full enough or she’s able to hold it without leakage. 

Moving on to cystometry—this will give us a more detailed picture. They'll check how much 
residual volume she has in her bladder and then do a cytometric profile to see what happens 
when she coughs or sneezes. 

If there's an obstruction, during the coughing or sneezing she might not be able to effectively 
relax the urethra, which could mean she experiences a sudden increase in pressure that pushes 
out urine involuntarily without a strong detrusor contraction, as these tests are usually done 
when you're relaxing. 

But wait, if there's an obstruction but her detrusor muscles seem okay—meaning they can 
contract adequately when needed—it should also show up. So in the cystometry, we might see that 
when she coughs or sneezes, there is a sudden rise in pressure without the usual strong 
detrusor contractions.

Putting it all together, with an obstruction indicated by the Q-tip test and symptoms triggered 
during stress, her cystometric findings should point to some residual volume and a clear link 
between her activities like coughing and that obstruction. This would mean that during these 
activities, even though she's not having full detrusor contractions, the obstruction leads to 
loss of urine without needing a big contraction.
</think>
Based on the 61-year-old woman’s symptoms and findings from the gynecological exam and Q-tip 
test, cystometry would most likely reveal that her residual volume is increased due to urethral 
obstruction. Additionally, during activities like coughing or sneezing, there would be an 
involuntary rise in intravesicular pressure without the typical detrusor contraction force. 
This suggests a functional obstruction causing her symptoms, possibly due to insufficient 
urethral muscle tone or structural issues contributing to her stress urinary incontinence.

total duration:       21.8932228s
load duration:        44.8384ms
prompt eval count:    66 token(s)
prompt eval duration: 3ms
prompt eval rate:     22000.00 tokens/s
eval count:           747 token(s)
eval duration:        21.843s
eval rate:            34.20 tokens/s
>>> A 25-year-old male presents with high-grade fever and hypotension, with lab results indicating he
... moglobin at 5 g/dL, total leukocyte count of 9000/mm3, and differential count of 2% polymorphs, 9
... 6% lymphocytes, and 2% eosinophils. What is a treatment option that should be avoided in this cli
... nical scenario?
<think>
Alright, let's try to figure out what kind of situation this young man might be facing based on 
his symptoms and lab results. He has a high fever, which often points towards an infection or 
systemic issue. Then there's the hypotension, which suggests low blood pressure—something like 
sepsis can really cause that kind of drop in blood pressure. 

Looking at his lab results, we see something more concerning: his hemoglobin is only 5 g/dL. 
That's pretty low—it means he has significant anemia, possibly due to a serious underlying 
condition like malaria or other tropical diseases known for their effect on the blood. The 
leukocyte count being quite high—9000/mm3—is suspicious too because it suggests a strong immune 
response, which is typical in severe infections.

And then there's his differential white cell count: 2% polymorphs, 96% lymphocytes, and just 2% 
eosinophils. This combination of elevated lymphocytes is interesting. In the case of malaria, 
for instance, the body tends to respond by increasing the number of lymphocytes to combat the 
infection. So this aligns with a possible diagnosis like malaria. But it's also important to 
think about other tropical diseases that cause anemia and high fever, such as dengue or 
typhoid.

Now, given these symptoms and lab findings, what treatments should we be cautious with? The 
options are pretty broad here, but let's see—since the main focus is on his low blood pressure 
and anemia, it's crucial to think about how different medications could potentially affect him. 
For instance, there might be situations where using certain drugs like quinine or antimalarials 
isn't advisable because of risks like hypotension or arrhythmias, especially if he has other 
serious conditions.

Wait a second, though, let's not forget the unique aspect here: his extremely low hemoglobin. 
When faced with such severe anemia, even though it might seem tempting to jump straight into 
giving blood transfusions, we should be cautious. Blood transfusions can bring on complications 
like acute respiratory distress or circulatory overload in this kind of situation.

And let's not overlook how significant his symptoms are—his high fever is something that could 
get worse before getting better, so any treatment choice needs to be well thought out and safe.

So considering all these factors, I’d say one important thing to keep in mind when thinking 
about treatments for this guy would be to avoid blood transfusions if at all possible. Blood 
transfusions can lead to complications like acute respiratory distress syndrome or circulatory 
overload in this situation, especially given his high fever and anemia. This is really a 
critical point that needs to be considered before deciding on any treatment plan.
</think>
In the clinical scenario described, it would be important to avoid blood transfusions for this 
25-year-old male. Blood transfusions can lead to complications such as acute respiratory 
distress syndrome or circulatory overload, which are significant concerns in someone with 
severe anemia and high fever due to a serious underlying condition like malaria.

total duration:       15.9641597s
load duration:        20.2957ms
prompt eval count:    895 token(s)
prompt eval duration: 14ms
prompt eval rate:     63928.57 tokens/s
eval count:           623 token(s)
eval duration:        15.923s
eval rate:            39.13 tokens/s
>>> Send a message (/? for help)
>>> /bye

$ ollama ps
NAME                                                                              ID              SIZE     PROCESSOR    UNTIL              
hf.co/rwibawa/DeepSeek-R1-Distill-Llama-8B-unsloth-bnb-4bit-Medical-COT:latest    f64fd8a4dc04    10 GB    100% GPU     4 minutes from now    

$ ollama list
NAME                                                                              ID              SIZE      MODIFIED     
hf.co/rwibawa/DeepSeek-R1-Distill-Llama-8B-unsloth-bnb-4bit-Medical-COT:latest    f64fd8a4dc04    8.5 GB    11 hours ago    
```

## 3. `llama.cpp`
### 3.1. Install `cmake`
```shell
$ cd ~/Downloads/
$ sudo apt-get install build-essential libssl-dev
$ wget https://github.com/Kitware/CMake/releases/download/v3.31.6/cmake-3.31.6.tar.gz
$ tar xvfz cmake-3.31.6.tar.gz
$ cd cmake-3.31.6/
$ ./bootstrap 
$ gmake
$ sudo gmake install

$ cmake --help
```

### 3.2. Build `llama.cpp` using `cmake`:
* [Build llama.cpp using CMake](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md)

```shell
# cd llama.cpp/
$ cmake -B build
$ cmake --build build --config Release
$ ll build/bin/
total 68M
-rwxr-xr-x  1 ryan ryan 1.8M Mar 12 07:15 llama-batched*
-rwxr-xr-x  1 ryan ryan 1.8M Mar 12 07:15 llama-batched-bench*
-rwxr-xr-x  1 ryan ryan 503K Mar 12 07:16 llama-bench*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-cli*
-rwxr-xr-x  1 ryan ryan 373K Mar 12 07:17 llama-convert-llama2c-to-ggml*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-cvector-generator*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:15 llama-embedding*
-rwxr-xr-x  1 ryan ryan 1.8M Mar 12 07:16 llama-eval-callback*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-export-lora*
-rwxr-xr-x  1 ryan ryan  27K Mar 12 07:16 llama-gbnf-validator*
-rwxr-xr-x  1 ryan ryan 1.8M Mar 12 07:17 llama-gen-docs*
-rwxr-xr-x  1 ryan ryan  28K Mar 12 07:16 llama-gguf*
-rwxr-xr-x  1 ryan ryan 102K Mar 12 07:16 llama-gguf-hash*
-rwxr-xr-x  1 ryan ryan  47K Mar 12 07:16 llama-gguf-split*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-gritlm*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-imatrix*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-infill*
-rwxr-xr-x  1 ryan ryan 2.1M Mar 12 07:17 llama-llava-cli*
-rwxr-xr-x  1 ryan ryan 494K Mar 12 07:17 llama-llava-clip-quantize-cli*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-lookahead*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-lookup*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-lookup-create*
-rwxr-xr-x  1 ryan ryan  69K Mar 12 07:16 llama-lookup-merge*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-lookup-stats*
-rwxr-xr-x  1 ryan ryan 2.1M Mar 12 07:17 llama-minicpmv-cli*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-parallel*
-rwxr-xr-x  1 ryan ryan 1.8M Mar 12 07:16 llama-passkey*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-perplexity*
-rwxr-xr-x  1 ryan ryan  21K Mar 12 07:17 llama-q8dot*
-rwxr-xr-x  1 ryan ryan 366K Mar 12 07:16 llama-quantize*
-rwxr-xr-x  1 ryan ryan 213K Mar 12 07:17 llama-quantize-stats*
-rwxr-xr-x  1 ryan ryan 2.1M Mar 12 07:17 llama-qwen2vl-cli*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:16 llama-retrieval*
-rwxr-xr-x  1 ryan ryan 1.6M Mar 12 07:17 llama-run*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-save-load-state*
-rwxr-xr-x  1 ryan ryan 3.8M Mar 12 07:17 llama-server*
-rwxr-xr-x  1 ryan ryan  27K Mar 12 07:17 llama-simple*
-rwxr-xr-x  1 ryan ryan  32K Mar 12 07:17 llama-simple-chat*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-speculative*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-speculative-simple*
-rwxr-xr-x  1 ryan ryan 344K Mar 12 07:17 llama-tokenize*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:17 llama-tts*
-rwxr-xr-x  1 ryan ryan  22K Mar 12 07:17 llama-vdot*
-rwxr-xr-x  1 ryan ryan 1.9M Mar 12 07:15 test-arg-parser*
-rwxr-xr-x  1 ryan ryan  18K Mar 12 07:15 test-autorelease*
-rwxr-xr-x  1 ryan ryan 586K Mar 12 07:15 test-backend-ops*
-rwxr-xr-x  1 ryan ryan  22K Mar 12 07:15 test-barrier*
-rwxr-xr-x  1 ryan ryan  16K Mar 12 07:15 test-c*
-rwxr-xr-x  1 ryan ryan 1.6M Mar 12 07:15 test-chat*
-rwxr-xr-x  1 ryan ryan 1.5M Mar 12 07:15 test-chat-template*
-rwxr-xr-x  1 ryan ryan  76K Mar 12 07:15 test-gguf*
-rwxr-xr-x  1 ryan ryan 726K Mar 12 07:15 test-grammar-integration*
-rwxr-xr-x  1 ryan ryan  41K Mar 12 07:15 test-grammar-parser*
-rwxr-xr-x  1 ryan ryan 719K Mar 12 07:15 test-json-schema-to-grammar*
-rwxr-xr-x  1 ryan ryan  46K Mar 12 07:15 test-llama-grammar*
-rwxr-xr-x  1 ryan ryan  34K Mar 12 07:15 test-log*
-rwxr-xr-x  1 ryan ryan  17K Mar 12 07:15 test-model-load-cancel*
-rwxr-xr-x  1 ryan ryan  18K Mar 12 07:15 test-quantize-fns*
-rwxr-xr-x  1 ryan ryan  41K Mar 12 07:15 test-quantize-perf*
-rwxr-xr-x  1 ryan ryan  21K Mar 12 07:15 test-rope*
-rwxr-xr-x  1 ryan ryan  50K Mar 12 07:15 test-sampling*
-rwxr-xr-x  1 ryan ryan 355K Mar 12 07:15 test-tokenizer-0*
-rwxr-xr-x  1 ryan ryan 337K Mar 12 07:15 test-tokenizer-1-bpe*
-rwxr-xr-x  1 ryan ryan 337K Mar 12 07:15 test-tokenizer-1-spm*
```

### 3.3. Converting Safetensors to GGUF model
```shell
$ python llama.cpp/convert_hf_to_gguf.py \
  DeepSeek-R1-Medical-COT/ \
  --outfile llama-3-8b-chat-doctor.gguf \
  --outtype f16
```

### 3.4. Quantizing the GGUF Model
```shell
$ ./llama.cpp/build/bin/llama-quantize \
  llama-3-8b-chat-doctor.gguf \
  llama-3-8b-chat-doctor-Q4_K_M.gguf \
  Q4_K_M
llama_model_quantize_impl: model size  = 15317.02 MB
llama_model_quantize_impl: quant size  =  4685.30 MB

main: quantize time = 525046.75 ms
main:    total time = 525046.75 ms
```