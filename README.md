# Gamification Case Videos

本仓库用于存放“游戏化立案”项目的普法视频交付资产，供前后端联调、对象存储迁移或后续发布使用。

## 当前交付范围

- 案件类型：`42` 类
- 视频总量：`208` 条
- 视频类型：每题仅 `C` 选项视频
- 当前状态：`208/208` 已质检通过

## 目录结构

- `videos/deliverable/`
  - 最终交付版视频目录
  - 目录规则：`{案种序号}_{案件类型}/q{题号}_c.mp4`
- `mapping/`
  - 视频映射表与清单
  - `视频生成_manifest_反馈合并版.csv`
  - `视频生成_manifest_反馈合并版.json`

## 开发接入说明

开发联调时请以 `mapping/视频生成_manifest_反馈合并版.csv` 或 `mapping/视频生成_manifest_反馈合并版.json` 为准，不要扫描目录猜文件，也不要假设每个案种固定 `5` 题。

需要特别注意：

- `01_直播艺人经纪` 只有 `q1-q4`
- `02_电商代运营` 只有 `q1-q4`
- 其余 `40` 类案件均为 `q1-q5`
- 视频编码统一为 `H.264 + AAC`
- 视频分辨率统一为 `1080x1920`

## 映射字段说明

映射表中常用字段如下：

- `case_no`：案种序号
- `case_type`：案件类型
- `question_no`：题号
- `status`：当前视频状态
- `deliverable_video_path`：最终交付视频相对路径
- `role`：该案种使用的数字人角色
- `actual_duration_seconds`：实际时长
- `video_codec` / `audio_codec` / `resolution`：交付编码信息

## 推荐接入方式

前端或后端建议使用如下逻辑：

1. 读取 manifest
2. 以 `case_no + question_no` 或业务侧题目映射定位记录
3. 读取 `deliverable_video_path`
4. 按该路径加载对应 `mp4`

## 说明

- 本仓库当前以交付版视频为主，不再依赖 `videos/final`
- 映射表状态已更新为 `质检通过`
- 如果后续有返工或补版，应同步更新本仓库的 `mapping/` 清单
