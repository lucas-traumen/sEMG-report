# Quy tắc agent cho tài liệu LaTeX

## Bối cảnh

Repository chứa luận văn kỹ thuật tiếng Việt về hệ thống thu nhận và xử lý sEMG một kênh dùng ADS1292R và STM32, hướng tới nhận diện hoạt động cơ và xu hướng mỏi cơ. Đây chỉ là bối cảnh, không phải bằng chứng khoa học.

## Phạm vi làm việc

- Làm đúng yêu cầu hiện tại; không tự mở rộng phạm vi.
- Trước khi sửa, đọc `main.tex`, chương liên quan, `references.bib` và các file trực tiếp cần thiết.
- Giữ cấu trúc, thuật ngữ, citation style và quy ước LaTeX hiện có.
- Không sửa firmware, hardware, code phân tích hoặc dataset nếu người dùng không yêu cầu.
- Nếu tác vụ chỉ yêu cầu review, không chỉnh sửa file.

## Nguồn và trích dẫn

- Không bịa paper, tác giả, DOI, URL, số trang, số liệu, citation key hoặc nội dung datasheet.
- Chỉ trích dẫn nguồn đã được mở và kiểm tra có hỗ trợ đúng khẳng định.
- Search snippet, metadata, tên file và tóm tắt AI chỉ dùng để tìm nguồn, không phải bằng chứng.
- Kiểm tra citation key tồn tại trong `references.bib` trước khi sử dụng.
- Chỉ thêm bibliography từ metadata đã xác minh và giữ style hiện có.
- Khẳng định kỹ thuật, sinh lý, y sinh, số liệu và so sánh phải có nguồn, trừ kết quả hoặc quyết định thiết kế của dự án.
- Công thức lấy từ tài liệu phải có citation; định nghĩa đủ ký hiệu, đơn vị và giả thiết.
- Kết quả của dự án phải truy được về dataset, script, bảng, hình, log hoặc thí nghiệm tương ứng.
- Nếu thiếu bằng chứng, nêu rõ nguồn còn thiếu; chỉ chèn `% TODO(source): ...` khi người dùng cho phép bản nháp chưa hoàn chỉnh.

Ưu tiên nguồn: tài liệu người dùng cung cấp → nguồn đã có trong `references.bib` → tài liệu chính thức/tiêu chuẩn → nghiên cứu bình duyệt → web khác khi được phép.

## GitNexus và mã nguồn

- Dùng GitNexus để tìm module, symbol, dependency và luồng thực thi.
- Xác minh thông tin cuối cùng bằng mã nguồn thuộc revision hiện tại.
- Phân biệt rõ nội dung **đã triển khai**, **dự kiến** và **suy luận**.
- Chỉ nêu function, file, ngoại vi, thanh ghi, tần số lấy mẫu hoặc data flow sau khi kiểm tra.
- Nếu không truy cập được repository/revision cần thiết, nêu giới hạn thay vì đoán.

## Văn phong học thuật

- Viết tiếng Việt học thuật, chính xác, có liên kết logic; tránh văn nói, cường điệu và kết luận vượt bằng chứng.
- Giải thích từ viết tắt ở lần đầu và dùng thuật ngữ nhất quán.
- Phân biệt quan sát, mối liên hệ, suy luận và quan hệ nhân quả.
- Không coi sEMG là phép đo trực tiếp mỏi chủ quan; phân biệt performance fatigability, perceived fatigability và chỉ dấu điện sinh lý gián tiếp.
- Ưu tiên đoạn văn; chỉ dùng danh sách cho liệt kê, yêu cầu, quy trình hoặc so sánh thực sự phù hợp.
- Không lặp nội dung giữa các chương nếu có thể dùng tham chiếu chéo.

## Quy ước LaTeX

- Giữ document class, preamble, bibliography backend, citation command, glossary và định dạng hiện có.
- Không thêm package hoặc thay đổi font, lề, giãn dòng nếu chưa cần thiết hoặc chưa được yêu cầu.
- Dùng command LaTeX mang ngữ nghĩa; không căn chỉnh thủ công bằng khoảng trắng hay xuống dòng lặp lại.
- Mọi đối tượng được tham chiếu phải có `\label{}` mô tả rõ; dùng `\ref`/`\eqref`, không ghi cứng số.
- Mỗi hình và bảng phải có caption, được giới thiệu và diễn giải trong nội dung.
- Giữ Unicode tiếng Việt với XeLaTeX và escape ký tự đặc biệt.
- Không đổi tên label, citation key, file hoặc command nếu chưa cập nhật toàn bộ tham chiếu.
- Không reflow hoặc format lại nội dung không liên quan.

## Quy trình và kiểm tra

1. Xác định deliverable, vị trí chỉnh sửa và nguồn được phép dùng.
2. Kiểm tra cấu trúc và thuật ngữ hiện có; với mục lớn, chốt dàn ý trước khi viết.
3. Thực hiện thay đổi nhỏ nhất nhưng hoàn chỉnh; giữ nguyên nội dung không liên quan.
4. Kiểm tra citation, label, cross-reference, công thức, đơn vị, caption và thuật ngữ.
5. Dùng lệnh build của repository; nếu chưa có, chạy:

```bash
latexmk -xelatex -interaction=nonstopmode -file-line-error main.tex
```

6. Xác nhận không có lỗi, undefined citation/reference, duplicate label hoặc bibliography failure.
7. Đánh giá warning ảnh hưởng tới font, citation hoặc bố cục; báo các `overfull/underfull box` đáng kể.
8. Xem diff và báo file đã sửa, kết quả build cùng khoảng trống bằng chứng còn lại.

## An toàn và hoàn thành

- Không xóa, ghi đè, đổi tên hoặc format hàng loạt nội dung không liên quan.
- Không loại bỏ thay đổi sẵn có trong working tree.
- Không commit, push, tạo branch hoặc sửa tài nguyên remote nếu chưa được yêu cầu.
- Không thêm auxiliary build files vào Git trừ khi repository chủ ý theo dõi.
- Tác vụ hoàn thành khi nội dung đúng vị trí, nguồn hợp lệ, dự án build thành công và diff chỉ chứa thay đổi liên quan.
