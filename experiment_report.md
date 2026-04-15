# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600082
**Name:** Huỳnh Khải Huy
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Pipeline đã loại bỏ các bản ghi không hợp lệ; chỉ còn lại các sản phẩm điện tử hợp lệ |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Bản ghi outlier với giá cực cao làm lệch kết quả; agent đưa ra gợi ý vô lý |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi dùng Garbage Data, agent chọn sản phẩm có giá cao nhất trong danh mục electronics.
Do dữ liệu không qua bước validation và transformation, các bản ghi chất lượng kém vẫn tồn tại trong dataset.
Cụ thể, bản ghi "Nuclear Reactor" với giá $999,999 là một extreme outlier — giá trị này phi thực tế nhưng vẫn được agent tin tưởng.
Ngoài ra, garbage data còn chứa nhiều vấn đề khác: Duplicate IDs làm mất tính nhất quán, trường price kiểu sai ("ten dollars") gây lỗi khi agent xử lý số liệu, và giá trị null trong category làm agent không thể phân loại sản phẩm đúng.
Tất cả những vấn đề này chứng minh rằng chất lượng dữ liệu đầu vào ảnh hưởng trực tiếp đến chất lượng câu trả lời của AI Agent. Dù prompt có tốt đến đâu, nếu dữ liệu bẩn thì kết quả cũng không chính xác.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Dữ liệu chất lượng cao là nền tảng bắt buộc cho bất kỳ hệ thống AI nào. Một pipeline ETL với validation chắc chắn sẽ loại bỏ các bản ghi lỗi trước khi chúng ảnh hưởng đến agent. Prompt tốt có thể giúp agent hiểu yêu cầu hơn, nhưng nếu knowledge base chứa dữ liệu sai, agent vẫn sẽ đưa ra kết quả sai. Do đó, trong thực tế, đảm bảo chất lượng dữ liệu phải là ưu tiên hàng đầu.
