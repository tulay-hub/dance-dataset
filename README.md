<p align="center"><a href="#zh">🇨🇳 中文</a> &nbsp;|&nbsp; <a href="#en">🇬🇧 English</a></p>
<a id="zh"></a>

# 舞蹈数据集

## 原始数据

`raw_bvh/original_bvh/` 保存原始 BVH 舞蹈源文件，包括普通舞蹈片段和 `g1_moves/` 动作。全身项目、半身
项目和侧滚项目的 `data/raw/bvh` 都指向这里，避免同一份原始数据复制三遍。

## 处理后数据

任务专属 retargeted 数据按项目存放：

- 全身：`projects/01_dance_whole_body/data/processed/retargeted_actions/`；
- 半身/upper-lower 相关实验：`projects/02_dance_half_body/data/processed/retargeted_actions/`；
- 侧滚：`projects/05_side_roll/data/motions/side_roll_retargeted/`；
- 跌倒恢复：`projects/04_fall_to_stand/data/motions/walk0821/`。

文件名中出现 `pkl`、`npy`、`npz`、`csv` 不代表可以互换。使用前记录来源、fps、joint order、root quaternion
顺序、是否贴地/限位修复和对应回放验证。

## 标准流水线

```text
raw BVH/SMPL-X/源机器人 CSV
  -> retarget tool
  -> pkl / CSV / npy 中间产物
  -> self-collision / speed / joint-limit / grounding QA
  -> project data/training
  -> Isaac/MuJoCo replay
  -> project exports
```

训练数据必须和 policy 的 joint/body order 完全一致；只看数组 shape 通过不算验收。

<a id="en"></a>

## English

This repository contains the original dance motion dataset, primarily BVH source clips and dataset documentation. It is a data dependency for the dance and selected retargeting projects; processed training clips belong to the consuming project or framework and should not be mixed silently into the raw source tree.

Before publishing or redistributing the dataset, verify license, performer privacy, attribution, filename mapping, frame rate, coordinate frame, and third-party restrictions. Downstream retargeting should record the input checksum, conversion command, target robot, joint order, quaternion convention, and output validation report.
