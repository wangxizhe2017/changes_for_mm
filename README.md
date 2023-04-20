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

#### Datasets

Add `from xizhe.datasets import *` into: `mmdet.datasets.__init__.py` and `__all__`

If any dataset class is self-defined, add it into 



#### Models


### Add utils

It mainly contains the self-defined config files.




## MMYOLO
