# monoRGBNet
Monocular three-dimensional object detection using nuScenes dataset

Tests with default configs. Run in ~/monoRGBNet/second.pytorch/second/pytorch

python train.py train --config_path=../configs/nuscenes/all.fhd.config --model_dir=model_dir/

Notes:

Make sure to add second to PYTHONPATH:
export PYTHONPATH="/home/donnelly_patrick_t/second.pytorch/"

Make sure to specify blank model directory or specify resume

Path to data: /home/donnelly_patrick_t/data/mini/data/sets/nuscenes

(train_input_reader)
database_info_path: "/home/donnelly_patrick_t/data/sets/nuscenes/infos_train.pkl"
dataset_class_name: "v1.0-mini"
kitti_info_path: "/home/donnelly_patrick_t/data/mini/data/sets/nuscenes/infos_train.pkl"
kitti_root_path: "/home/donnelly_patrick_t/data/mini/data/sets/nuscenes/"

(eval_input_reader)
database_info_path: "/home/donnelly_patrick_t/data/mini/data/sets/nuscenes/infos_val.pkl"
dataset_class_name: "v1.0-mini"
kitti_info_path: "/home/donnelly_patrick_t/data/mini/data/sets/nuscenes/infos_val.pkl"
kitti_root_path: "/home/donnelly_patrick_t/data/mini/data/sets/nuscenes/"

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

dataset_class_name needs to be in REGISTERED_DATASET_CLASSES. Try NuScenesDataset
