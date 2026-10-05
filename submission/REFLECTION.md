# Reflection — Lab 19

**Tên:** Nguyễn Tiến Đạt  
**Cohort:** A20-K4  
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên tập đánh giá 50 queries, BM25 dẫn đầu ở nhóm truy vấn exact (96.7%) nhờ khả năng khớp từ khóa kỹ thuật chính xác mà không tốn chi phí suy luận ngữ nghĩa, trong khi Hybrid thắng tuyệt đối ở nhóm mixed (100% so với 97% của BM25 và 98.5% của Vector) nhờ cơ chế RRF kết hợp hài hòa giữa độ chuẩn xác từ vựng và ngữ cảnh semantic; riêng nhóm paraphrase vốn là thế mạnh tự nhiên của Vector search khi xử lý từ đồng nghĩa, dù ở bản thử nghiệm dùng bge-small-en Vector chỉ đạt 24.0% so với 33.3% của BM25 do rào cản ngôn ngữ, nhưng việc nâng cấp lên bge-m3 sẽ giúp ngữ nghĩa áp đảo hoàn toàn. Do đó, ta không nên lạm dụng Hybrid mà chỉ chọn pure BM25 khi tìm kiếm các định danh chính xác như mã lỗi, SKU sản phẩm, tên hàm API hoặc khi hệ thống yêu cầu độ trễ cực thấp và chi phí tối thiểu, ngược lại ưu tiên pure Vector cho các bài toán trừu tượng, tìm kiếm đa phương thức (cross-modal) hoặc truy vấn đa ngôn ngữ không có từ khóa cố định.

---

## Điều ngạc nhiên nhất khi làm lab này

Sự đơn giản nhưng hiệu quả bất ngờ của thuật toán RRF trong việc dung hòa hai thang điểm hoàn toàn khác nhau giữa BM25 và Vector Search mà không cần chuẩn hóa điểm số phức tạp.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
