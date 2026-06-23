# Reflection — Lab 19

**Tên:** _<Họ Tên>_
**Cohort:** _<A20-K1 / A20-K2 / ...>_
**Path đã chạy:** _<lite | docker | both>_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries, hybrid RRF thắng trung bình với Precision@10 là
78.6%, cao hơn BM25 (77.8%) và semantic vector search (73.2%). Với query
`exact`, BM25 và hybrid cùng đạt 96.7% vì các thuật ngữ xuất hiện trực tiếp
trong corpus. Với `mixed`, hybrid thắng rõ nhất (100.0% so với 97.0% BM25 và
98.5% semantic) vì RRF kết hợp được cả keyword chính xác lẫn tín hiệu ngữ
nghĩa. Trên `paraphrase`, cả ba mode đều yếu; BM25 đạt 33.3%, hybrid 32.0% và
semantic 24.0%. Điều này cho thấy model `bge-small-en-v1.5` chưa phù hợp tối
ưu cho paraphrase tiếng Việt.

Tôi không dùng hybrid khi cần lookup thuật ngữ chính xác, latency tối thiểu,
hoặc hệ thống có ngân sách compute hạn chế: BM25 là đủ. Ngược lại, pure vector
phù hợp khi corpus và query cùng ngôn ngữ, nhiều paraphrase, và embedding model
multilingual đã được đánh giá tốt.

---

## Điều ngạc nhiên nhất khi làm lab này

_(Optional, 1–2 câu)_

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
