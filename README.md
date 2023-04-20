# changes_for_mm


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <ul>
      <a href="#1-mmdetection">1. MMDetection</a>
      <ul>
        <ul><a href="#1-1-comment-off-several assertions">1.1. Comment off several assertions</a></ul>
        <ul><a href="#1-2-add-xizhe">1.2. Add xizhe</a></ul>
        <ul>
          <ul><a href="#datasets">Datasets</a></ul>
        </ul>
        <ul><a href="#add-utils">Add utils</a></ul>
      </ul>
    </ul>
    <ul>
      <a href="#mmyolo">MMYOLO</a>
    </ul>
  </ol>
</details>

## 1. MMDetection
### 1.1. Comment off several assertions

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


### 1.2. Add xizhe

It mainly contains the self-defined code files.



#### Datasets


### Add utils

It mainly contains the self-defined config files.




## MMYOLO
