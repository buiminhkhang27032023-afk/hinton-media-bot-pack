# QA report — DOUYIN-20261005-01 (v1) · Bot 2B — Douyin

- **QA string:** OmniVoice · male clone v2 locked · 1.2 · voice_locked:true
  - /health: status=ok voice_mode=clone voice_locked=True ref=`voice-lock-vn-v2.wav` (+ `voice-lock-vn-v2.ref.txt`) speed=1.2 (post) seed=1234
  - 17/17 câu TTS qua OmniVoice local `/tts` (127.0.0.1:8123), mỗi câu kiểm header `X-Voice-Locked: true` + `X-Voice-Clone: voice-lock-vn-v2.wav` (log: qa/pipeline.log). Không edge-tts / cloud TTS. Loudnorm 2-pass −14 LUFS / TP −1.5.
- **Engine / template:** HyperFrames 0.8.114 (headless Chrome + GSAP), composition dựng tay theo bảng cảnh 11 shot của `lam-viec/script.md` — F01 HyperFrames neon UI · G07 Douyin remix.
  - Project: `lam-viec/hf/index.html` · generator `lam-viec/custom/gen_hf.py` + `lam-viec/custom/style.css` · render `lam-viec/custom/render.sh` · TTS/align `lam-viec/custom/tts_align.py` (dùng module `/workspace/AI-auto-generate-video/pipeline`: tts_omnivoice, align, text_vi).
  - FFmpeg chỉ dùng để mux audio + tạo bản 720p (`/workspace/video-jobs/deliver.sh`).
- **Render lock:** TTS và render đều chạy trong `flock -w 7200 /workspace/video-jobs/.render.lock`.
- **VO:** nguyên văn `lam-viec/storytelling_script.txt` (bản Bố QA PASS v1: giữ "tháng mười một năm 2024"; 10×10=100 ghi "(ví dụ minh họa)" trên màn; câu cấp quyền cẩn thận) · 17 câu · 247 từ.

## File
| File | Thông số |
|---|---|
| output/storytelling_final.mp4 | h264 1080x1920 30/1 yuv420p High · aac 48000Hz ch=2 51.974s · 52.0s · 20.52 MB (21516456 B) · -14.8 LUFS / TP -4.2 dBFS |
| output/storytelling_mobile_720p.mp4 | h264 720x1280 30/1 yuv420p High · aac 48000Hz ch=2 51.974s · 52.0s · 5.97 MB (6263679 B) |
| output/voice_storytelling.wav | VO-only, 51.523s, -14.8 LUFS / TP -1.5 dBFS, 48 kHz mono |
| output/subtitle.srt | 44 cue, 0.00–51.40s |
| output/storytelling_script.txt | VO đã duyệt |

## ffprobe
- 1080p: resolution 1080×1920 · codec h264 1080x1920 30/1 yuv420p High · audio aac 48000Hz ch=2 51.974s · duration 52.0s
- 720p: resolution 720×1280 · codec h264 720x1280 30/1 yuv420p High · audio aac 48000Hz ch=2 51.974s · duration 52.0s

## Self-QA
- 1080×1920 ✓ · 720×1280 ✓ · H.264 + AAC · video 52.0s = VO 51.52s + 0.45s đuôi.
- SRT: không chồng lấn = True; chữ SRT trùng 100% VO = True; cue cuối 51.40s vs VO 51.52s; 17/17 đầu câu khớp đầu cue (±0.25s). Align: 247 từ, 37 nội suy, 210 từ lấy từ faster-whisper fallback.
- Nghe lại bằng ASR proxy (faster-whisper small int8): độ giống kịch bản **0.795**. Khác biệt ASR (đa phần do tên riêng / tiếng Anh / "em xi pi"):
  - replace: "em xi pi em xi pi" → "mcp mcp"
  - replace: "mười một" → "11"
  - replace: "hai nghìn không trăm hai mươi tư anthropic" → "2024 anthropics"
  - replace: "mười" → "mỗi"
  - replace: "mười" → "mời"
  - replace: "một trăm" → "100"
  - replace: "rối" → "dối"
  - replace: "em xi pi" → "mcp"
  - replace: "phía" → "viết"
  - delete: "phía server là nơi mở ra dữ liệu công cụ và mẫu câu lệnh hai đầu nói chung một ngôn ngữ nên cắm vào là hiểu nhau thay vì nối từng sợi riêng" → ""
  - replace: "chuẩn chung" → "chuẩ the"
  - replace: "tài" → "tai"
  - replace: "bạn" → "mạng"
  - replace: "chung" → "trùm"
  - replace: "phù" → "phụ"
  - replace: "em xi pi" → "mcp"
  - replace: "chữ em xi pi" → "chứ mcp"
- **Không BGM:** track audio = VO + 66 SFX one-shot ngắn theo cột "Âm thanh" của bảng cảnh ({'hit': 9, 'click': 18, 'scan': 4, 'whoosh': 19, 'pop': 16}), gain thấp, không có nhạc nền. Khoảng lặng giữa câu trong VO-only: -91.0…-91.0 dB. Bản VO-only cùng hình: `lam-viec/render/video_vo_only.mp4`.
- **Không burn karaoke/caption** — chỉ chữ khóa kinetic theo cột "Chữ trên màn"; SRT sidecar.
- Khung hình: qa/contact_sheet.jpg (11 cảnh, 70% mỗi cảnh) + qa/frames/. Chữ trong vùng an toàn x 60–940, y 150–1590.
- Hiệu ứng theo bảng cảnh: S1 phích USB-C trượt lên cắm "cạch" + zoom punch + pin sạc, glitch RGB-split sang não AI có ổ cắm nháy, `MCP` slam 160%→100% + flash trắng 2 frame + shake; S2 M/C/P typewriter thành Model/Context/Protocol, chip `CHUẨN MỞ` stamp, 3 icon (database/cờ lê/đám mây) bay vào + dây stroke-draw về lõi AI; S3 timeline scrub dừng 11/2024 + zoom punch, ổ khóa bật mở + `OPEN SOURCE`; S4 4 app ↔ 4 nguồn, 16 sợi dây mọc nhanh dần + camera kéo lùi; S5 búi dây "mì" 26 sợi vẽ dần, counter 0→100, `10 × 10 = 100` + "(ví dụ minh họa)", đổi đỏ + shake + zoom punch; S6 split CLIENT/SERVER slide-in, chat bubble, 3 ngăn 01 Resources/02 Tools/03 Prompts pop theo VO + nhãn Việt; S7 plug snap overshoot, gói `{ }` chạy 2 chiều, viền xanh connected pulse, `JSON-RPC` chữ nhỏ; S8 path-morph búi dây (cùng hình S5) thu về hub MCP, `100` gạch ngang → `1 CHUẨN CHUNG` + zoom punch; S9 kinetic `KHÔNG CHỈ TRẢ LỜI` gạch → `LÀM VIỆC THAY BẠN`, 3 thẻ hành động flip-in + tick xanh; S10 phích cắm thử ổ sai bật ra (bounce) + ✕, viền vàng nháy 2 lần, khiên khóa + 2 dòng `Chọn server phù hợp` / `Cấp quyền cẩn thận`; S11 câu hỏi từng từ, logo Hinton Media scale-in, ô bình luận typewriter `MCP`, nút Follow pulse. Flash + zoom chuyển cảnh mỗi cảnh; progress bar; footer nguồn Anthropic ở S2–S3.
- Cảnh (s): [(0.0, 5.1), (5.1, 10.92), (10.92, 15.51), (15.51, 20.97), (20.97, 23.97), (23.97, 30.07), (30.07, 32.62), (32.62, 35.76), (35.76, 41.3), (41.3, 46.08), (46.08, 51.97)]
- Anchor fallback (mốc hiệu ứng ước lượng thay vì theo từ): không có

## Gaps / lệch spec
- Không có template `frame-*` (frame-liquid-bg-hero, frame-glitch-title, frame-vignelli, …) trên box → dựng tay bằng HyperFrames theo đúng motion trong bảng cảnh (tên template chỉ là gợi ý).
- Không dùng `./run.sh` auto pipeline: preset mặc định là kiểu "Tin AI" (footage/presenter PIP, shot 1.6–3s ngẫu nhiên) — không khớp brief 11 shot HyperFrames neon UI, job không có footage/presenter; dùng fallback HyperFrames theo bảng cảnh (cùng module TTS/align của repo).
- Video gốc Douyin chưa tải được/không dùng: chỉ remix ý tưởng, không lấy hình/lời gốc, không logo kênh gốc.
- Icon/hình là đồ họa vector minh họa (điện thoại, phích, não AI, ổ khóa, khiên), không dùng ảnh thật/logo Anthropic.
- Thẻ "Tra dữ liệu" ở S9 lấy từ bảng cảnh (VO nói "đọc tài liệu và gọi công cụ"); "Dịch vụ" ở S4 là minh họa cho "dịch vụ bên ngoài".
- ASR full-pass (faster-whisper small) bỏ sót đoạn ~27.4–33s (câu "Phía server…", "Hai đầu…", "Thay vì…") → đã spot-check riêng đoạn 27.3–35.8s: audio đủ, nghe ra "…server là nơi mở ra dữ liệu công cụ và mẫu câu lệnh. Hai đầu nói chung một [con] ngữ nên cắm vào là hiểu nhau, [vì] nói từng [xại] riêng, [mọi] bên chỉ cần hỗ trợ một chuẩn [trung]" → lỗi nghe của ASR small, không phải thiếu voice. Thời lượng từng câu TTS bình thường (0.17–0.22 s/âm tiết).
- **Bố nghe lại giúp** (ASR nghe khác; "Phía" và "chuẩn chung" lệch ở cả 2 lượt): "**Phía** client/server" (~25.6s, ~27.6s; ASR nghe "Viết"), "chuẩn **chung**" (~35.3s, ~42.0s; ASR nghe "trung/trùm"), "thay **bạn**" (~41.0s; ASR full-pass nghe "mạng"). OmniVoice khóa seed 1234 nên TTS lại cùng chữ sẽ ra y hệt; muốn sửa phải đổi chữ VO (cần bố duyệt).
- Render 2 lượt: lượt 1 (16:51–16:55) bị tràn chữ ở S1 `AI CÓ CỔNG CHUNG?`, S8 `1 CHUẨN CHUNG`, S9 `LÀM VIỆC THAY BẠN` → giảm cỡ chữ, render lại (17:12–17:15, trong flock), bản giao là lượt 2.
- SFX one-shot có (theo bảng cảnh), không nhạc nền. Nếu cần VO-only: `lam-viec/render/video_vo_only.mp4`.

## Bàn giao
```
DOUYIN-20261005-01|Hoàn thành|v1|/workspace/video-jobs/DOUYIN-20261005-01/output/|done
```
