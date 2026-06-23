# Reflection — Lab 19

**Tên:** Hoàng Đức Dũng
**Cohort:** A20
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Dựa trên kết quả benchmark:
- **Keyword (BM25)** xử lý tốt nhất các câu truy vấn `exact` vì nó khớp chính xác từng từ vựng.
- **Semantic (Vector)** có khả năng hiểu ngữ nghĩa, nhưng **Hybrid** lại là phương pháp tối ưu nhất cho các câu `mixed` và có điểm trung bình tổng thể cao nhất. Thuật toán RRF giúp dung hòa ưu điểm của cả hai: vừa không bỏ lót keyword, vừa bắt được ngữ cảnh.

**KHÔNG nên dùng Hybrid khi:**
1. Hệ thống đòi hỏi độ trễ (latency) cực kỳ thấp và tiết kiệm tài nguyên. Hybrid phải chạy song song cả 2 bộ máy nên sẽ chậm và tốn RAM/CPU hơn.
2. Dữ liệu thuần túy là các mã định danh, ID, mã linh kiện (part numbers). Vector model thường không hiểu các mã này nên sẽ gây nhiễu, khi đó pure BM25 là lựa chọn đúng đắn duy nhất.

---

## Điều ngạc nhiên nhất khi làm lab này

Việc sử dụng Qdrant in-memory và FastAPI thực sự rất mượt mà và nhẹ nhàng, không cần setup Docker phức tạp mà vẫn đạt hiệu năng cực kỳ tốt.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
