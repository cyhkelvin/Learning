# object detection

## algorithms
  - paper resources [reference](https://procjx.github.io/2020/08/04/%E3%80%90arxiv%E8%AE%BA%E6%96%87%E3%80%91%20Computer%20Vision%20and%20Pattern%20Recognition%202020-08-04/)

## datasets
  - paper with code [resources](https://paperswithcode.com/datasets?task=object-detection)

### quality of a dataset
  - [reference](https://yulongtsai.medium.com/object-detection-data-collection-16d551526a33)
  - good generalization/data diversity/nothing or background/物件總類數量的平均
      - 物體: 視角，光照條件，物體形變，遮擋，混亂背景，待側物體變異
      - 場景: 光照，角度，尺度(距離)，遮擋，背景
      - 取像裝置: 解析度，對比，對焦
    - Learning curve 推估需要資料量
    - 資料處理: 格式統一，資料清理，折損管理，標記範例，分割原則
  - 標記流程規範
    - 標記範例: 追蹤時長、物體遮蔽、物件類別數量平均、環境平均
    - 資料儲存格式
    - 分割資料集定義 (train/dev/test)
    - 推估需求資料量
    - 訂定評估標準: 初始模型+數據指標