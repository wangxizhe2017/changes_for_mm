# changes_for_mm


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#mmdetection">1. MMDetection</a>
      <ul>
        <li><a href="#comment-off">Comment off several assertions</a></li>
        <li><a href="#add-xizhe">Add xizhe</a></li>
        <ul>
          <li><a href="#datasets">Datasets</a></li>
        </ul>
        <li><a href="#add-utils">Add utils</a></li>
      </ul>
    </li>
    <li>
      <a href="#mmyolo">MMYOLO</a>
    </li>
  </ol>
</details>

## 1. MMDetection
### Comment off several assertions

Purpose: We can set multi-scale image input in config files.

Comment off in mmdet.datasets.pipelines:

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


### Add xizhe

It mainly contains the self-defined code files.

#### Datasets


### Add utils

It mainly contains the self-defined config files.




## MMYOLO
