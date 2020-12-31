# Đồ án cuối kì Khoa học dữ liệu và Ứng dụng
Đề tài: Phân tích thị trường tiền ảo - Cryptocurrency Market Analysis

## Thông tin nhóm:
- Lê Thanh Hiếu - 1712434
- Phạm Minh Thắng - 1712759

## 1. Câu hỏi được đặt ra là gì?
- Đồng tiền nào có giá trị/giá trị thị trường lớn nhất?
- Tương quan giá top 10 đồng tiền ảo
- Xu hướng về khối lượng giao dịch cho top các đồng tiền ảo
- Xem xét về thị phần phân chia giữa top 10 đồng tiền ảo hàng đầu
- Tương quan giữa các thuộc tính với mỗi đòng tiền
- Đồng tiền nào dễ biến động hơn và đồng nào ổn định hơn?
- Biến động giá cả của các loại tiền ảo tương quan với nhau như thế nào?
- Xu hướng theo mùa (seasonal trend) trong biến động giá trông như thế nào?
- Dự đoán giá bitcoin trong tương lai. (Áp dụng học máy)

## 2. Nếu trả lời được câu hỏi thì có ý nghĩa gì?
- Giúp tìm hiểu các xu hướng trong thị trường tiền ảo
- Dự đoán giá bitcoin để người dùng có thêm thông tin tham khảo khi ra quyết định đầu tư vào tiền ảo.

## 3. Cách thức thu nhập dữ liệu như thế nào? (từ đâu, parse HTML hay API, tham khảo từ đâu,...)
- Toàn bộ dữ liệu được thu thập từ trang [Coinmarketcap](https://coinmarketcap.com).
- Việc thu thập dữ liệu được thực hiện bằng cách parse HTML với thư viện Selenium (do trang web có sử dụng JavaScript với cơ chế lazy loading).
- Nhóm tiến hành crawl dữ liệu danh sách các đồng tiền trước và lưu vào file **coin_list.csv**.
- Sau khi đã có được danh sách các đồng tiền điện tử, nhóm tiến hành thu thập lịch sử thay đổi giá của các đồng tiền trên.Lịch sử được thu thập từ ngày đầu tiên coin có mặt trên thị trường đến ngày 16/12/2020.

## 4. Tổng quan dữ liệu thu nhập được có bao nhiêu dòng, cột và cột cần dự đoán là gì.
- coin_list.csv có có kích thước là (3694, 10)
- Tập dữ liệu top 10 đồng coin có giá trị thị trường lớn nhất có kích thước là (17308, 8)

## 5. Với mỗi cột dữ liệu thu nhập có ý nghĩa gì, kiểu dữ liệu và ví dụ.
Các thông tin thu thập được từ danh sách đồng tiền bao gồm:
- **name**: Tên đầy đủ của coin.
- **symbol**: Ký hiệu của coin.
- **price**: Giá trị của coin tại thời điểm thu thập dữ liệu.
- **24h**: Sự thay đổi giá so với 24 giờ/7 ngày trước.
- **7d**: Giá trị vốn hoá thị trường (USD).
- **market_cap**: Khối lượng giao dịch trong vòng 24h (theo USD và theo loại coin tương ứng).
- **volume** (coin): Tổng lượng coin đang được lưu thông trên thị trường.
- URL dẫn đến trang cung cấp thông tin chi tiết từng loại coin.  

Các thông tin về giá từng loại coin bao gồm tập dữ liệu chứa các thuộc tính sau:
- **Date**: Ngày quan sát dữ liệu
- **Open**: Giá mở cửa của ngày được cho
- **High**: Giá cao nhất trong ngày được cho
- **Low**: Giá thấp nhất trong ngày được cho
- **Close**: Giá đóng cửa của ngày đựơc cho
- **Volume**: Khối lượng giao dịch trong ngày được cho
- **Market Cap**: Vốn hóa thị trường tính bằng USD

## 6. Tự đánh giá đồ án (kết quả, thiếu sót, cần làm gì phát triển thêm,..).
- Kết quả: Nhóm hoàn thành phần lớn các yêu cầu của đồ án đề ra.
- Thiếu sót: một số câu hỏi chưa được nhóm trả lời một cách rõ ràng, tường minh (ví dụ: xu hướng theo mùa trong biến động giá như thế nào?, ...).
- Cần làm gì để phát triển thêm:
    - Các dữ liệu có thể cho ra được nhiều thông tin hơn nữa nếu được khai thác hợp lý. Do đó nên thực hiện khai phá dữ liệu chi tiết hơn.
    - Mặc dù khó có thể dự đoán chính xác sự thay đổi giá, nhóm cho rằng vẫn có thể cải thiện mô hình tốt hơn (với tham số khác, với đặc trưng, mô hình khác, ...)

## 7. Phân công công việc.
- Hiếu: readme, EDA, viết báo cáo.
- Thắng: Crawl data, áp dụng machine learning, viết báo cáo.

## 8. Hướng dẫn chạy các file notebook (tất cả các quy trình, cả code thu nhập dữ liệu)
- OS: Ubuntu 20.04
- Chạy file **Data_Crawling.ipynb** để tiến hành crawl dữ liệu
- Chạy file **Cryptocurrency_Market_Analysis.ipynb** để tiến hành các bước EDA, áp dụng mô hình học máy