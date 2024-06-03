# InternImage
My implementation of InternImage and fine-tuning on our custom dataset

Background:
InternImage is developed on top of **mmsegmentation**: `0.27.0`. The most recent commit of this repo occured on the 28th of July 2022. **mmsegmentation** is a subrepository of **OpenMMLab**.

The documentation for the **OpenMMLab** repositories is know to be sparse, ambiguois and "awful" (https://medium.com/@george.pearse/how-to-train-a-model-with-mmdetection-8ab6a6fea3f0)
## InternImage Dependencies

### InternImage Dependency Versions 

- **mmsegmentation**: `0.27.0`
- **mmcv-full**:      `1.5.0`
- **tim**:            `0.6.11`
- **mmdet**:          `2.28.1`
- **openmim**

`mmcv-full` is a dependency of `mmsegmetation`.

`mmcv-full` has been changed to `mmcv`. 

mmcv has two versions, which were previosuly: `mmcv-full` which suppoert CUDA ops 'out of the box' ... and `mmcv` without CUDA ops (referenced to as mmcv lite). 
More recently, with the migration from mmcv 1.x to mmcv 2.x, `mmcv-full` became `mmcv` and `mmcv` (lite) became `mmcv-lite`.


## Installation Issue with mmcv-full

When installing `mmcv-full` version `1.5.0`, 

`!mim install mmcv-full==1.5.0`

(`mim` is OpenMMLab's package manager.)

the following error occurs:

```plaintext
Failed to build mmcv-full
ERROR: Could not build wheels for mmcv-full, which is required to install pyproject.toml-based projects
```
## Possible Solution

Install `mmcv==2.0.0rc4` and `mmcv_full==1.7.1` (note != `1.5.0`)


the mmcv used in mmseg is `2.x` which is incompatable with internImage



When applying transfer learning, the mmsegmentation framework is used. The InternImage model weights and config are found in the InternImage repo. The `EncoderDecoderMask2Former` class is required when loading the model into mmsegmentation. This is a mmsegmentation class, which 

With this migration, components of mmcv were transfered to a `mmengine`. `mmengine` serves as the training engine of all OpenMMLab codebases. 







