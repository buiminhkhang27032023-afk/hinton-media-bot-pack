# Hinton Media — Bot Pack & Pipeline

Đóng gói ngày **2026-10-05**: điều phối viên (bố của các bot), roles/personas, skills, bài học, và metadata job mẫu.

## Nội dung

- `BOTS.md` — roster + ID bot
- `roles/` / `personas/` — brief từng bot
- `skills/` — hinton-orchestrate, getting-started, map-animation (+ `skills/live/` bản đang chạy)
- `docs/` / `pipeline-docs/` — playbook, voice-lock, bootstrap
- `lessons/` — bài học vận hành
- `jobs/` — JOB.md + script/research text (không gồm mp4)

## Lưu ý

- MP4/WAV không commit (Drive: Hinton Media - Videos).
- OmniVoice male clone v2, speed 1.2, voice_locked:true.
- 1 render: `flock /workspace/video-jobs/.render.lock`

## Luồng

- Tin AI: Bot5 → bố chọn → Bot3 → QA → Bot2
- Douyin: Bot4 → Bot5 → Bot3 → QA → Bot2B
- Phiếu: `JOB|status|version|path|next`
