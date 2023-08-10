# object tracking

## algorithm and models
  - pytracking [github](https://github.com/visionml/pytracking)
  - mmlab model zoo [github](https://github.com/open-mmlab/mmtracking/blob/master/docs/zh_cn/model_zoo.md)
  - CVPR 2022 [論文推薦](https://cloud.tencent.com/developer/article/2020116)

### track-by-detect vs end-to-end
  - track-by-detect 基礎算法 [reference](https://zhuanlan.zhihu.com/p/628015159)
    - Euclidean distance tracking
    - SORT
    - DeepSORT
    - ByteTrack
  - end-to-end 模型範例
    - mixFormer(2022)
    - RTS(ECCV2022)
    - keeptrack(2021)
### multi/single object tracking
  - multi object tracking [reference](https://peaceful0907.medium.com/%E5%88%9D%E6%8E%A2%E7%89%A9%E4%BB%B6%E8%BF%BD%E8%B9%A4-multiple-object-tracking-mot-4f1b42e959f9)
  - single object tracking [paper](https://arxiv.org/ftp/arxiv/papers/2201/2201.13066.pdf)

## datasets
  - paper with code [resources](https://paperswithcode.com/datasets?task=object-tracking)

### LaSOT (Large-scale Single Object Tracking)
  - data download: [resource](https://huggingface.co/datasets/l-lt/LaSOT/tree/main)
  - paper: [CVPR-2019](https://openaccess.thecvf.com/content_CVPR_2019/papers/Fan_LaSOT_A_High-Quality_Benchmark_for_Large-Scale_Single_Object_Tracking_CVPR_2019_paper.pdf)
  - 分析: [reference](https://blog.csdn.net/MJ17709005513/article/details/120961344)
    - 1400個影片(超過3.5M幀)
    ![image](https://github.com/cyhkelvin/Learning/blob/main/resources/object_tracking_datasets_statistics.png)
    - 物件追蹤資料集的困難: 高質量/高密集度的標記、追蹤長/短期、類別bias
      因此分為密集基準、非密集基準的資料集(e.g. annotation per 30 frames)
    - 標記規則細緻，例如: 老鼠標記時不包含尾巴
    - 標記團隊、驗證過程嚴謹
    - 影片屬性分布
      - 光照變化    IV The illumination in the target region changes 
      - 視點變化    VC Viewpoint affects target appearance significantly
      - 離開視野    OV The target completely leaves the video frame 
      - 完全遮擋    FOC The target is fully occluded in the sequence 
      - 部分遮擋    POC The target is partially occluded in the sequence 
      - 運動模糊    MB The target region is blurred due to target or camera motion
      - 攝影機運動  CM Abrupt motion of the camera 
      - 快速運動    FM The motion of the target is larger than the size of its bounding box
      - 物體旋轉    ROT The target rotates in the image 
      - 物體變形    DEF The target is deformable during tracking 
      - 背景雜波    BC The background has the similar appearance as the target
      - 尺度變化    SV(scale variation) The ratio of bounding box is outside the rage [0.5, 2]
      - 長寬比變化  ARC(aspect ratio change) The ratio of bounding box aspect ratio is outside the rage [0.5, 2]
      - 低分辨率    LR The target box is smaller than 1000 pixels in at least one frame
        ![image](https://github.com/cyhkelvin/Learning/blob/main/resources/LaSOT_video_attribute_distribution.png)
### OTB (Object Tracking Benchmark)
  - 與 VOT 進行比較 [reference](https://blog.csdn.net/Tang_Zhe/article/details/121827534)
  - 11種變化: 光照變化、尺度變化、遮擋、形變、運動模糊、快速運動、平面內旋轉、平面外旋轉、出視野、背景干擾、低像素
  - 矩形框初始化時+隨機干擾
  - 強調初始化robustness(擾亂時序、空間上真實目標的位置初始狀態)
  - 評價指標: 
    - precision plot, 預測與答案的中心位置誤差(Average Pixel Error)
    - success plot, 邊框重疊率的AUC, AOR(Average overlap rate)
    - temporal/spatial robustness evaluation
### VOT (Visual Object Tracking)
  - 沒有灰度，更精細，分辨率較高，從第一幀開始
  - 強調檢測、追蹤不分離
  - 評價指標
    - accuracy(AOR)/robustness(定義追蹤失敗)
    - EFO(equivalent filter operations) 衡量追蹤速度
    - EAO(expected average overlap) 影片時序長度為橫軸，準確率為縱軸