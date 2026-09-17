# G1 Moves 筛选动作（适合 Lens110 训练）

来源: https://huggingface.co/datasets/exptech/g1-moves (CC-BY-4.0, MOVIN Studio 动捕, 60 FPS, Mixamo 风格骨架)

## 筛选结果 (实测腿部活动量)

| 文件 | 时长 | 腿角速度 | 手臂角速度 | 双脚同时着地 | 说明 |
|---|---|---|---|---|---|
| B_HandsUp.bvh | 7.4s | 18°/s | 83°/s | 100% | 脚完全不动，纯手臂，直接可用 |
| B_HandsChop.bvh | 29.4s | 38°/s | 81°/s | 95.5% | 原地手臂动作，基本不用改 |
| B_WiggleDance.bvh | 37.3s | 11°/s | 73°/s | 2.4% | 腿几乎不转但采集时身体有起伏，需地面校正 |
| J_Dance20_DWG.bvh | 15.6s | 19°/s | 157°/s | 2.7% | 手臂很活跃，需地面校正 |
| J_Dance1_Modern.bvh | 37.8s | 4°/s | 47°/s | 1.0% | 腿角速度最低但骨盆起伏 34cm，需较强地面校正 |

备注:
- 后三个采集时脚没有贴地约束 (both_feet_ground < 3%), 转换时建议用已有的 footplant/地面压平处理。
- 同一数据集还有 23 支其他舞蹈和更多动作: https://hf-mirror.com/datasets/exptech/g1-moves
- 需要标注来源: G1 Moves (exptech), CC-BY-4.0
