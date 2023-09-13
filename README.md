# House Price Crawling
## Giới thiệu đề bài
Tạo một Dataset về nhà bán ở tại TP.HCM, Dataset phải có ít nhất trên 20.000 mẫu dữ liệu trong khoảng 12 tháng gần nhất.
## Mô tả chương trình
Chương trình được viết bằng ngôn ngữ Python, có sử dụng thư viện **Selenium** kết hợp với **Undetected ChromeDriver** nhằm vượt qua Cloudflare của website Batdongsan.com.vn. Về cơ bản, đầu tiên, chương trình sẽ vào từng trang danh sách hiển thị của web, tại đó nó sẽ crawl đường dẫn đi kèm các tin đăng bán nhà và lưu vào file URLs_data.csv. Thường sẽ có 20 tin trên 1 trang danh sách. Sau đó, dựa trên những đường dẫn có trong URLs_data.csv, chương trình crawl sẽ tiến hành truy cập vào từng trang đăng bán nhà cụ thể để thu thập các thông tin chi tiết về ngôi nhà đang bán và lưu chúng thành một dòng trong file dataset.csv.

Lưu ý: Crawl thủ công nên tốn rất nhiều thời gian, nên cân nhắc trước khi áp dụng vào dữ liệu có quy mô lớn.
## Về Dataset kết quả
URLs_data.csv: Chứa các đường dẫn đến trang thông tin chi tiết của từng mẫu tin đăng bán nhà.

dataset.csv: Dataset sau cùng, gồm 20.499 mẫu, với 23 trường thông tin, trong khoảng từ ngày 12 tháng 6 đến ngày 2 tháng 7 về các nhà bán ở tại TP.HCM như nhà riêng, nhà biệt thự, nhà mặt phố, shophouse, nhà phố thương mại.
## Một số lỗi có thể xảy ra
1/ Gặp lỗi tương tự như ví dụ bên dưới. Để xử lý lỗi này có 2 cách, một là downgrade Google Chrome xuống phiên bản mà Undetected ChromeDriver hỗ trợ, hai là upgrade Undetected ChromeDriver lên cùng phiên bản với Google Chrome. Ở cách thứ hai, tồn tại tình huống đã update Undetected ChromeDriver nhưng lỗi vẫn hiện như cũ, điều này là do trong máy vẫn còn tồn tại "undetected_chromedriver.exe" phiên bản cũ, ví dụ: "C:\Users\ADMIN\AppData\Roaming\undetected_chromedriver\undetected_chromedriver.exe" cho hệ máy Window. Do đó, phải tìm và xóa file này, cập nhật thủ công file mới, thì mới hết báo lỗi.


"Message: unknown error: *cannot connect to chrome at* 127.0.0.1:64848

from session not created: *This version of ChromeDriver only supports Chrome version* 109

*Current browser version is* 114.0.5735.134"


3/ Crawl dữ liệu suốt một tuần, lấy được khoảng 15.000 mẫu hay hơn thì gặp tình trạng chương trình bị đứng, đơ không thể làm gì. Nguyên nhân có thể là vì mẫu tin đang crawl bị lỗi, hết hiệu lực nên bị người đăng bán nhà xóa, rút lại do đã bán thành công ngôi nhà hoặc gặp liên tiếp 2 mẫu tin bị lỗi, khiến chương trình cứ tải lại mẫu tin thay thế.
