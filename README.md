[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573979&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.huyhk@vinuni.edu.vn
**Name:** Huỳnh Khải Huy
**Student ID:** 2A202600082

---

## Mo ta

Bài lab này xây dựng một ETL pipeline hoàn chỉnh bao gồm 4 bước: Extract dữ liệu từ file JSON,
Validate để loại bỏ các bản ghi không hợp lệ (giá <= 0, category rỗng), Transform để chuẩn hoá
dữ liệu (Title Case category, tính discounted_price giảm 10%, thêm timestamp processed_at),
và Load kết quả ra file CSV. Ngoài ra, bài làm còn có phần Stress Test so sánh kết quả của
AI Agent khi chạy với clean data và garbage data nhằm chứng minh tầm quan trọng của chất lượng dữ liệu.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Tao Garbage Data
```bash
python generate_garbage.py
```

### Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```

### Chay Tests
```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline (3 records hop le)
├── garbage_data.csv         # Du lieu "doc" dung cho stress test
├── agent_simulation.py      # Gia lap AI Agent voi clean/garbage data
├── generate_garbage.py      # Script tao file du lieu chat luong kem
├── experiment_report.md     # Bao cao thi nghiem so sanh clean vs garbage
└── README.md                # File nay
```

---

## Ket qua

- **Tong records trong raw_data.json:** 5
- **Records hop le sau validation:** 3 (loại bỏ 2: giá âm và category rỗng)
- **Records da luu vao processed_data.csv:** 3
- **Cot bo sung:** `discounted_price` (giảm 10%) va `processed_at` (timestamp)
- **Stress Test:** Agent cho kết quả chính xác với clean data; trả lời sai với garbage data do extreme outlier va sai kiểu dữ liệu
