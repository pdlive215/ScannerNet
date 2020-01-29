# monoRGBNet
Monocular three-dimensional object detection using nuScenes dataset

#### System

Ubuntu 16.04 / 18.04 (developed on 18.04)  
gcc (developed on 6.3.0)  
cmake >= 3.13.2 (developed on 3.16.3)  
Python 3.6 or 3.7 (developed on 3.7.4)  
spconv (follow instructions in monoRGBNet/spconv)
libbz2-dev

Clone repository:  
git clone --recursive https://github.com/pdlive215/monoRGBNet/

Make sure to add second to PYTHONPATH:  
export PYTHONPATH=$PYTHONPATH:$$root directory$$/monoRGBNet/second.pytorch

#### Python package requirements (see requirements.txt)

fire==0.2.1  
numba==0.47.0  
nuscenes-devkit  
matplotlib==3.1.2  
opencv-python==4.1.2
pillow==6.2.2
protobuf==3.11.2
psutil==5.6.7
scikit-image==0.16.2  
scipy==1.4.1  
seaborn==0.10.0  
tensorboardX==2.0
torch==1.0.0
torchvision==0.2.1

#### Create environment variable for data directory. This directory should include the following subdirectories downloaded from the NuScenes dataset  

maps  
samples  
sweeps  
v1.0-mini  
v1.0-trainval

export DATA=$$data directory$$

Run the following commands in $ROOT/monoRGBNet/second.pytorch/second:

Create dataset:  
python create_data.py nuscenes_data_prep --root_path=$DATA --version=<version> --dataset_name="NuscenesDataset" --version=<version> --max_sweeps=10
  
This creates a ground truth database at $DATA/gt_database  
You can also create a ground truth database with velocity by specifying --dataset_name="NuscenesDatasetVelo"

Train:  
python train.py train --config_path=../configs/nuscenes/$$config file$$--model_dir=$$model directory$$


Notes:



Make sure to specify blank model directory or specify resume

Path to data: /home/donnelly_patrick_t/data/sets/nuscenes/

mini data path: "/home/donnelly_patrick_t/data/sets/nuscenes/

Run create_data.py to generate .pkl files first

(for mini)
python create_data.py nuscenes_data_prep --root_path=/home/donnelly_patrick_t/data/sets/nuscenes --version="v1.0-mini" --dataset_name="mini"

8 train scenes, 2 val scenes

don't worry about error for now -- writes to root path

(train_input_reader)
database_info_path: "/home/donnelly_patrick_t/data/sets/nuscenes/infos_train.pkl"
dataset_class_name: "v1.0-mini"
kitti_info_path: "/home/donnelly_patrick_t/data/sets/nuscenes/infos_train.pkl"
kitti_root_path: "/home/donnelly_patrick_t/data/sets/nuscenes/"

(eval_input_reader)
database_info_path: "/home/donnelly_patrick_t/data/sets/nuscenes/infos_val.pkl"
dataset_class_name: "v1.0-mini"
kitti_info_path: "/home/donnelly_patrick_t/data/sets/nuscenes/infos_val.pkl"
kitti_root_path: "/home/donnelly_patrick_t/data/sets/nuscenes/"

fix these everywhere! (e.g. at train_input_reader)

Make sure to edit config (looks like "database_sampler" and "dataset" got flipped?):

train_input_reader: {
  ...
  database_sampler {
    database_info_path: "/path/to/dataset_dbinfos_train.pkl"
    ...
  }
  dataset: {
    dataset_class_name: "DATASET_NAME"
    kitti_info_path: "/path/to/dataset_infos_train.pkl"
    kitti_root_path: "DATASET_ROOT"
  }
}
...
eval_input_reader: {
  ...
  dataset: {
    dataset_class_name: "DATASET_NAME"
    kitti_info_path: "/path/to/dataset_infos_val.pkl"
    kitti_root_path: "DATASET_ROOT"
  }
}

dataset_class_name needs to be in REGISTERED_DATASET_CLASSES

try dataset_name="NuScenesDataset"

python create_data.py nuscenes_data_prep --root_path=/home/donnelly_patrick_t/data/sets/nuscenes/ --
version="v1.0-mini" --dataset_name="NuScenesDataset"


