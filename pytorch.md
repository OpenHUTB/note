conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes

wget https://repo.anaconda.com/archive/Anaconda3-5.1.0-Linux-x86_64.sh
bash Anaconda3-5.1.0-Linux-x86_64.sh
python3 -m conda install pytorch torchvision cuda80 -c pytorch
python3 -m conda install -c conda-forge tensorboardx


pip install torch-encoding
git clone https://github.com/zhanghang1989/PyTorch-Encoding && cd PyTorch-Encoding
python setup.py install



***************************

https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/
pip install http://download.pytorch.org/whl/cpu/torch-0.4.0-cp35-cp35m-win_amd64.whl