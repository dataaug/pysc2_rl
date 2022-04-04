## Packages
* [pysc2](https://github.com/deepmind/pysc2) v1.2
* [sc2client-proto](https://github.com/Blizzard/s2client-proto) v3.18.0
* [pytorch](https://github.com/pytorch/pytorch) v0.4.0
* [StarCraft II (Linux)](https://github.com/Blizzard/s2client-proto#downloads) v.3.16.1
* [tensorboardX (Tensorboard for Pytorch)](https://github.com/lanpa/tensorboard-pytorch) v1.0
* common packages

  * [psutil](https://github.com/giampaolo/psutil)
  * [cloudpickle](https://github.com/cloudpipe/cloudpickle)

Python3 is required to resolve [multiprocessing issue](https://github.com/ikostrikov/pytorch-a3c/issues/37).

Detail installation [steps](#installation).

## Usage
- `<project_path>`: full path of this repo in local environment
- `<hose_name>`: host name of local environment (ex. `localhost`) 
### Train
To train agent in "FindAndDefeatZerglings" mini game with 8 different worker threads:
```bash
cd <project_path>
python -m rl.main --map-name FindAndDefeatZerglings --num-processes 8
```
Use `python rl/main.py --help` to see all available options.

To train with GPU, use `--gpu_ids` option. Default is CPU only.
```bash
# Use two GPUs for example
python -m rl.main --map-name FindAndDefeatZerglings --gpu_ids 0 1 --num-processes 8 
```

### Monitor
To visualize training progress stats, run Tensorboard (tensorflow required).
```bash
tensorboard --logdir <project_path>/output/summaries
```
Then open the link [http://<host_name>:6006](http://<host_name>:6006) in browser.

### Output
All output files are located in `<project_path>/output` by default.
- Trained models: `<project_path>/output/models`
- Logs/Temp files: `<project_path>/output/logs`
- Tensorboard summary logs: `<project_path>/output/summaries`

## <a id='installation'></a> Installation
#### pytorch
Follow instruction [here](http://pytorch.org) and chose OS, Package Manager, Python version and CUDA version accordingly.
- Linux
```bash
# check cuda version
nvcc --version
# use CUDA 9.1 as example
pip3 install http://download.pytorch.org/whl/cu91/torch-0.4.0-cp35-cp35m-linux_x86_64.whl 
```
- OS X
```bash
# no GPU as example
pip3 install torch
```
#### pysc2
```bash
pip install pysc2
```
#### tensorboardX
```bash
pip install git+https://github.com/lanpa/tensorboard-pytorch
# TensorFlow is required for dashboard visualization
pip install tensorflow
```

## References
pytorch reinforcement learning
- [pytorch-a3c](https://github.com/ikostrikov/pytorch-a3c) - pytorch A3c implementation
- [rl_a3c_pytorch](https://github.com/dgriff777/rl_a3c_pytorch) - pytorch A3C with GPU

pysc2 integratioin
- [pysc2-agents](https://github.com/xhujoy/pysc2-agents) - pysc2 A3C agent with FullyConv model and epsilon greedy exploration by Tensorflow
- [pysc2-rl-agents](https://github.com/simonmeister/pysc2-rl-agents) - pysc2 A2C agent with FullyConv model by Tensorflow


## Conda 安装 windows环境 （测试机器3060ti）
conda create -n hyt_sc2 python=3.7
conda install pytorch==1.7.0 torchvision==0.8.0 torchaudio==0.7.0 cudatoolkit=11.0 -c pytorch
pip install pysc2==1.2
pip install pyyaml
