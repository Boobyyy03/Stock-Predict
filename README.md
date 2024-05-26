# Dự Đoán Giá Cổ Phiếu sử dụng Mạng LSTM

## Mô Tả

Đây là một dự án nhằm dự đoán giá cổ phiếu của các mã FPT, PNJ, VIC, MSN sử dụng mạng LSTM (Long Short-Term Memory).

## Các Bước Thực Hiện

### 1. Tiền Xử Lý Dữ Liệu

- Đọc dữ liệu từ các tập tin CSV chứa thông tin về giá cổ phiếu của các mã FPT, PNJ, VIC, MSN.
- Chọn các cột cần thiết như 'Date/Time', 'Open', 'Close'.
- Lọc dữ liệu theo thời gian giao dịch từ 9h15 đến 14h46.
- Thêm cột ngày để dễ dàng nhóm dữ liệu theo ngày.
- Tạo DataFrame mới để lưu giá Open và Close cho mỗi ngày và mỗi Ticker.

### 2. Chuẩn Bị Dữ Liệu cho Mô Hình LSTM

- Chọn giá trị cần dự đoán là giá Close của cổ phiếu.
- Chuẩn hóa dữ liệu sử dụng MinMaxScaler để đưa dữ liệu về khoảng từ 0 đến 1.
- Tạo dữ liệu chuỗi thời gian cho mô hình LSTM, bao gồm các bước thời gian và giá Close tương ứng.

### 3. Xây Dựng và Huấn Luyện Mô Hình LSTM

- Sử dụng mô hình LSTM để dự đoán giá Close của cổ phiếu.
- Sử dụng Sequential API của TensorFlow để xây dựng mô hình.
- Chọn kiến trúc mạng LSTM với 2 lớp LSTM có 50 units mỗi lớp, kết hợp với các lớp Dense.
- Sử dụng optimizer Adam và hàm loss là mean squared error (MSE).
- Huấn luyện mô hình trên tập dữ liệu huấn luyện với số epochs là 50 và batch size là 1.

### 4. Dự Đoán và Vẽ Biểu Đồ

- Dự đoán giá trị trên tập dữ liệu huấn luyện và giá trị trong tương lai.
- Chuyển đổi dữ liệu dự đoán về dạng ban đầu để so sánh với dữ liệu thực tế.
- Vẽ biểu đồ cho mỗi loại cổ phiếu để so sánh giữa dữ liệu thực tế và dữ liệu dự đoán trong tương lai.

## Lý Do Chọn Mô Hình LSTM

- **Xử Lý Dữ Liệu Chuỗi Thời Gian:** LSTM là một loại mạng nơ-ron hồi tiếp (RNN) được thiết kế đặc biệt để xử lý dữ liệu chuỗi thời gian, phù hợp cho việc dự đoán giá cổ phiếu dựa trên dữ liệu lịch sử.
- **Khả Năng Ghi Nhớ Thời Gian Dài:** LSTM có khả năng ghi nhớ thông tin trong một khoảng thời gian dài, giúp mô hình hiểu được mối quan hệ giữa các giá trị trong quá khứ và giá trị hiện tại.
- **Tính Linh Hoạt:** LSTM có khả năng học và trích xuất đặc trưng phức tạp từ dữ liệu chuỗi thời gian, giúp cải thiện khả năng dự đoán của mô hình.
- **Độ Phức Tạp Cao:** Mô hình LSTM được chọn với kiến trúc phức tạp bao gồm nhiều lớp LSTM và các lớp kết nối đầy đủ (Dense), giúp mô hình có khả năng học được các mối quan hệ phức tạp trong dữ liệu.

## Cài Đặt

1. Clone repository này về máy của bạn.
2. Cài đặt các thư viện cần thiết:
    ```
    pip install pandas tensorflow
    ```
3. Chạy các script Python tương ứng với từng bước để thực hiện dự đoán giá cổ phiếu.

