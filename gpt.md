

# 安装

[参考链接](https://github.com/ymcui/Chinese-LLaMA-Alpaca/wiki/%E4%BD%BF%E7%94%A8text-generation-webui%E6%90%AD%E5%BB%BA%E7%95%8C%E9%9D%A2) 



##
cuda 11.2 不行
```shell
wget https://developer.download.nvidia.com/compute/cuda/11.5.0/local_installers/cuda_11.5.0_495.29.05_linux.run
sudo sh cuda_11.5.0_495.29.05_linux.run
```


```shell
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.3.1-Linux-x86_64.sh
```

[创建虚拟环境](https://zhuanlan.zhihu.com/p/94744929) 


```shell
conda create -n text-generation-webui_1 python=3.10
conda activate text-generation-webui_1
```
或者执行`source activate text-generation-webui_1`。

```shell
ssh ubuntu@172.21.121.130
```


```shell
/home/ubuntu/anaconda3/envs/text-generation-webui_1/bin/python server.py --model llama-7b-hf --lora chinese-alpaca-lora-7b --cpu

/home/ubuntu/anaconda3/envs/text-generation-webui_1/bin/python scripts/openai_server_demo/openai_api_server.py --base_model /home/ubuntu/gpt/model  --gpus 0,1

--lora_model /path/to/lora_model
```




# llama

## linux
```shell
torchrun --nproc_per_node 1 example.py --ckpt_dir /home/ubuntu/llama/model/7B --tokenizer_path /home/ubuntu/llama/model/tokenizer.model
```

## windows下运行
```shell
D:\gpt\Anaconda3\Scripts\pip install https://download.pytorch.org/whl/cu90/torch-1.1.0-cp37-cp37m-win_amd64.whl  -i http://mirrors.aliyun.com/pypi/simple/  --trusted-host mirrors.aliyun.com


D:\gpt\Anaconda3\Scripts\pip.exe install -r requirements.txt

D:\gpt\Anaconda3\Scripts\pip.exe install -e .

torchrun --nproc_per_node 1 example.py --ckpt_dir D:\ssd\LLaMA\7B --tokenizer_path D:\ssd\LLaMA\tokenizer.model
```
```



