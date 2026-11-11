# Prompt cho Lovable – Web mẫu tin nhắn gửi khách L-Shop Tour

Copy toàn bộ phần bên dưới đường kẻ và dán vào Lovable.

---

Tạo một web app một trang, giao diện tiếng Việt, tên **"L-Shop Tour – Mẫu gửi khách"**. Đây là công cụ nội bộ cho nhân viên công ty du lịch: chọn đúng mẫu thông tin rồi copy để gửi cho khách qua Zalo, Messenger, WhatsApp.

## Cách hoạt động
1. Trên cùng là các **nút bấm**, mỗi nút là một mẫu. Các nút được **chia nhóm theo tiêu đề nhóm** (ví dụ "Visa Anh", "Visa Trung Quốc", "Visa Mỹ").
2. Bấm một nút: nút đó được tô đậm (trạng thái đang chọn), và **phần bên dưới hiện ra nội dung mẫu đó**. Chỉ hiện một mẫu tại một thời điểm.
3. Bên trên khung nội dung có tên mẫu và một **nút "📋 Copy"** to, dễ bấm. Bấm vào thì copy **toàn bộ nội dung mẫu dưới dạng chữ thường (plain text)** vào clipboard, rồi nút đổi thành "✅ Đã copy!" trong 2 giây và hiện thông báo nhỏ (toast).
4. Có ô **tìm kiếm** phía trên các nút: gõ chữ (ví dụ "mỹ", "đức", "trung") thì chỉ hiện những nút có tên khớp. Tìm không phân biệt hoa thường, và tìm được cả khi gõ không dấu (ví dụ "my" khớp "Mỹ", "duc" khớp "Đức").
5. Khi chưa chọn mẫu nào thì hiện dòng hướng dẫn: "Chọn một mẫu ở trên để xem và copy".

## Yêu cầu quan trọng về nội dung
- Nội dung mẫu phải hiển thị và copy **giữ nguyên 100%**: giữ đúng từng chữ, emoji, dấu tiếng Việt, xuống dòng và khoảng trắng đầu dòng. Không tự sửa chữ, không render Markdown, không thêm hay bớt gì.
- Hiển thị nội dung trong khung có `white-space: pre-wrap`, font dễ đọc, cỡ chữ khoảng 15–16px.
- Lưu tất cả mẫu trong **một file dữ liệu riêng** (ví dụ `src/data/templates.ts`), dạng mảng `{ id, group, title, content }`, để sau này dễ thêm hoặc sửa mẫu. Thứ tự nhóm và thứ tự nút theo đúng thứ tự trong file.
- Không cần đăng nhập, không cần database, không cần backend.

## Giao diện
- Gọn, sạch, chuyên nghiệp, tông màu xanh dương/trắng.
- **Ưu tiên dùng tốt trên điện thoại**: các nút xuống hàng tự động, dễ bấm bằng ngón tay. Khi bấm một nút trên điện thoại thì tự cuộn xuống phần nội dung, và nút Copy luôn dễ thấy (có thể dính ở trên khung nội dung khi cuộn).
- Copy phải chạy được trên iPhone Safari và Android Chrome. Dùng `navigator.clipboard.writeText`, và nếu không được thì fallback bằng textarea ẩn + `document.execCommand('copy')`.

## Danh sách mẫu (giữ nguyên nội dung giữa các dòng ```text và ```)

### Mẫu 1
- group: Visa Anh
- title: Trẻ em đi với trường học
- content:

```text
📋 THÔNG TIN CẦN CUNG CẤP ĐỂ LÀM HỒ SƠ VISA ANH QUỐC
(Dành cho trẻ em đi Anh cùng trường học)

💶 GIÁ TRỌN GÓI: 400 EUR
Bao gồm: phí visa, lấy vân tay, dịch thuật giấy tờ, làm hồ sơ.

━━━━━━━━━━━━━━━━━━━━

🛂 1. HỘ CHIẾU VÀ THẺ CƯ TRÚ
Của em bé, của bố và của mẹ:
- Chụp trang hộ chiếu có thông tin cá nhân
- Chụp thẻ cư trú (cả mặt trước và mặt sau)

🏠 2. ĐỊA CHỈ NHÀ
- Địa chỉ hiện tại (số nhà, đường, thành phố):
- Đã sống ở địa chỉ này bao lâu:
- Nhà bố mẹ sở hữu hay đi thuê:
- Có thẻ cư trú dài hạn (trvalý pobyt) từ khi nào:

💳 3. NGƯỜI CHI TRẢ CHI PHÍ CHUYẾN ĐI
- Họ tên:
- Ngày sinh:
- Địa chỉ:
- Mối quan hệ với em bé:

👨‍👩‍👧‍👦 4. THÔNG TIN BỐ MẸ (bắt buộc)
Bố:
- Họ tên:
- Ngày sinh:
- Quốc tịch:
Mẹ:
- Họ tên:
- Ngày sinh:
- Quốc tịch:

✈️ 5. LỊCH SỬ DU LỊCH TRONG 5 NĂM QUA
- Nếu đã đi các nước sau, vui lòng ghi rõ tháng, năm và đi bao lâu (ưu tiên, có lợi cho hồ sơ): Úc, Canada, New Zealand, Mỹ, Thụy Sỹ, các nước châu Âu.
- Các nước khác (nếu có): ghi cụ thể tháng, năm đã đi.

❌ 6. VISA ANH
- Em bé đã bao giờ bị từ chối visa Anh chưa? Nếu có, ghi rõ:

🏫 7. THÔNG TIN CHUYẾN ĐI VỚI TRƯỜNG
- Lịch trình chuyến đi: gửi link trang web hoặc giấy đăng ký tour với trường

━━━━━━━━━━━━━━━━━━━━

📄 HỒ SƠ CẦN SCAN / CHỤP GỬI
☐ Hộ chiếu – của em bé và của bố/mẹ (người đứng tên giấy ngân hàng)
☐ Thẻ cư trú – của em bé và của bố/mẹ (người đứng tên giấy ngân hàng)
☐ Sao kê ngân hàng hoặc xác nhận số dư của bố/mẹ
   👉 Tốt nhất xin ngân hàng hoặc tải online bản tiếng Anh để khỏi phải dịch – gọi là "potvrzení o zůstatku v angličtině"
☐ Lịch trình chuyến đi với trường
☐ Giấy khai sinh của em bé
```

### Mẫu 2
- group: Visa Trung Quốc
- title: Khách tự đi
- content:

```text
📌 THÔNG TIN CẦN CUNG CẤP ĐỂ LÀM VISA TRUNG QUỐC 🇨🇳

━━━━━━━━━━━━━━━━━━━━

📄 1. THÔNG TIN CÁ NHÂN
- Số điện thoại:
- Chụp trang hộ chiếu có ảnh
- Chụp thẻ cư trú dài hạn (trvalý pobyt) cả 2 mặt
- Ảnh chân dung tự chụp: nền trắng, không đeo kính, không đội mũ

💼 2. THÔNG TIN VIỆC LÀM
- Công việc hiện tại:
- Số điện thoại nơi làm việc:
👉 Hoặc chỉ cần gửi số IČO là được

🏡 3. THÔNG TIN GIA ĐÌNH
- Tình trạng hôn nhân:
Vợ/chồng:
- Họ tên:
- Ngày sinh:
- Nơi sinh:
- Quốc tịch:
Con cái (mỗi con):
- Họ tên:
- Ngày sinh:
- Quốc tịch:
Bố mẹ (cần cả khi khách đã là người lớn):
- Họ tên bố, ngày sinh:
- Họ tên mẹ, ngày sinh:

✈️ 4. THÔNG TIN CHUYẾN ĐI
- Ngày dự kiến đi:
- Ngày quay lại:
- Bay từ đâu:
- Đến thành phố nào ở Trung Quốc:
- Về từ thành phố nào:

🇨🇳 5. ĐÃ TỪNG ĐẾN TRUNG QUỐC CHƯA?
- Nếu đã có visa Trung Quốc: gửi ảnh visa Trung Quốc gần nhất
- Nếu đã đến Trung Quốc: cho thông tin chuyến đi gần nhất

🌍 6. CÁC NƯỚC ĐÃ DU LỊCH TRONG 5 NĂM GẦN ĐÂY
- Chỉ cần kể tên các nước:
```

### Mẫu 3
- group: Visa Trung Quốc
- title: Đi tour L-Shop Tour
- content:

```text
📌 THÔNG TIN CẦN CUNG CẤP ĐỂ LÀM VISA TRUNG QUỐC – ĐI TOUR L-SHOP TOUR 🇨🇳

━━━━━━━━━━━━━━━━━━━━

📄 1. THÔNG TIN CÁ NHÂN
- Số điện thoại:
- Chụp trang hộ chiếu có ảnh
- Chụp thẻ cư trú dài hạn (trvalý pobyt) cả 2 mặt
- Ảnh chân dung tự chụp: nền trắng, không đeo kính, không đội mũ

💼 2. THÔNG TIN VIỆC LÀM
- Công việc hiện tại:
- Số điện thoại nơi làm việc:
👉 Hoặc chỉ cần gửi số IČO là được

🏡 3. THÔNG TIN GIA ĐÌNH
- Tình trạng hôn nhân:
Vợ/chồng:
- Họ tên:
- Ngày sinh:
- Nơi sinh:
- Quốc tịch:
Con cái (mỗi con):
- Họ tên:
- Ngày sinh:
- Quốc tịch:
Bố mẹ (cần cả khi khách đã là người lớn):
- Họ tên bố, ngày sinh:
- Họ tên mẹ, ngày sinh:

🇨🇳 4. ĐÃ TỪNG ĐẾN TRUNG QUỐC CHƯA?
- Nếu đã có visa Trung Quốc: gửi ảnh visa Trung Quốc gần nhất
- Nếu đã đến Trung Quốc: cho thông tin chuyến đi gần nhất

🌍 5. CÁC NƯỚC ĐÃ DU LỊCH TRONG 5 NĂM GẦN ĐÂY
- Chỉ cần kể tên các nước:
```

### Mẫu 4
- group: Visa Mỹ
- title: Sống tại Séc – đi tour L-Shop Tour
- content:

```text
📌 THÔNG TIN LÀM VISA MỸ – ĐI TOUR L-SHOP TOUR 🇺🇸
(Dành cho khách sống tại Séc)

Đầu tiên, mình cần nộp hồ sơ online để lấy lịch hẹn phỏng vấn. Để làm việc này, anh/chị chuẩn bị giúp L-Shop Tour các thông tin sau:

━━━━━━━━━━━━━━━━━━━━

📄 1. ẢNH CHỤP
- Trang hộ chiếu có ảnh
- Thẻ cư trú (cả 2 mặt)
- Ảnh chân dung tự chụp:
   • Đứng trước tường nền trắng
   • Không đội mũ, không đeo kính
   • Nhìn rõ cả 2 vai (ảnh visa là ảnh vuông, công ty sẽ tự cắt)

🏠 2. THÔNG TIN LIÊN LẠC
- Địa chỉ nhà:
- Số điện thoại:
- Email:

🇺🇸 3. LỊCH SỬ VISA MỸ
- Đã từng đi Mỹ chưa?
- Đã từng xin visa Mỹ chưa?
- Đã từng được cấp visa Mỹ chưa?
👉 Nếu đã được cấp: ghi rõ ngày/tháng/năm cấp và chụp visa cũ (có số visa)

🗽 4. NGƯỜI THÂN TẠI MỸ
- Có người thân đang sống ở Mỹ hoặc là công dân Mỹ không?
- Nếu có, ghi rõ quan hệ:

💍 5. TÌNH TRẠNG HÔN NHÂN
- Tình trạng hôn nhân:
Vợ/chồng (nếu có):
- Họ tên:
- Ngày sinh:
- Nơi sinh:
- Quốc tịch (nếu là quốc tịch EU, ghi rõ nước nào):

💼 6. CÔNG VIỆC / THU NHẬP
Công việc hiện tại:
- Tên công ty:
- Địa chỉ công ty:
- Số điện thoại công ty:
- Chức vụ:
- Nhiệm vụ chính:
- Làm từ tháng/năm nào:
👉 Nếu không đi làm nhưng có nguồn thu nhập khác (ví dụ cho thuê cửa hàng, cho thuê nhà...) cũng ghi rõ.

Công việc trước đó:
- Tên công ty:
- Địa chỉ:
- Số điện thoại:
- Chức vụ:
- Làm từ năm nào đến năm nào:

🎓 7. HỌC VẤN
Ghi trường học cuối cùng, kể cả học ở Việt Nam, kể cả trung học:
- Tên trường:
- Học từ năm nào đến năm nào:

👨‍👩‍👧‍👦 8. BỐ MẸ (cần cả khi khách đã là người lớn)
- Họ tên bố, ngày sinh:
- Họ tên mẹ, ngày sinh:

🌍 9. CÁC NƯỚC ĐÃ DU LỊCH TRONG 5 NĂM GẦN ĐÂY
- Ghi càng nhiều càng tốt:

🗣️ 10. NGÔN NGỮ
- Anh/chị nói được những ngôn ngữ nào?
```

### Mẫu 5
- group: Visa Mỹ
- title: Sống tại Đức – đi tour L-Shop Tour
- content:

```text
📌 THÔNG TIN LÀM VISA MỸ – ĐI TOUR L-SHOP TOUR 🇺🇸
(Dành cho khách sống tại Đức)

Đầu tiên, mình cần nộp hồ sơ online để lấy lịch hẹn phỏng vấn. Để làm việc này, anh/chị chuẩn bị giúp L-Shop Tour các thông tin sau:

━━━━━━━━━━━━━━━━━━━━

📄 1. ẢNH CHỤP
- Trang hộ chiếu có ảnh
- Thẻ Ausweis (cả 2 mặt)
- Ảnh chân dung tự chụp:
   • Đứng trước tường nền trắng
   • Không đội mũ, không đeo kính
   • Nhìn rõ cả 2 vai (ảnh visa là ảnh vuông, công ty sẽ tự cắt)

🏠 2. THÔNG TIN LIÊN LẠC
- Địa chỉ nhà:
- Số điện thoại:
- Email:

🇺🇸 3. LỊCH SỬ VISA MỸ
- Đã từng đi Mỹ chưa?
- Đã từng xin visa Mỹ chưa?
- Đã từng được cấp visa Mỹ chưa?
👉 Nếu đã được cấp: ghi rõ ngày/tháng/năm cấp và chụp visa cũ (có số visa)

🗽 4. NGƯỜI THÂN TẠI MỸ
- Có người thân đang sống ở Mỹ hoặc là công dân Mỹ không?
- Nếu có, ghi rõ quan hệ:

💍 5. TÌNH TRẠNG HÔN NHÂN
- Tình trạng hôn nhân:
Vợ/chồng (nếu có):
- Họ tên:
- Ngày sinh:
- Nơi sinh:
- Quốc tịch (nếu là quốc tịch EU, ghi rõ nước nào):

💼 6. CÔNG VIỆC / THU NHẬP
Công việc hiện tại:
- Tên công ty:
- Địa chỉ công ty:
- Số điện thoại công ty:
- Chức vụ:
- Nhiệm vụ chính:
- Làm từ tháng/năm nào:
👉 Nếu không đi làm nhưng có nguồn thu nhập khác (ví dụ cho thuê cửa hàng, cho thuê nhà...) cũng ghi rõ.

Công việc trước đó:
- Tên công ty:
- Địa chỉ:
- Số điện thoại:
- Chức vụ:
- Làm từ năm nào đến năm nào:

🎓 7. HỌC VẤN
Ghi trường học cuối cùng, kể cả học ở Việt Nam, kể cả trung học:
- Tên trường:
- Học từ năm nào đến năm nào:

👨‍👩‍👧‍👦 8. BỐ MẸ (cần cả khi khách đã là người lớn)
- Họ tên bố, ngày sinh:
- Họ tên mẹ, ngày sinh:

🌍 9. CÁC NƯỚC ĐÃ DU LỊCH TRONG 5 NĂM GẦN ĐÂY
- Ghi càng nhiều càng tốt:

🗣️ 10. NGÔN NGỮ
- Anh/chị nói được những ngôn ngữ nào?
```
