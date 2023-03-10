# 3D Object Detection with SECOND on MORAI dataset

This repository is based on [OpenPCDet](https://github.com/open-mmlab/OpenPCDet). All configurations and codes were revised for MORAI dataset.

## Results and Models

### SECOND

Class accuracy is IoU(Intersection over Union).

| Dataset | epoch | bbox AP(0.70) | bev AP(0.70) | bev AP(0.50) | 3d AP(0.70) | 3d AP(0.50) | aos | config | log | model |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Real | 80 | 84.46 | 62.83 | 74.31 | 50.25 | 73.52 | 82.70 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Daegu | 80 | 84.99 | 74.59 | 76.46 | 62.33 | 74.77 | 79.15 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Daegu(Mix) | 80 | 89.15 | 82.55 | 82.95 | 79.16 | 82.95 | 85.35 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sejong BRT 1 | 80 | 83.83 | 69.59 | 70.00 | 64.84 | 69.88 | 80.02 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sejong BRT 1(Mix) | 80 | 81.18 | 70.19 | 70.45 | 61.56 | 70.21 | 76.22 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sangam Edge | 80 | 81.56 | 66.73 | 69.28 | 63.02 | 68.00 | 65.41 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sangam Edge(Mix) | 80 | 86.13 | 74.10 | 78.45 | 69.27 | 76.16 | 65.09 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sejong BRT 1 Edge | 80 | 77.42 | 47.88 | 51.16 | 45.33 | 48.04 | 73.58 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |
| Sejong BRT 1 Edge(Mix) | 80 | 88.93 | 80.99 | 81.34 | 80.39 | 81.31 | 85.76 | [config](tools/cfgs/custom_models/second.yaml) | [log] | [model] |

Real:

![image](https://user-images.githubusercontent.com/121915405/213386469-22418eb1-a206-479a-b261-99d770acb720.png)

Daegu:

![image](https://user-images.githubusercontent.com/121915405/213386552-a2ba16e3-82d9-47ae-821e-626e3611e626.png)

Sejong BRT 1:

![image](https://user-images.githubusercontent.com/121915405/213386621-46b1e287-d918-413d-a71d-6fdbc9fba16e.png)

Sangam Edge:

![image](https://user-images.githubusercontent.com/121915405/213386694-fb9d6d37-f116-49d4-956d-e54bfbf5332b.png)

Sejong BRT 1 Edge:

![image](https://user-images.githubusercontent.com/121915405/213386731-c83ac329-310d-4f96-b4c0-3ebec901d28e.png)


## Usage

### Installation

Please refer to [install.md](docs/install.md) for installation, dataset preparation and making configuration file.

### Testing

```
python test.py --cfg_file ${CONFIG_FILE} --batch_size ${BATCH_SIZE} --ckpt ${CKPT}
```

Example:
```
python test.py --cfg_file cfgs/custom_models/second.yaml --batch_size 4 --ckpt ../ckpt/custom_model/second_daegu.pth
```

### Training

```
python train.py --cfg_file ${CONFIG_FILE}
```

Example:
```
python train.py --cfg_file cfgs/custom_models/second.yaml
```

### Demo

```
python demo.py --cfg_file ${CONFIG_FILE} \
    --ckpt ${CKPT} \
    --data_path ${POINT_CLOUD_DATA}
    (--ext .npy)
```

Default --ext is .pcd. But custom point cloud is .npy

Example:
```
python demo.py --cfg_file cfgs/custom_models/second.yaml \
    --ckpt ../ckpt/custom_model/second_daegu.pth \
    --data_path ../data/custom/points/000000.npy
    --ext .npy
```
