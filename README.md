# 📍 WiFi Indoor Localization using Machine Learning

## 📖 Giới thiệu Dự án
Dự án Khai phá dữ liệu (Data Mining) áp dụng các thuật toán Học máy có giám sát và không giám sát để dự đoán vị trí thiết bị trong không gian kín (Indoor Positioning). Dựa trên dữ liệu cường độ tín hiệu mạng (RSSI) thu thập từ 7 Router WiFi khác nhau, mô hình có thể phân lớp chính xác thiết bị đang nằm ở căn phòng nào trong 4 căn phòng cho trước.

## 📊 Tập dữ liệu (Dataset)
*   **Nguồn:** D08 - WiFi Localization Dataset.
*   **Kích thước:** 2000 mẫu dữ liệu (tương ứng với 4 căn phòng, mỗi phòng ~500 mẫu).
*   **Đặc trưng (Features):** 7 biến liên tục đại diện cho cường độ tín hiệu (RSSI) đo bằng thiết bị di động.
*   **Nhãn (Target):** Biến phân loại (Categorical) từ 1 đến 4, đại diện cho 4 căn phòng. Tập dữ liệu cân bằng tuyệt đối.

## 🛠 Công nghệ & Thư viện sử dụng
*   **Ngôn ngữ:** Python 3.1x
*   **Môi trường:** Jupyter Notebook (Visual Studio Code)
*   **Thư viện xử lý & Trực quan hóa:** `pandas`, `numpy`, `matplotlib`, `seaborn`
*   **Thư viện Học máy:** `scikit-learn` (PCA, KNN, Random Forest, SVM, K-Means, DBSCAN)

## 🚀 Pipeline Phân tích & Kết quả
Dự án được triển khai qua 4 giai đoạn cốt lõi:

### 1. Exploratory Data Analysis (EDA)
Đọc dữ liệu, kiểm tra cấu trúc định dạng và trích xuất các thông số thống kê mô tả cơ bản (Min, Max, Mean) để đánh giá độ nhiễu của tín hiệu.

### 2. Giảm chiều dữ liệu (Dimensionality Reduction)
Sử dụng **PCA (Principal Component Analysis)** để nén dữ liệu từ không gian 7 chiều (7 Routers) xuống 2 chiều (2D). Kết quả trực quan hóa cho thấy các điểm dữ liệu tụ thành 4 cụm tương đối rõ ràng, minh chứng cho tính khả thi của việc dùng Học máy để phân loại.

### 3. Phân lớp (Classification)
Tiến hành chuẩn hóa dữ liệu (StandardScaler) và sử dụng `GridSearchCV` kết hợp `10-Fold Cross Validation` để tinh chỉnh tham số cho 3 mô hình học máy. 
🏆 **Kết quả F-Score (Macro):**
*   **K-Nearest Neighbors (KNN):** `98.75%` (Best parameters: `n_neighbors=3`, `weights='uniform'`) - *Mô hình tối ưu nhất*
*   **Support Vector Machine (SVM):** `98.35%` 
*   **Random Forest:** `98.30%` 

### 4. Gom cụm (Clustering)
Thử nghiệm các thuật toán học máy không giám sát để nhóm các tín hiệu WiFi tự động mà không cần nhãn.
*   **K-Means (k=4):** Hoạt động hiệu quả với điểm Adjusted Rand Index (ARI) đạt **~0.81**, cho thấy sự tương đồng cao với nhãn thực tế.
*   **DBSCAN:** Thất bại trong việc gom cụm với cấu hình mật độ mặc định do dải tín hiệu phân bố không đều, chứng minh K-Means ổn định hơn đối với cấu trúc dữ liệu này.

## ⚙️ Hướng dẫn cài đặt & Cấu hình
1. Clone repository này về máy:
   ```bash
   git clone [https://github.com/Tên-Tài-Khoản-Của-Bạn/wifi-indoor-localization.git](https://github.com/Tên-Tài-Khoản-Của-Bạn/wifi-indoor-localization.git)
