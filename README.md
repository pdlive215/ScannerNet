# ScannerNet
LIDAR object detection using nuScenes dataset based on SECOND implementation of VoxelNet (https://github.com/traveller59/second.pytorch/)

#### System

Ubuntu 16.04 / 18.04 (developed on 18.04)  
gcc (developed on 6.3.0)  
cmake >= 3.13.2 (developed on 3.16.3)  
Python 3.6 or 3.7 (developed on 3.7.4)  
spconv (follow instructions in monoRGBNet/spconv)
libbz2-dev

Clone repository:  
`git clone --recursive https://github.com/pdlive215/ScannerNet`

Make sure to add second to PYTHONPATH:  
`export PYTHONPATH=$PYTHONPATH:<root directory>/ScannerNet/second.pytorch`

#### Python package requirements (see `requirements.txt`)

`fire==0.2.1`  
`numba==0.47.0`  
`nuscenes-devkit=1.0.1`  
`matplotlib==3.1.2`  
`opencv-python==4.1.2`  
`pillow==6.2.2`  
`protobuf==3.11.2`  
`psutil==5.6.7`  
`scikit-image==0.16.2`  
`scipy==1.4.1`  
`seaborn==0.10.0`  
`tensorboardX==2.0`  
`torch==1.0.0`  
`torchvision==0.2.1`  
`wheel==0.29.0`

#### Install SECOND (see https://github.com/pdlive215/ScannerNet/second.pytorch)

#### Download nuScenes data
Sign up at https://www.nuscenes.org/sign-up  
Go to https://www.nuscenes.org/download  
For fastest experimentation, download the `mini` subset of `trainval`

#### Create environment variable for data directory. This directory should include the following subdirectories downloaded from the nuScenes dataset  

`maps/`  
`samples/`  
`sweeps/` 
`v1.0-mini/`  
`v1.0-trainval/`

`export DATA=<data directory>`

#### Run the following commands in $$root directory$$/ScannerNet/second.pytorch/second

Create dataset:  
`python create_data.py nuscenes_data_prep --root_path=$DATA --version=<version> --dataset_name="NuScenesDataset" --version=<version> --max_sweeps=10`
  
This creates a ground truth database at `$DATA/gt_database`  
You can also create a ground truth database with velocity by specifying `--dataset_name="NuScenesDatasetVelo"`

Train:  
`python train.py train --config_path=../configs/nuscenes/<config file> --model_dir=<model directory>`

Training currently breaks at each evaluation (every 5865 train steps). To resume training, run `python train.py train --config_path=../configs/nuscenes/$$config file$$--model_dir=<model directory> --resume`
