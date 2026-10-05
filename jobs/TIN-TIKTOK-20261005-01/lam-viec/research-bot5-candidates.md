# TIN-TIKTOK-20261005-01 · Research nguồn TikTok cho video Tin AI (Bot5)

- **Job:** TIN-TIKTOK-20261005-01 · **Phiên bản:** v1 · **Ngày lập:** 05/10/2026 (giờ VN, UTC+7)
- **Brief:** video Tin AI, tham chiếu TikTok có view công khai >100k, ưu tiên 24–72h, khán giả là chủ DN / nhà sáng tạo. Không trùng các job cũ.
- **Cách kiểm chứng view:** đọc JSON `__UNIVERSAL_DATA_FOR_REHYDRATION__` (`webapp.video-detail` → `itemStruct.stats.playCount`, `createTime`) trên trang TikTok công khai bằng curl, **lúc 05/10/2026 15:51 UTC+7**. Danh sách ứng viên lấy bằng `yt-dlp --flat-playlist` trên trang profile của khoảng 80 tài khoản tin tức/AI; số liệu khớp với JSON trang video. Log thô và script nằm ở `lam-viec/evidence/` (`out_*.txt`, `ttuser.py`, `ttfull.py`; giờ trong log là **UTC**).
- **Lưu ý về view:** TikTok tự làm tròn số view từ 1 triệu trở lên (ví dụ 1.600.000). View còn tăng sau thời điểm kiểm.
- **Đã tránh trùng:** AlphaFold/Nobel (EDIT-FULL-01, SELFTRAIN), OpenAI dots + DevDay + GPT-6.1 Sol (TIN-02, EDIT-FULL-02), Gemini 4 Argon (TIN-02), OpenAI hủy GPT-6.1 Astra + hiệp ước Nhà Trắng + trát California (TIN-02, Kallaway job).
- **Bị chặn:** `yt-dlp --dump-json` cho từng video bị TikTok chặn theo IP của box ("Your IP address is blocked"), nhưng JSON trang video và listing profile vẫn đọc được. Lần đọc lại lúc 15:52 thì bị giới hạn tần suất (không có data), nên số view dưới đây là lần đọc lúc 15:51 UTC+7. Không cần browser cho 5 ứng viên này.

---

## ĐỀ XUẤT CHÍNH: Ứng viên 1, 60 Minutes: Daron Acemoglu (Nobel Kinh tế) nói "B.S." về chuyện "AI tạo ra ngành nghề mới bù cho số việc làm bị mất"

**Vì sao chọn:**
1. **Mới nhất:** đăng 05/10/2026 07:28 UTC+7, chưa tới 24h. Tập 60 Minutes phát sóng tối 04/10 (giờ Mỹ).
2. **View tăng nhanh:** 320.400 view sau khoảng 8 giờ. Tài khoản lớn (3,5 triệu follower), không phải quảng cáo, tương tác thật (21.600 like, 2.550 lượt lưu).
3. **Claim kiểm chứng được 100%:** câu trích có nguyên văn trong transcript chính thức của CBS, kèm bài báo CBS News.
4. **Hợp audience:** chủ DN và nhà sáng tạo đều quan tâm "AI thay người", "cắt giảm nhân sự nhờ AI agent". Hook mạnh ("Nobel nói thẳng: B.S."), dễ gây tranh luận. Có nhiều số liệu phụ (Pew, McKinsey, Clara Shih) giúp dựng nhiều đồ họa và animation.

**Phương án dự phòng mạnh:** Ứng viên 2 (McDonald's dùng AI định giá Big Mac). Clip này nhiều view hơn (473k) và sát chuyện kinh doanh nhất, nhưng đã đăng khoảng 6 ngày, ngoài khung 72h. Nếu bố ưu tiên tính ứng dụng cho chủ DN hơn độ mới thì chọn ứng viên 2.

---

## Danh sách ứng viên (đã kiểm view thật)

### 1. 60 Minutes: Acemoglu: "What you just described is B.S." (AI và việc làm) ⭐ ĐỀ XUẤT
- **URL:** https://www.tiktok.com/@60minutes/video/7692974037072416014
- **Tác giả:** @60minutes (60 Minutes, CBS) · 3,5 triệu follower · dài 88 giây
- **View đã thấy:** **320.400** · 21.600 like · 437 bình luận · 713 chia sẻ · 2.550 lưu (đọc JSON trang lúc 05/10/2026 15:51 UTC+7)
- **Đăng lúc:** 05/10/2026 07:28 UTC+7
- **Mô tả/claim chính (theo caption):** Nhà kinh tế đoạt Nobel Daron Acemoglu (MIT) bác ý kiến cho rằng nghề "huấn luyện AI" sẽ thành một ngành việc làm khổng lồ: *"The number of people they're employing in these positions is small relative to the number of people who will be replaced… That's the whole point of automation."* Ông lo **thất nghiệp có thể tăng gấp ba trong thập kỷ tới nếu không làm gì và cứ đi tiếp theo hướng hiện tại**.
- **Kiểm chứng:**
  - Transcript chính thức của CBS có nguyên văn câu "What you just described is B.S." và câu "small relative to…": https://www.cbsnews.com/news/will-ai-take-my-job-60-minutes-transcript/
  - Bài CBS News (Jon Wertheim, cập nhật 04/10/2026 22:26 EDT, tức 05/10 09:26 UTC+7): https://www.cbsnews.com/news/artificial-intelligence-trained-to-help-with-careers-60-minutes/. Bài ghi rõ đây là **kịch bản xấu nhất** ("In a worst-case scenario, unemployment could triple in the next decade, if nothing is done").
  - Số liệu phụ trong bài CBS (dùng được nếu ghi nguồn CBS): gần 3/4 người Mỹ sợ AI lấy việc (Pew). McKinsey Global Institute (báo cáo tháng 9) ước tính AI có thể buộc 11 triệu lao động Mỹ chuyển nghề trước 2035. Mercor có hơn 100.000 freelancer dạy AI, trả 20–200 USD/giờ. "AI trainer" là nhóm nghề tăng nhanh thứ 4 trên LinkedIn tại Mỹ. Clara Shih (từng điều hành mảng AI ở Salesforce và Meta) nói việc trước cần **hàng chục người** nay chỉ cần **1–3 người dùng AI agent**. Nghiên cứu Stanford cho thấy tuyển dụng người trẻ giảm ở nhóm nghề dễ bị AI thay (ví dụ lập trình viên).
- **Confidence:** CAO về việc ông có nói những câu này và về số view. TRUNG BÌNH về giá trị dự báo, vì đây là ý kiến và kịch bản, không phải sự thật đã xảy ra.
- **Caveat:**
  - "Thất nghiệp tăng gấp ba" là **dự báo kịch bản xấu nhất**, có điều kiện ("nếu không làm gì"). Trong transcript, câu này là lời dẫn của 60 Minutes, không phải câu Acemoglu nói nguyên văn trước camera. Không được trình bày như chắc chắn sẽ xảy ra.
  - Số liệu về Mỹ, **chưa có dữ liệu cho Việt Nam**.
  - Acemoglu cũng nói *không nên từ chối công nghệ*, và có thể làm nhiều việc như thiết kế AI để hỗ trợ con người hoặc dùng chính sách thuế khuyến khích tuyển người. Nên giữ ý cân bằng này.
  - Clip là nội dung của CBS: chỉ trích dẫn hoặc tham chiếu, không reup nguyên clip (bản quyền).

### 2. Reuters: McDonald's dùng AI định giá từng món ở từng cửa hàng (Big Mac chênh 21% chỉ cách 2 dặm)
- **URL:** https://www.tiktok.com/@reuters/video/7690906796042521870
- **Tác giả:** @reuters · 4,7 triệu follower · dài 92 giây
- **View đã thấy:** **473.400** · 37.200 like · 2.516 bình luận · 8.905 chia sẻ · 2.780 lưu (đọc JSON trang lúc 05/10/2026 15:51 UTC+7)
- **Đăng lúc:** 29/09/2026 17:46 UTC+7 (khoảng 6 ngày trước, **ngoài khung 72h**)
- **Claim chính:** McDonald's dùng AI để gợi ý giá menu tại Mỹ và một số thị trường. Công cụ ước tính "mức sẵn sàng chi trả" của khách từng khu vực, nhằm tăng lợi nhuận, nhưng có rủi ro làm khách khó chịu và bị soi về chống độc quyền.
- **Kiểm chứng:** bài độc quyền của Reuters ngày 29/09/2026 "Inside McDonald's push to have AI price your Big Mac": https://www.reuters.com/business/inside-mcdonalds-push-have-ai-price-your-big-mac-2026-09-29/. Đã đọc toàn văn qua bản đăng lại trên CNA (30/09/2026): https://www.channelnewsasia.com/business/us-mcdonalds-ai-pricing-franchisee-6419791. USA Today cũng đưa tin (30/09). Chi tiết chính:
  - Engine machine learning phân tích dữ liệu hàng triệu giao dịch mỗi ngày từ gần **14.000 nhà hàng** để đưa ra "giá tối ưu" cho từng món, ở từng điểm bán. Màn hình cho chủ cửa hàng hiển thị kiểu "MEDIUM SENSITIVITY to Price".
  - Ví dụ ở Fresno: Big Mac giá **5,69 USD** và **6,89 USD** tại hai cửa hàng cách nhau 2 dặm (đắt hơn 21%). **Reuters ghi rõ chưa xác nhận được chênh lệch này là do AI.**
  - 5 chủ nhượng quyền nói bị ép dùng công cụ. McDonald's nói đây là "a tool, not a mandate" và gọi bài báo là "speculative and uninformed".
  - Nền tảng do Tiger Analytics vận hành. McDonald's dùng một dạng công cụ định giá AI ít nhất từ 2019.
- **Confidence:** CAO (Reuters có ảnh chụp màn hình hệ thống và 9 nguồn tin, nhiều báo đăng lại).
- **Caveat:** đã khoảng 6 ngày. Chưa có thông tin McDonald's Việt Nam áp dụng. Phải giữ phản hồi phủ nhận của McDonald's và câu "chưa xác nhận chênh giá là do AI".

### 3. VTV24: Gần 96% học sinh 15 tuổi Việt Nam từng dùng chatbot AI để học (PISA 2025)
- **URL:** https://www.tiktok.com/@vtv24news/video/7692073370245991700
- **Tác giả:** @vtv24news (VTV24) · 9,2 triệu follower · dài 172 giây
- **View đã thấy:** **222.300** · 5.242 like · 2.783 chia sẻ · 244 lưu (đọc JSON trang lúc 05/10/2026 15:51 UTC+7)
- **Đăng lúc:** 03/10/2026 07:45 UTC+7 (khoảng 56 giờ trước, **trong khung 72h**)
- **Claim chính:** khảo sát hơn 7.300 học sinh 15 tuổi tại Việt Nam cho thấy gần 96% từng dùng chatbot AI để học. Dùng thiếu kiểm soát có thể ảnh hưởng khả năng tự học và tư duy.
- **Kiểm chứng:** báo cáo PISA 2025 của OECD công bố 08/09/2026. Thanh Niên (10/09/2026) ghi: 7.353 học sinh từ 194 trường, chỉ 4,1% hầu như hoặc chưa từng dùng, tức **95,9% có dùng, cao nhất trong 83 quốc gia/nền kinh tế**. Xếp sau là Singapore 95,6%, Thái Lan 95,5%. Thấp nhất là Nhật Bản 60,9%. Học sinh không dùng AI nhìn chung có điểm cao hơn, còn dùng vừa phải và có chủ đích "có thể có liên hệ tích cực". https://thanhnien.vn/gan-96-hoc-sinh-viet-dung-ai-ty-le-cao-nhat-the-gioi-185260910183700006.htm · Ghi chú quốc gia của OECD: https://www.oecd.org/en/publications/pisa-2025-results-volume-i-country-notes_2d4ff9ea-en/viet-nam_d652623e-en.html (chưa mở trực tiếp trang OECD; số liệu lấy qua Thanh Niên).
- **Confidence:** CAO (số liệu OECD, báo chính thống đăng lại).
- **Caveat:** dữ liệu gốc công bố từ 08/09, nghĩa là **clip mới nhưng dữ liệu đã gần 1 tháng**. Chủ đề giáo dục, hợp phụ huynh hơn là chủ DN. Clip bị tắt bình luận (0 comment).

### 4. CBS Mornings: Trường học "Alpha" không giáo viên, dạy bằng AI đầu tiên ở Chicago (học xong môn chính trong 2 giờ/ngày)
- **URL:** https://www.tiktok.com/@cbsmornings/video/7691350339085241630
- **Tác giả:** @cbsmornings · 4 triệu follower · dài 231 giây
- **View đã thấy:** **1.600.000** (TikTok làm tròn) · 105.300 like · 6.919 bình luận · 73.600 chia sẻ · 17.014 lưu (đọc JSON trang lúc 05/10/2026 15:51 UTC+7)
- **Đăng lúc:** 30/09/2026 22:28 UTC+7 (khoảng 4,7 ngày trước, **ngoài khung 72h**)
- **Claim chính:** trường Alpha (do AI dẫn dắt) khai trương ở Chicago tháng này giữa lúc dư luận phản đối AI. Trường nói học sinh nắm vững các môn chính chỉ trong 2 giờ mỗi ngày.
- **Kiểm chứng:** NBC Chicago (09/09/2026): Alpha Chicago khai giảng 08/09/2026, học phí **55.000 USD/năm**, từ mầm non tới lớp 8, người lớn được gọi là "guides" thay vì giáo viên. Hệ thống trường do MacKenzie Price lập năm 2014 tại Austin, có mặt ở ít nhất 15 bang khác. https://www.nbcchicago.com/news/local/first-ai-driven-teacher-free-school-in-chicago-opens-with-55000-annual-tuition/3986851/ · CBS News: https://www.cbsnews.com/video/teacherless-ai-driven-school-opens-in-chicago/
- **Confidence:** CAO về sự kiện. Câu "master in 2 hours" là **lời quảng cáo của trường**, chưa có bằng chứng độc lập.
- **Caveat:** view cao nhất nhóm nhưng chủ đề giáo dục, không phải tin AI "nóng". Trường mở từ 08/09, nên tin đã cũ khoảng 4 tuần.

### 5. Kallaway: "Google Gemini vừa tích hợp khả năng agentic vào Gemini Live" (QUẢNG CÁO)
- **URL:** https://www.tiktok.com/@kanekallaway/video/7690630566726618399
- **Tác giả:** @kanekallaway (Kallaway) · khoảng 445k follower · dài 119 giây
- **View đã thấy:** **3.600.000** (TikTok làm tròn) · **chỉ 1.507 like** · 56 bình luận · 63 chia sẻ (đọc JSON trang lúc 05/10/2026 15:51 UTC+7). JSON có `isAd: true`, kèm hashtag #googlepartner.
- **Đăng lúc:** 28/09/2026 23:54 UTC+7 (khoảng 6,7 ngày trước)
- **Claim chính:** Gemini Live đã có khả năng agentic (theo caption, chưa xem nội dung clip).
- **Kiểm chứng:** CHƯA XÁC MINH claim với nguồn chính thức của Google.
- **Confidence:** THẤP cho mục đích "video viral thật". Tỷ lệ like/view khoảng 0,04% cho thấy view chủ yếu đến từ **quảng cáo trả tiền**, không phải lan truyền tự nhiên.
- **Caveat:** nội dung tài trợ, không dùng làm bằng chứng "hot". Chỉ ghi lại để bố biết, **không đề xuất**.

---

## Đã xem nhưng loại (có view >100k nhưng không hợp hoặc trùng)
- @yahoofinance: OpenAI demo giọng nói bị lỗi ở DevDay, 101.500 view, 29/09 (https://www.tiktok.com/@yahoofinance/video/7691034629310041358). **Trùng chủ đề DevDay/dots** (TIN-02, EDIT-FULL-02).
- @dailymail: Musk đồng dẫn dắt Project Meridian của Lầu Năm Góc (chiến tranh tự động, drone, AI), 127.300 view, 01/10 (https://www.tiktok.com/@dailymail/video/7691657358728121614). Clip 12 giây, chủ đề quân sự, ít liên quan tới chủ DN.
- @cbsmornings: John Grisham "không cần AI", 277.700 view, 29/09. Chỉ là câu nói 14 giây, không có tin.
- @rileybrown.ai: dựng SaaS bằng Claude Code (Opus 5.5), 299.400 view, 27/09. Là tutorial, không phải tin, và đã cũ.
- @tommythings: ngành phim ngắn sẽ bị AI thay, 152.400 view, 02/10, tiếng Indonesia. Chỉ là ý kiến, không có claim kiểm chứng được.
- @newsweek: Trump nói dân sống gần trung tâm dữ liệu có thể nhận "cổ tức", 110.900 view, 30/09. Chính trị Mỹ.
- @adam.digital: dùng Runway biến ảnh sản phẩm 10 USD thành quảng cáo, 133.400 view, 26/09. Tutorial có kêu gọi comment, đã cũ.

---

## Tóm tắt một dòng
TIN-TIKTOK-20261005-01 | AI và việc làm: Nobel Kinh tế Daron Acemoglu (60 Minutes) gọi "B.S." luận điểm "AI tạo nghề mới bù việc mất" | Số người được thuê để huấn luyện AI rất nhỏ so với số người bị thay thế; kịch bản xấu nhất: thất nghiệp Mỹ có thể tăng gấp 3 trong 10 năm nếu không hành động | https://www.tiktok.com/@60minutes/video/7692974037072416014 (320.400 view lúc 05/10/2026 15:51 UTC+7) | 2026-10-05 07:28 UTC+7 (TikTok); tập phát sóng tối 04/10/2026 giờ Mỹ | Transcript CBS https://www.cbsnews.com/news/will-ai-take-my-job-60-minutes-transcript/ + bài CBS News https://www.cbsnews.com/news/artificial-intelligence-trained-to-help-with-careers-60-minutes/ + JSON trang TikTok | cao (trích dẫn, view) / trung bình (giá trị dự báo) | "Gấp 3" là kịch bản xấu nhất có điều kiện, lời dẫn của 60 Minutes chứ không phải nguyên văn của Acemoglu; số liệu Mỹ, chưa có dữ liệu VN; giữ ý "không chống công nghệ"; clip CBS chỉ trích dẫn, không reup; dự phòng: Reuters/McDonald's AI định giá (473.400 view, 29/09) | next=bố
