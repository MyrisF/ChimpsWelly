# ChimpsWelly

ChimpsWelly is a small chimpanzee video set recorded at Wellington Zoo. It contains **25 clips**, **1,078 pose-annotated frames**, and per-segment labels for locomotion and the support surface.

Paper: *Cross-Zoo Transfer of Chimpanzee Pose Estimation and Chimp–Object Interaction Recognition* (Submitted IVCNZ 2026)

## Demo

Ground truth vs dual-head predictions on held-out clips (compressed preview).

https://github.com/user-attachments/assets/59ae9643-e2ea-4509-a75c-72c041cb11b6

The full-resolution file is [`demos/dual_head_demo.mp4`](demos/dual_head_demo.mp4) (~72 MB).

## Download

Clone this repository. Raw clips are in `videos/`.

## Files

| Path | Description |
|------|-------------|
| `videos/*.mp4` | 25 source clips |
| `clips.csv` | Clip id, filename, outer CV fold, annotated frame range |
| `annotations/pose_coco.json` | COCO-style keypoints for 1,078 frames |
| `annotations/gt_action_object.csv` | Action and object segments |
| `splits/fold1.json` … `fold5.json` | Video-level 5-fold splits (20 train / 5 held-out) |
| `demos/dual_head_demo.mp4` | Full-resolution paper demo montage (~72 MB) |

`clips.csv` column `fold` is the held-out group in the nested cross-validation protocol: when fold \(k\) is locked, those five videos are the test set.

## Labels

**Pose.** Thirteen body points (head, shoulders, elbows, wrists, hips, knees, and ankles) in `pose_coco.json`. Image `file_name` is prefixed by the clip name (for example `pose1/…`).

**Action** (one of): `walk`, `stand`, `sit`, `other`.

**Object** (one of): `wood`, `rock`, `grass`, `none` (no wood/rock/grass support).

Interaction labels in `gt_action_object.csv` use inclusive `[start_frame, end_frame]`. The columns to use are `video`, `start_frame`, `end_frame`, `gt_action`, and `gt_object`.

## Citation

Please cite the IVCNZ paper. Footage courtesy of Wellington Zoo.

## Licence

Research use of this release should credit Wellington Zoo. Redistribution or commercial use requires permission from the data providers.
