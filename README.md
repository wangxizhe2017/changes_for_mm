# Changes for MM


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <ul>
      <a href="#I-mmdetection">I. MMDetection</a>
      <ul>
        <ul><a href="#1-comment-off-several-assertions">1. Comment off several assertions</a></ul>
        <ul><a href="#2-add-xizhe">2. Add xizhe</a></ul>
        <ul>
          <ul><a href="#dataloader">DataLoader</a></ul>
        </ul>
        <ul>
          <ul><a href="#datasets">Datasets</a></ul>
        </ul>
        <ul>
          <ul><a href="#models">Models</a></ul>
        </ul>
        <ul><a href="#add-utils">Add utils</a></ul>
      </ul>
    </ul>
    <ul>
      <a href="#mmyolo">MMYOLO</a>
    </ul>
  </ol>
</details>

## I. MMDetection
### 1. Comment off several assertions

Purpose: We can set multi-scale image input in config files.

Comment off lines in mmdet.datasets.pipelines:

test_time_aug.py

    class MultiScaleFlipAug
        def __init__: 
            assert mmcv.is_list_of(self.img_scale, tuple)
            
            
transforms.py

    class Resize
        def __init__:
            assert mmcv.is_list_of(self.img_scale, tuple)
            
        def random_select:
            assert mmcv.is_list_of(img_scales, tuple)
            
        def random_sample:
            assert mmcv.is_list_of(img_scales, tuple) and len(img_scales) == 2
            
        def random_sample_ratio:
            assert isinstance(img_scale, tuple) and len(img_scale) == 2


### 2. Add xizhe

It mainly contains the self-defined code files.
It is recommended to put it under the mmdet directory.

#### DataLoader

Everything should be in xizhe.dataloader, 

and all the code inside should NOT import anything from mmdet.datasets in canse of circle import.

##### If any data_loader class is self-defined, 

mmdet.datasets.builder.py
      
    # comment off the original DataLoader
    # from torch.utils.data import DataLoader
    # add the new DataLoader
    from mmdet.xizhe.dataloader import XDataLoader as DataLoader

#### Datasets

Everything should be in xizhe.datasets.

##### If any dataset class is self-defined, 

add `from ..xizhe.datasets import *` into mmdet.datasets.\_\_init\_\_.py,

add the class name into `__all__`,

add the class name into

.dev_scripts.gather_models.py (.dev_scripts is in the mmdetection root folder)
    
    def get_dataset_name:
      name_map = dict(...add it here...)



#### Models

Everything should be in xizhe.models. 

##### If any module class is self-defined, 

add `from ..xizhe.models import *` into mmdet.models.\_\_init\_\_.py.


### Add utils

It mainly contains the self-defined config files.




## MMYOLO
