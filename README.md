# monoRGBNet
Monocular three-dimensional object detection using nuScenes dataset

Following https://github.com/nutonomy/nuscenes-devkit, I extract data to /data/sets
Initially, I split data by subset (e.g. trainval01), extracting to e.g. /data/sets/nuscenes, /data/sets/nuscenes2

Nutonomy provides the following raw data:

(Camera -> extract to directory in S3)

v1.0-trainval01_blobs_camera.tgz -> /data/sets/nuscenes
/samples/CAM_BACK (3376 objects, 435.8 MB)
/samples/CAM_BACK_LEFT (3377 objects, 509.7 MB)
/samples/CAM_BACK_RIGHT (3377 objects, 499.5 MB)
/samples/CAM_FRONT (3377 objects, 484.2 MB)
/samples/CAM_FRONT_LEFT (3377 objects, 516.7 MB)
/samples/CAM_FRONT_RIGHT (3377 objects, 491.5 MB)
/sweeps/CAM_BACK (3486 objects, 447.4 MB)

v1.0-trainval02_blobs_camera.tgz -> /data/sets/nuscenes2
/samples/CAM_BACK (3367 objects, 406.9 MB)
/samples/CAM_BACK_LEFT (3368 objects, 468.6 MB)
/samples/CAM_BACK_RIGHT 
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT

v1.0-trainval03_blobs_camera.tgz -> /data/sets/nuscenes3
/samples/CAM_BACK
/samples/CAM_BACK_LEFT
/samples/CAM_BACK_RIGHT
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT
/sweeps/CAM_BACK

v1.0-trainval04_blobs_camera.tgz -> /data/sets/nuscenes4
/samples/CAM_BACK
/samples/CAM_BACK_LEFT
/samples/CAM_BACK_RIGHT
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT
/samples/LIDAR_TOP

v1.0-trainval05_blobs_camera.tgz -> /data/sets/nuscenes5
/samples/CAM_BACK
/samples/CAM_BACK_LEFT
/samples/CAM_BACK_RIGHT
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT
/sweeps/CAM_BACK

v1.0-trainval06_blobs_camera.tgz -> /data/sets/nuscenes6
/samples/CAM_BACK
/samples/CAM_BACK_LEFT
/samples/CAM_BACK_RIGHT
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT

v1.0-trainval07_blobs_camera.tgz -> /data/sets/nuscenes7
/samples/CAM_BACK
/samples/CAM_BACK_LEFT
/samples/CAM_BACK_RIGHT
/samples/CAM_FRONT
/samples/CAM_FRONT_LEFT
/samples/CAM_FRONT_RIGHT 
/sweeps/CAM_BACK (284 objects, 31.6 MB)

v1.0-trainval08_blobs_camera.tgz -> /data/sets/nuscenes8
/samples/CAM_BACK (3433 objects, 422.5 MB)
/samples/CAM_BACK_LEFT (3433 objects, 484.6 MB)
/samples/CAM_BACK_RIGHT (3433 objects, 475.8 MB)
/samples/CAM_FRONT (3433 objects, 432.6 MB)
/samples/CAM_FRONT_LEFT (3433 objects, 477.7 MB)
/samples/CAM_FRONT_RIGHT (1542 objects, 209.1 MB)

v1.0-trainval09_blobs_camera.tgz -> /data/sets/nuscenes9
/samples/CAM_BACK (3439 objects, 508.8 MB)
/samples/CAM_BACK_LEFT (3439 objects, 531.0 MB)
/samples/CAM_BACK_RIGHT (3439 objects, 555.7 MB)
/samples/CAM_FRONT (3439 objects, 532.3 MB)
/samples/CAM_FRONT_LEFT (2583 objects, 394.0 MB)

v1.0-trainval10_blobs_camera.tgz -> /data/sets/nuscenes10
/samples/CAM_BACK (3421 objects, 760.9 MB)
/samples/CAM_BACK_LEFT (2041 objects, 391.6 MB)

This is taking a while to extract in S3, so I'll use the "Mini" subset (3.88 GB) for the MVP
