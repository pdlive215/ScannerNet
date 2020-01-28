# monoRGBNet
Monocular three-dimensional object detection using nuScenes dataset

System

Ubuntu 16.04 / 18.04 (developed on 18.04)
gcc (developed on 6.3.0)
cmake >= 3.13.2 (developed on 3.16.3)
Python (developed on 3.7.4)
pytorch 1.0.0 (does not work on 1.4!)
spconv (follow instructions in monoRGBNet/spconv)

Requirements (pip/conda; put these in .txt file)

scikit-image 
scipy 
numba 
pillow 
matplotlib
fire 
tensorboardX 
protobuf 
opencv-python

Tests with default configs. Run in ~/monoRGBNet/second.pytorch/second/pytorch

python train.py train --config_path=../configs/nuscenes(/mini)/all.fhd.config --model_dir=model_dir/

Notes:

Make sure to add second to PYTHONPATH:
export PYTHONPATH="/home/donnelly_patrick_t/monoRGBNet/second.pytorch/"

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
