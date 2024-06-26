# InternImage

InternImage is developed on top of **mmsegmentation**: `0.27.0`. The most recent commit of this repo occurred on the 28th of July 2022. **mmsegmentation** is a repo of **OpenMMLab**.

The documentation for the **OpenMMLab** repositories is known to be sparse, ambiguous and "awful" (https://medium.com/@george.pearse/how-to-train-a-model-with-mmdetection-8ab6a6fea3f0)
## InternImage Dependencies

### InternImage Dependency Versions 

- **mmsegmentation**: `0.27.0`
- **mmcv-full**:      `1.5.0`
- **tim**:            `0.6.11`
- **mmdet**:          `2.28.1`
- **openmim**

`mmcv-full` is a dependency of `mmsegmetation`.

mmcv has two versions, which were previously: `mmcv-full` which support CUDA ops 'out of the box' ... and `mmcv` without CUDA ops (referenced to as mmcv lite). 
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

Initially, it was thought that the specific version, 1.5.0, was causing the error. However, upon further investigation, it was found that when installing `mmcv-full` the installation hangs indefinitely (https://github.com/open-mmlab/mmcv/issues/1386)

The solution to the hanging seems to be to install `mmcv==2.0.0` and `mmengine`.  In the migration mentioned above, components of `mmcv-full` were transferred to a `mmengine`. `mmengine` serves as the training engine of all OpenMMLab codebases. Indeed by installing `mmcv==2.0.0`, hanging is prevented. However, `mmcv==2.0.0` is not compatible with `mmsegmentation==0.27.0`. 

I spend most of last week attempting to resolve these issues. Im not sure if there is a solution and even if there is one, I am use sure as to how long it would take to find it. 








