# QA report — TIN-TIKTOK-20261005-02 (v1) · Bot 2 — Tin AI

- **Voice:** OmniVoice · male clone v2 locked · 1.2 · voice_locked:true
  - /health: status=ok voice_mode=clone voice_locked=True ref=`voice-lock-vn-v2.wav` speed=1.2 (post) seed=1234
  - 16/16 câu TTS qua `/tts` với header `X-Voice-Locked: true` + `X-Voice-Clone: voice-lock-vn-v2.wav` (log: qa/pipeline.log); loudnorm 2-pass −14 LUFS/TP −1.5
- **Engine:** HyperFrames 0.8.114 (headless Chrome, GSAP) — composition tay theo bảng cảnh 11 shot (`lam-viec/hf/index.html`, generator `lam-viec/custom/gen_hf.py` + `style.css`), F01 neon UI; FFmpeg chỉ dùng mux/720p.
- **Render lock:** TTS và render đều chạy trong `flock /workspace/video-jobs/.render.lock`.
- **VO text:** đúng nguyên văn `lam-viec/storytelling_script.txt` (script QA v1 PASS, giữ "nhảm nhí"); 245 âm tiết (đếm theo từ), 16 câu.

## File
| File | Thông số |
|---|---|
| output/storytelling_final.mp4 | h264 1080x1920 30/1 yuv420p High · aac 48000Hz ch=2 54.026s · 54.033s · 17.88 MB (18750170 B) · -14.8 LUFS / TP -4.3 dBFS |
| output/storytelling_mobile_720p.mp4 | h264 720x1280 30/1 yuv420p High · aac 48000Hz ch=2 54.026s · 54.033s · 5.44 MB |
| output/voice_storytelling.wav | VO-only, 53.576s, -14.8 LUFS / TP -1.5 dBFS, 48 kHz mono |
| output/subtitle.srt | 44 cue, 0.00–53.46s |
| output/storytelling_script.txt, output/script.md | VO duyệt + script v1 kèm bảng cảnh 9 cảnh |

## Self-QA
- ffprobe: 1080×1920 ✓ · 720×1280 ✓ · H.264 yuv420p + AAC ✓ · video 54.033s = VO 53.58s + 0.45s đuôi.
- SRT: thứ tự/thời gian không chồng lấn = True; chữ SRT trùng 100% VO = True; cue cuối kết thúc 53.46s vs VO 53.58s; 16/16 đầu câu khớp đầu cue (±0.25s). Align WhisperX: 245 từ, 0 nội suy, 245 lấy từ faster-whisper fallback.
- Nghe lại (faster-whisper small int8, ASR proxy): độ giống kịch bản **0.625**. Khác biệt ASR (phần lớn là cách nghe tên riêng/tiếng Anh, không phải đọc sai):
  - replace: "đoạt" → "đoàn"
  - delete: "hình" → ""
  - replace: "daron acemoglu" → "donald asimoglu"
  - replace: "bác" → "bát"
  - replace: "của ông rất" → "đồn dất"
  - replace: "clara shih" → "claricy"
  - replace: "mảng" → "mạng"
  - replace: "chục người giờ" → "hàng"
  - replace: "cần" → "cầm"
  - replace: "ba" → "3"
  - replace: "ai agent" → "aiagent"
  - replace: "sixty" → "60"
  - replace: "xấu" → "sấu"
  - replace: "ba" → "3"
  - replace: "mười" → "10"
  - replace: "báo không phải chắc chắn mckinsey ước tính khoảng mười một triệu lao động mỹ có thể phải chuyển nghề trước năm hai nghìn không trăm ba mươi lăm nhưng acemoglu không chống công nghệ ông cho rằng có thể thiết kế ai để hỗ trợ con người kèm chính sách khuyến khích tuyển người đây là số liệu mỹ việt nam chưa có con số tương đương nhưng câu hỏi thì giống nhau dùng ai để thay người hay để mỗi người làm giỏi hơn chủ doanh nghiệp hay nhà sáng tạo bạn chọn hướng nào bình luận cho hinton media biết nhé" → "b"
- Không BGM: track audio = VO + 46 SFX one-shot ngắn (≤0.9s, theo cột "Âm thanh" của bảng cảnh: {'hit': 11, 'bleep': 1, 'whoosh': 11, 'click': 6, 'pop': 13, 'scan': 4}), gain −6 dB, không có nhạc nền. Khoảng lặng giữa câu trong VO-only: mean -91.0…-91.0 dB.
- Không burn karaoke/caption (chỉ chữ khoá kinetic theo bảng cảnh); SRT sidecar.
- Khung hình: qa/contact_sheet.jpg (9 cảnh, 70% mỗi cảnh) + qa/frames/; chữ nằm trong vùng an toàn x 60–940, y 150–1590 (SO-TAY-DUNG §3.1).
- Hiệu ứng đã dựng: TV neon + huy chương Nobel xoay + glitch RGB-split + sóng âm, `“B.S.”` slam 180→100% + shake + flash + thanh bleep quét + SFX bleep sau chữ "nhảm nhí" (S1); profile card slide/blur-in + typewriter `DARON ACEMOGLU` + gõ câu luận điểm + stamp `?` đỏ + cán cân lắc (S2); listicle 01–03 pop-in; bar chart cột "người bị thay" mọc vượt khung + shake, trích kinetic từng cụm (S3); lưới 30 icon người co theo hàng còn 3 + AI agent pulse + chữ morph (S4); đường biểu đồ vẽ dần (minh hoạ, không trục số), `×3` zoom punch + nháy đỏ, nhãn điều kiện, sticker `CẢNH BÁO ≠ CHẮC CHẮN` stamp (S5); dot-map Mỹ ripple + counter 0→11.000.000 + lower-third nguồn wipe (S6); split NGƯỜI/AI trượt lại, `VS` xoay biến thành `+`, tick chính sách (S7); badge `SỐ LIỆU MỸ` stamp, ngã rẽ THAY/NÂNG NGƯỜI nháy luân phiên (S8); câu hỏi từng từ + poll 2 nút pulse + logo + bubble bình luận (S9). Flash/zoom chuyển cảnh; progress bar.
- Cảnh (s): [(0.0, 4.45), (4.45, 10.48), (10.47, 17.36), (17.36, 23.96), (23.96, 31.18), (31.18, 36.97), (36.97, 42.99), (42.99, 49.46), (49.46, 54.03)]

## Ghi chú / lệch spec
- Không có template `frame-*` trên box → dựng tay bằng HyperFrames theo motion trong bảng cảnh 9 cảnh (dùng lại generator/CSS job 01, viết cảnh mới).
- Không dùng mặt/footage/logo CBS: Acemoglu = thẻ hồ sơ silhouette có nhãn "Ảnh minh hoạ"; Clara Shih = thẻ chữ (không ảnh). Biểu đồ thất nghiệp ghi "Minh hoạ · không theo trục số thật". Không thêm trích dẫn ngoài script/research.
- "B.S." chỉ trên màn hình + thanh bleep; VO "nhảm nhí" giữ nguyên (theo QA bố). SFX bleep (sine 1 kHz 0.28s, nhỏ) đặt ngay sau chữ "nhí", không che lời.
- Caveat có đủ trên màn: `KỊCH BẢN XẤU NHẤT · NẾU KHÔNG LÀM GÌ`, sticker `CẢNH BÁO ≠ CHẮC CHẮN`, "Theo 60 Minutes (CBS)"; `SỐ LIỆU MỸ` + "VN: chưa có số tương đương"; cảnh 7 không chống công nghệ.
- SFX one-shot giống job 01 (gain −6 dB, không nhạc nền). Bản không SFX cùng hình: `lam-viec/render/video_vo_only.mp4`.
- ASR small toàn file chỉ 0.625 vì faster-whisper small dừng/cụt sau ~30s (lỗi ASR, transcript bị cắt ở "Đó là cảnh b…"). Nghe lại bằng faster-whisper **medium** theo 3 cửa sổ dài (0–15.7s, 15.5–31.2s, 31–54s): khớp gần như toàn bộ kịch bản; chỉ khác tên riêng (Darren Asimoglu, Claracy) và số viết thành chữ số. Chỗ duy nhất đáng nghe lại: ~0.6s "đoạt giải" (medium chỉ nghe "đ… giải"). Transcript theo câu: `lam-viec/custom/asr_medium.txt` (clip ngắn không ngữ cảnh nên kém tin cậy hơn).
- Align: WhisperX gãy timing cả 16 câu (tên Latin) → fallback faster-whisper word timestamps 245/245 từ khớp.
- JOB.md: giữ "Đang sản xuất" trong lúc render; chuyển "Đang kiểm tra" sau khi deliverables đã nằm trong output/.

## Bàn giao
```
TIN-TIKTOK-20261005-02|Đang kiểm tra|v1|/workspace/video-jobs/TIN-TIKTOK-20261005-02/output|next=bố
```
