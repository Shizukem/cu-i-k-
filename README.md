# 🎯 AIDEOM-VN: Mô hình Ra Quyết định Phát triển Kinh tế Việt Nam trong Kỷ nguyên AI

## 📋 Giới thiệu

**AIDEOM-VN** (AI-Driven Economic Decision-making Model - Vietnam) là một hệ thống tích hợp 6 module để hỗ trợ ra quyết định chính sách phát triển kinh tế Việt Nam, với tập trung vào chuyển đổi số, trí tuệ nhân tạo, và phát triển bền vững.

**Mục đích**: Xây dựng Mô hình AIDEOM-VN
**Khóa học**: Các Mô hình Ra Quyết định - Viện Quản trị Kinh doanh, Đại học Kinh tế, ĐHQGHN

---

## 🏗️ Cấu trúc Hệ thống (6 Module)

| Module | Tên | Mô tả | Kỹ thuật |
|--------|-----|-------|---------|
| **M1** | Dự báo Kinh tế | Dự báo GDP 2026-2030 & Phân rã tăng trưởng | Cobb-Douglas + Growth Accounting |
| **M2** | Đánh giá Sẵn sàng Số | Xếp hạng 6 vùng theo mức độ sẵn sàng AI | TOPSIS + Entropy Weights |
| **M3** | Tối ưu Phân bổ | Phân bổ ngân sách theo ngành-vùng-thời gian | Linear Programming (LP) |
| **M4** | Mô phỏng Lao động | Tác động AI đến thị trường lao động | NetJob Analysis |
| **M5** | Đánh giá Rủi ro | Đánh giá rủi ro đa mục tiêu & ngẫu nhiên | Pareto + Stochastic Analysis |
| **M6** | Dashboard | Giao diện ra quyết định trực quan | Streamlit Dashboard |

---

## 📊 5 Kịch bản Chính sách

| Kịch bản | Mô tả | Phân bổ (K:D:AI:H) | Ưu tiên |
|----------|-------|-------------------|--------|
| **S1** | Truyền thống | 70:10:10:10 | Vốn vật chất, FDI, xuất khẩu |
| **S2** | Số hóa nhanh | 25:45:15:15 | Hạ tầng số, doanh nghiệp số |
| **S3** | AI dẫn dắt | 20:20:45:15 | AI, bán dẫn, dữ liệu lớn |
| **S4** | Bao trùm số | 30:20:10:40 | Nhân lực, vùng yếu, SME |
| **S5** | Tối ưu cân bằng | Tính toán từ mô hình | Kết hợp 4 mục tiêu |


## 📁 Cấu trúc Thư mục

```
aideom_vn/
├── dashboard_app.py          # Module M6 - Dashboard Streamlit (chính)
├── data_loader.py            # Tải & chuẩn bị dữ liệu
├── m1_forecast.py            # Module M1 - Dự báo
├── m2_readiness.py           # Module M2 - Đánh giá sẵn sàng
├── m3_allocation.py          # Module M3 - Tối ưu phân bổ
├── m4_labor.py               # Module M4 - Mô phỏng lao động
├── m5_risk.py                # Module M5 - Đánh giá rủi ro
├── test_modules.py           # Unit tests
├── requirements.txt          # Dependencies
├── README.md                 # File này
├── data/
│   ├── vietnam_macro_2020_2025.csv
│   ├── vietnam_sectors_2024.csv
│   └── vietnam_regions_2024.csv
└── outputs/
    ├── scenario_results/     # Kết quả các kịch bản
    └── visualizations/       # Biểu đồ & hình ảnh
```

## 💻 Sử dụng Dashboard

### Tab 1: 📊 Tổng quan
- Dữ liệu kinh tế cơ bản 2024-2025
- Xu hướng GDP lịch sử
- Sẵn sàng số theo vùng

### Tab 2: 💰 Phân bổ Ngân sách
- Chọn kịch bản xem chi tiết
- Biểu đồ tròn phân bổ
- Bảng phân bổ theo 6 vùng

### Tab 3: ⚖️ So sánh Kịch bản
- Dự báo GDP từng scenario
- Tác động thị trường lao động
- Đánh giá rủi ro tương đối

### Tab 4: ⚠️ Đánh giá Rủi ro
- Heatmap rủi ro đa chiều
- Phân tích cú sốc (Stochastic)
- Cảnh báo rủi ro cao

### Tab 5: 📈 Dự báo 2030
- Biểu đồ dự báo GDP lịch sử + forecast
- Phân rã tăng trưởng theo yếu tố
- Bảng chi tiết 5 năm (2026-2030)

---

## 📈 Sử dụng Module Độc lập

### Module 1: Dự báo Kinh tế

```python
from m1_forecast import EconomicForecast

m1 = EconomicForecast()

# Tính TFP lịch sử
hist = m1.calculate_tfp_historical()
print(hist[['year', 'GDP_trillion_VND', 'TFP_A']])

# Dự báo 2026-2030
forecast = m1.forecast_2026_2030()
print(forecast)

# Phân rã tăng trưởng
growth_acct = m1.growth_accounting()
print(growth_acct)
```

### Module 2: Đánh giá Sẵn sàng

```python
from m2_readiness import DigitalReadiness

m2 = DigitalReadiness()

# TOPSIS ranking
ranking = m2.topsis()
print(ranking.sort_values('TOPSIS_score', ascending=False))
```

### Module 3: Tối ưu Phân bổ

```python
from m3_allocation import BudgetAllocation

m3 = BudgetAllocation(total_budget=50000)

# Phân bổ theo scenario
scenario = {'K': 0.30, 'D': 0.20, 'AI': 0.10, 'H': 0.40}
allocation = m3.allocate_proportional(scenario)
```

### Module 4: Lao động

```python
from m4_labor import LaborMarketSimulation

m4 = LaborMarketSimulation()

# Tính NetJob
net_job = m4.calculate_net_job(x_AI=2500, x_H=2500)
print(net_job[['sector', 'net_job', 'net_job_ratio']])
```

### Module 5: Rủi ro

```python
from m5_risk import RiskAssessment

m5 = RiskAssessment()

# Đánh giá rủi ro scenario
risks = m5.evaluate_scenario_risks('S1', {'K': 0.7, 'D': 0.1, 'AI': 0.1, 'H': 0.1})
print(risks)

# Pareto tradeoffs
tradeoffs = m5.evaluate_pareto_tradeoffs({'K': 0.3, 'D': 0.2, 'AI': 0.2, 'H': 0.3})
print(tradeoffs)
```

## 📚 Tài liệu Tham khảo
### Văn bản Chính phủ Việt Nam
- Nghị quyết 57-NQ/TW: Phát triển KH&CN, đổi mới sáng tạo, chuyển đổi số (2024)
- Quyết định 749/QĐ-TTg: Chương trình Chuyển đổi số quốc gia (2020)
- Quyết định 127/QĐ-TTg: Chiến lược phát triển & ứng dụng AI (2021)
- Quyết định 411/QĐ-TTg: Chiến lược phát triển kinh tế - xã hội số (2022)

### Nguồn Dữ liệu
- Cục Thống kê Quốc gia (GSO): www.gso.gov.vn
- Bộ Khoa học & Công nghệ (MoST): www.most.gov.vn
- Ngân hàng Thế giới (World Bank): data.worldbank.org
- OECD: stats.oecd.org

### Tài liệu Học thuật
- Solow (1956): Growth Model
- Romer (1990): Endogenous Growth
- Deb et al. (2002): NSGA-II
- Hwang & Yoon (1981): TOPSIS
