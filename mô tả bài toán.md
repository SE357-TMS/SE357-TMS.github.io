# HỆ THỐNG QUẢN LÝ DU LỊCH

## 1. Giới thiệu chung

Hệ thống quản lý du lịch (Tourist Management System - TMS) giúp công ty du lịch quản lý các tuyến du lịch, chuyến đi, đặt tour và theo dõi khách hàng một cách hiệu quả. Hệ thống hỗ trợ khách hàng dễ dàng tìm kiếm, đặt tour du lịch phù hợp với nhu cầu, đồng thời giúp nhân viên quản lý các nghiệp vụ đặt chỗ, thanh toán và theo dõi lịch trình chuyến đi.

Công ty du lịch Sài Gòn quản lý hàng trăm tuyến du lịch với hàng ngàn chuyến đi mỗi năm, phục vụ cho khách hàng trong và ngoài nước. Các công việc chính mà công ty cần quản lý là: quản lý tuyến du lịch, quản lý chuyến đi, quản lý đặt tour, quản lý khách hàng, quản lý thanh toán, thống kê báo cáo, và xử lý các trường hợp khách hàng vi phạm điều khoản đặt tour. Công ty hoạt động suốt cả năm, thường xuyên cập nhật tuyến du lịch mới, điều chỉnh giá tour theo mùa, và bảo trì thông tin chuyến đi.

## 2. Quản lý Tuyến du lịch và Điểm tham quan

Nhân viên gọi tuyến du lịch là **Route** (tuyến), mỗi tuyến du lịch thuộc về một hoặc nhiều **Category** (danh mục) du lịch (chẳng hạn như du lịch biển, du lịch núi, du lịch văn hóa, du lịch sinh thái, du lịch khám phá thành phố...). Mỗi tuyến du lịch bao gồm nhiều **Attraction** (điểm tham quan), mỗi điểm tham quan có mã số để phân biệt, tên điểm tham quan, mô tả chi tiết, vị trí địa lý.

Mỗi tuyến du lịch có thông tin về:

- Tên tuyến (name)
- Điểm xuất phát (start_location)
- Điểm kết thúc (end_location)
- Số ngày của tuyến (duration_days)
- Hình ảnh minh họa (image)
- Trạng thái (status: OPEN, ONGOING, CLOSED)

Thông tin về mối quan hệ giữa tuyến và điểm tham quan được lưu trong **Route_Attraction**, bao gồm:

- Ngày thăm quan (day)
- Thứ tự trong ngày (order_in_day)
- Mô tả hoạt động tại điểm đó (activity_description)

Mỗi điểm tham quan thuộc về một Category, có trạng thái (ACTIVE, INACTIVE, DELETED) để quản lý việc hiển thị và sử dụng.

## 3. Quản lý Chuyến đi (Trip)

Mỗi tuyến du lịch có thể có nhiều **Trip** (chuyến đi) với các ngày khởi hành khác nhau. Mỗi chuyến đi được phân biệt bằng mã chuyến duy nhất và có các thông tin:

- Ngày khởi hành (departure_date)
- Ngày trở về (return_date)
- Giá tour (price)
- Tổng số chỗ (total_seats)
- Số chỗ đã đặt (booked_seats)
- Thời gian và địa điểm đón (pick_up_time, pick_up_location)
- Trạng thái (status: SCHEDULED, ONGOING, FINISHED, CANCELED)

Mỗi chuyến đi có số lượng chỗ giới hạn. Hệ thống cần theo dõi số chỗ đã đặt để đảm bảo không vượt quá số chỗ tối đa.

## 4. Quản lý Người dùng

Để sử dụng hệ thống, mỗi người dùng (**User**) phải đăng ký tài khoản và cung cấp các thông tin:

- Tên đăng nhập (username) - duy nhất
- Mật khẩu (password)
- Họ tên đầy đủ (full_name)
- Email (email) - duy nhất
- Số điện thoại (phone_number)
- Địa chỉ (address)
- Ngày sinh (birthday)
- Giới tính (gender: M, F, O)
- Vai trò (role: CUSTOMER, STAFF, ADMIN)

Hệ thống có ba loại người dùng:

- **CUSTOMER** (Khách hàng): Có thể xem tour, đặt tour, quản lý đặt chỗ cá nhân, yêu thích tour
- **STAFF** (Nhân viên): Quản lý tuyến, chuyến đi, xử lý đặt chỗ, xem báo cáo
- **ADMIN** (Quản trị viên): Toàn quyền quản lý hệ thống, quản lý người dùng, cấu hình hệ thống

Tài khoản người dùng có thể bị khóa (is_lock) nếu vi phạm điều khoản sử dụng.

## 5. Quản lý Giỏ hàng và Yêu thích

### 5.1. Giỏ hàng (Cart)

Mỗi khách hàng có một giỏ hàng (**Cart**) để lưu trữ tạm thời các chuyến đi muốn đặt. Mỗi mục trong giỏ hàng (**Cart_Item**) bao gồm:

- Chuyến đi (trip_id)
- Số lượng chỗ (quantity)
- Giá tại thời điểm thêm vào giỏ (price)

Khách hàng có thể:

- Thêm chuyến đi vào giỏ hàng
- Chỉnh sửa số lượng chỗ
- Xóa chuyến đi khỏi giỏ hàng
- Thanh toán toàn bộ giỏ hàng để tạo đặt chỗ

### 5.2. Danh sách yêu thích (Favorite_Tour)

Khách hàng có thể đánh dấu các tuyến du lịch yêu thích (**Favorite_Tour**) để dễ dàng truy cập sau này. Mỗi bản ghi lưu:

- Người dùng (user_id)
- Tuyến du lịch (route_id)
- Thời gian đánh dấu (có thể mở rộng)

## 6. Quản lý Đặt tour

### 6.1. Quy trình đặt tour

Khi khách hàng muốn đặt tour, có hai cách:

1. **Đặt trực tiếp**: Chọn chuyến đi và đặt ngay
2. **Đặt qua giỏ hàng**: Thêm nhiều chuyến vào giỏ, sau đó thanh toán một lần

Mỗi lần đặt tour tạo ra một **Tour_Booking** (đặt chỗ) với các thông tin:

- Chuyến đi (trip_id)
- Khách hàng (user_id)
- Số chỗ đặt (seats_booked)
- Tổng tiền (total_price)
- Trạng thái (status: PENDING, CONFIRMED, CANCELED, COMPLETED)

### 6.2. Chi tiết đặt chỗ

Mỗi đặt chỗ có thông tin chi tiết trong **Tour_Booking_Detail**:

- Số người lớn (no_adults)
- Số trẻ em (no_children)

Thông tin hành khách được lưu trong **Booking_Traveler**:

- Họ tên (full_name)
- Giới tính (gender)
- Ngày sinh (date_of_birth)
- Giấy tờ tùy thân (identity_doc)

### 6.3. Hóa đơn và Thanh toán

Mỗi đặt chỗ tạo ra một **Invoice** (hóa đơn) với:

- Tổng tiền (total_amount)
- Trạng thái thanh toán (payment_status: UNPAID, PAID, REFUNDED)
- Phương thức thanh toán (payment_method)

Quy định thanh toán:

- Khách hàng phải thanh toán trước ít nhất 30% để xác nhận đặt chỗ
- Thanh toán đầy đủ trước 7 ngày khởi hành
- Nếu quá hạn thanh toán, đặt chỗ sẽ tự động hủy
- Hoàn tiền khi hủy tour:
  - Hủy trước 15 ngày: hoàn 80%
  - Hủy trước 7 ngày: hoàn 50%
  - Hủy trước 3 ngày: hoàn 20%
  - Hủy trong vòng 3 ngày: không hoàn tiền

## 7. Nghiệp vụ hàng ngày

### 7.1. Nghiệp vụ Đăng ký và Đăng nhập

**Đăng ký tài khoản:**
Khách hàng mới truy cập vào hệ thống cần đăng ký tài khoản bằng cách:

- Nhập thông tin cá nhân: username (duy nhất), password, full_name, email (duy nhất), phone_number, address, birthday, gender
- Hệ thống kiểm tra tính hợp lệ: username và email chưa tồn tại trong hệ thống
- Mật khẩu phải đủ mạnh (ít nhất 8 ký tự, có chữ hoa, chữ thường, số)
- Sau khi đăng ký thành công, hệ thống tự động gán role là CUSTOMER
- Gửi email xác nhận đăng ký

**Đăng nhập:**

- Người dùng nhập username/email và password
- Hệ thống xác thực thông tin
- Kiểm tra tài khoản có bị khóa (is_lock = true) không
- Nếu tài khoản bị khóa, hiển thị lý do và không cho phép đăng nhập
- Nếu hợp lệ, tạo phiên đăng nhập và chuyển đến trang tương ứng với vai trò

### 7.2. Nghiệp vụ Tìm kiếm và Lọc tour

**Xem danh sách tuyến du lịch:**

- Hệ thống hiển thị tất cả tuyến có status = OPEN
- Mỗi tuyến hiển thị: tên, hình ảnh, điểm xuất phát, điểm kết thúc, số ngày, giá khởi điểm
- Khách hàng có thể thấy icon yêu thích (nếu đã đăng nhập)

**Tìm kiếm tour:**
Khách hàng nhập các tiêu chí tìm kiếm:

- Từ khóa (tìm trong tên tuyến, tên điểm tham quan)
- Điểm xuất phát, điểm kết thúc
- Khoảng ngày khởi hành (từ ngày - đến ngày)
- Khoảng giá (từ - đến)
- Số ngày (duration_days)
- Danh mục (Category)

Hệ thống truy vấn:

```sql
SELECT DISTINCT r.* FROM Route r
JOIN Route_Attraction ra ON r.id = ra.route_id
JOIN Attraction a ON ra.attraction_id = a.id
JOIN Trip t ON t.route_id = r.id
WHERE r.status = 'OPEN'
AND (r.name LIKE '%keyword%' OR a.name LIKE '%keyword%')
AND r.start_location = 'location' (nếu có)
AND t.departure_date BETWEEN 'start_date' AND 'end_date'
AND t.price BETWEEN min_price AND max_price
ORDER BY ...
```

**Lọc và Sắp xếp:**

- Lọc theo category_id
- Lọc theo số ngày (= hoặc khoảng)
- Sắp xếp theo: giá tăng/giảm, số ngày, mới nhất, phổ biến nhất (dựa vào số lượng booking)

**Xem chi tiết tuyến:**
Khi khách hàng click vào một tuyến, hệ thống hiển thị:

- Thông tin tuyến: name, start_location, end_location, duration_days, image
- Lịch trình chi tiết theo từng ngày:
  ```sql
  SELECT ra.day, ra.order_in_day, a.name, a.description, a.location, ra.activity_description
  FROM Route_Attraction ra
  JOIN Attraction a ON ra.attraction_id = a.id
  WHERE ra.route_id = :route_id
  ORDER BY ra.day, ra.order_in_day
  ```
- Danh sách các chuyến đi sắp tới (Trip):
  ```sql
  SELECT * FROM Trip
  WHERE route_id = :route_id
  AND status IN ('SCHEDULED', 'ONGOING')
  AND departure_date >= CURRENT_DATE
  ORDER BY departure_date
  ```
- Hiển thị cho mỗi chuyến: ngày khởi hành, ngày về, giá, số chỗ còn trống (total_seats - booked_seats)

### 7.3. Nghiệp vụ Quản lý Yêu thích

**Đánh dấu yêu thích (Toggle Favorite):**

- Khách hàng click vào icon trái tim trên tuyến du lịch
- Hệ thống kiểm tra người dùng đã đăng nhập chưa (nếu chưa → chuyển đến trang đăng nhập)
- Kiểm tra trong bảng Favorite_Tour:
  ```sql
  SELECT * FROM Favorite_Tour
  WHERE user_id = :user_id AND route_id = :route_id
  ```
- Nếu đã tồn tại → XÓA (bỏ yêu thích):
  ```sql
  DELETE FROM Favorite_Tour
  WHERE user_id = :user_id AND route_id = :route_id
  ```
- Nếu chưa tồn tại → THÊM (đánh dấu yêu thích):
  ```sql
  INSERT INTO Favorite_Tour (user_id, route_id)
  VALUES (:user_id, :route_id)
  ```
- Cập nhật giao diện ngay lập tức (đổi màu icon)

**Xem danh sách yêu thích:**

- Khách hàng vào mục "Yêu thích" trong tài khoản
- Hệ thống hiển thị danh sách tuyến đã đánh dấu yêu thích:
  ```sql
  SELECT r.* FROM Route r
  JOIN Favorite_Tour ft ON r.id = ft.route_id
  WHERE ft.user_id = :user_id AND r.status = 'OPEN'
  ```
- Khách hàng có thể lọc theo giá, địa điểm, ngày
- Có thể bỏ yêu thích trực tiếp từ danh sách này

### 7.4. Nghiệp vụ Quản lý Giỏ hàng

**Thêm chuyến vào giỏ:**

- Khách hàng chọn một chuyến đi và click "Thêm vào giỏ"
- Hệ thống kiểm tra người dùng đã đăng nhập chưa
- Lấy hoặc tạo Cart cho user:
  ```sql
  SELECT * FROM Cart WHERE user_id = :user_id
  -- Nếu chưa có:
  INSERT INTO Cart (user_id) VALUES (:user_id)
  ```
- Kiểm tra chuyến đã có trong giỏ chưa:
  ```sql
  SELECT * FROM Cart_Item
  WHERE cart_id = :cart_id AND trip_id = :trip_id
  ```
- Nếu đã có → Cập nhật số lượng:
  ```sql
  UPDATE Cart_Item
  SET quantity = quantity + :quantity, price = :current_price
  WHERE cart_id = :cart_id AND trip_id = :trip_id
  ```
- Nếu chưa có → Thêm mới:
  ```sql
  INSERT INTO Cart_Item (cart_id, trip_id, quantity, price)
  VALUES (:cart_id, :trip_id, :quantity, :current_price)
  ```
- Kiểm tra số chỗ còn trống:
  ```sql
  SELECT (total_seats - booked_seats) as available
  FROM Trip WHERE id = :trip_id
  ```
- Nếu quantity > available → Báo lỗi "Không đủ chỗ"

**Xem giỏ hàng:**

- Hiển thị danh sách các Cart_Item:
  ```sql
  SELECT ci.*, t.*, r.name as route_name
  FROM Cart_Item ci
  JOIN Trip t ON ci.trip_id = t.id
  JOIN Route r ON t.route_id = r.id
  WHERE ci.cart_id = :cart_id
  ```
- Hiển thị: tên tuyến, ngày khởi hành, số lượng, giá, tổng tiền từng item
- Tổng tiền toàn bộ giỏ: SUM(ci.quantity \* ci.price)

**Chỉnh sửa số lượng:**

- Khách hàng thay đổi số lượng chỗ trong giỏ
- Kiểm tra số chỗ còn trống
- Cập nhật:
  ```sql
  UPDATE Cart_Item
  SET quantity = :new_quantity
  WHERE id = :item_id
  ```
- Cập nhật lại tổng tiền

**Xóa khỏi giỏ:**

- Khách hàng click "Xóa" trên một item
- Xác nhận: "Bạn có chắc muốn xóa chuyến này khỏi giỏ?"
- Nếu đồng ý:
  ```sql
  DELETE FROM Cart_Item WHERE id = :item_id
  ```

### 7.5. Nghiệp vụ Đặt tour

**Đặt tour trực tiếp (không qua giỏ):**
Khách hàng click "Đặt ngay" trên một chuyến:

1. Kiểm tra đăng nhập
2. Hiển thị form nhập thông tin:
   - Số người lớn (no_adults)
   - Số trẻ em (no_children)
   - Thông tin từng hành khách (full_name, gender, date_of_birth, identity_doc)
3. Kiểm tra số chỗ còn trống >= (no_adults + no_children)
4. Tạo booking:
   ```sql
   INSERT INTO Tour_Booking (trip_id, user_id, seats_booked, total_price, status)
   VALUES (:trip_id, :user_id, :total_seats, :total_price, 'PENDING')
   ```
5. Tạo booking detail:
   ```sql
   INSERT INTO Tour_Booking_Detail (booking_id, no_adults, no_children)
   VALUES (:booking_id, :no_adults, :no_children)
   ```
6. Thêm thông tin hành khách:
   ```sql
   INSERT INTO Booking_Traveler (booking_id, full_name, gender, date_of_birth, identity_doc)
   VALUES (:booking_id, ...) -- Lặp cho từng hành khách
   ```
7. Cập nhật số chỗ đã đặt:
   ```sql
   UPDATE Trip
   SET booked_seats = booked_seats + :seats_booked
   WHERE id = :trip_id
   ```
8. Tạo hóa đơn:
   ```sql
   INSERT INTO Invoice (booking_id, total_amount, payment_status, payment_method)
   VALUES (:booking_id, :total_price, 'UNPAID', NULL)
   ```
9. Gửi email xác nhận với thông tin đặt chỗ và hướng dẫn thanh toán

**Đặt tour qua giỏ hàng (Checkout):**
Khách hàng click "Thanh toán" trong giỏ:

1. Kiểm tra giỏ có ít nhất 1 item
2. Hiển thị tổng quan giỏ hàng
3. Nhập thông tin cho TẤT CẢ các chuyến trong giỏ:
   - Mỗi chuyến: số người lớn, số trẻ em, thông tin hành khách
4. Xác nhận đặt chỗ
5. Bắt đầu transaction:
   - Với mỗi Cart_Item:
     - Tạo Tour_Booking (status = 'PENDING')
     - Tạo Tour_Booking_Detail
     - Tạo Booking_Traveler cho từng hành khách
     - Cập nhật Trip.booked_seats
     - Tạo Invoice
   - Xóa tất cả Cart_Item sau khi tạo booking thành công
6. Commit transaction
7. Gửi email xác nhận tất cả booking

**Kiểm tra tính hợp lệ khi đặt tour:**

- Chuyến đi phải có status = 'SCHEDULED'
- Ngày khởi hành phải >= ngày hiện tại + 2 ngày
- Số chỗ yêu cầu <= số chỗ còn trống
- Thông tin hành khách phải đầy đủ
- Giấy tờ tùy thân (identity_doc) phải hợp lệ

### 7.6. Nghiệp vụ Quản lý đặt chỗ (Khách hàng)

**Xem danh sách đặt chỗ:**
Khách hàng vào mục "Booking của tôi":

```sql
SELECT tb.*, t.*, r.name as route_name, i.payment_status
FROM Tour_Booking tb
JOIN Trip t ON tb.trip_id = t.id
JOIN Route r ON t.route_id = r.id
JOIN Invoice i ON i.booking_id = tb.id
WHERE tb.user_id = :user_id
ORDER BY t.departure_date DESC
```

Hiển thị tab:

- Sắp tới (PENDING, CONFIRMED và departure_date >= today)
- Đã hoàn thành (COMPLETED)
- Đã hủy (CANCELED)

**Lọc đặt chỗ:**

- Theo trạng thái booking
- Theo trạng thái thanh toán
- Theo khoảng thời gian
- Theo tên tuyến

**Xem chi tiết đặt chỗ:**
Hiển thị đầy đủ thông tin:

- Thông tin tuyến và chuyến đi
- Thông tin booking (ngày đặt, số chỗ, tổng tiền, trạng thái)
- Danh sách hành khách:
  ```sql
  SELECT * FROM Booking_Traveler
  WHERE booking_id = :booking_id
  ```
- Thông tin hóa đơn:
  ```sql
  SELECT * FROM Invoice
  WHERE booking_id = :booking_id
  ```
- Lịch trình chi tiết của tuyến

**Chỉnh sửa thông tin hành khách:**

- Chỉ được phép nếu:
  - Booking có status = 'PENDING' hoặc 'CONFIRMED'
  - departure_date - today >= 3 ngày
- Khách hàng sửa thông tin trong form
- Cập nhật:
  ```sql
  UPDATE Booking_Traveler
  SET full_name = :name, gender = :gender,
      date_of_birth = :dob, identity_doc = :doc
  WHERE id = :traveler_id AND booking_id = :booking_id
  ```

**Thanh toán hóa đơn:**

- Hiển thị thông tin hóa đơn với payment_status = 'UNPAID'
- Khách hàng chọn phương thức thanh toán (payment_method)
- Có thể thanh toán một phần hoặc toàn bộ
- Sau khi thanh toán thành công:

  ```sql
  UPDATE Invoice
  SET payment_status = 'PAID', payment_method = :method
  WHERE id = :invoice_id

  UPDATE Tour_Booking
  SET status = 'CONFIRMED'
  WHERE id = :booking_id
  ```

- Gửi email xác nhận thanh toán và vé điện tử

**Hủy đặt chỗ:**
Khách hàng click "Hủy tour":

1. Kiểm tra điều kiện cho phép hủy:
   - Booking có status = 'PENDING' hoặc 'CONFIRMED'
   - Chưa quá hạn cho phép hủy
2. Hiển thị thông báo về chính sách hoàn tiền:
   - Tính số ngày còn lại đến ngày khởi hành
   - Hiển thị % hoàn tiền tương ứng
3. Khách hàng xác nhận hủy
4. Cập nhật:

   ```sql
   UPDATE Tour_Booking
   SET status = 'CANCELED'
   WHERE id = :booking_id

   UPDATE Invoice
   SET payment_status = 'REFUNDED'
   WHERE booking_id = :booking_id AND payment_status = 'PAID'

   UPDATE Trip
   SET booked_seats = booked_seats - :seats_booked
   WHERE id = :trip_id
   ```

5. Tạo yêu cầu hoàn tiền (nếu đã thanh toán)
6. Gửi email xác nhận hủy

### 7.7. Nghiệp vụ Quản lý Tuyến du lịch (Staff/Admin)

**Xem danh sách tuyến:**

```sql
SELECT r.*, COUNT(t.id) as total_trips
FROM Route r
LEFT JOIN Trip t ON r.id = t.route_id
GROUP BY r.id
ORDER BY r.id DESC
```

Hiển thị: tên, điểm đi, điểm đến, số ngày, số chuyến, trạng thái

**Lọc tuyến:**

- Theo trạng thái (OPEN, ONGOING, CLOSED)
- Theo điểm xuất phát, điểm đến
- Theo số ngày

**Thêm tuyến mới:**

1. Nhập thông tin cơ bản: name, start_location, end_location, duration_days, image
2. Chọn status (mặc định OPEN)
3. Thêm điểm tham quan cho từng ngày:
   - Chọn ngày (1 đến duration_days)
   - Chọn điểm tham quan từ danh sách Attraction
   - Nhập thứ tự trong ngày (order_in_day)
   - Nhập mô tả hoạt động (activity_description)
4. Kiểm tra:
   - Tên tuyến không trùng (logic unique)
   - duration_days > 0
   - Có ít nhất 1 điểm tham quan
5. Lưu:

   ```sql
   INSERT INTO Route (name, start_location, end_location, duration_days, image, status)
   VALUES (...)

   -- Lặp cho mỗi điểm tham quan:
   INSERT INTO Route_Attraction (route_id, attraction_id, day, order_in_day, activity_description)
   VALUES (...)
   ```

6. Thông báo thành công

**Xem chi tiết tuyến:**
Hiển thị đầy đủ:

- Thông tin tuyến
- Lịch trình chi tiết (Route_Attraction)
- Danh sách chuyến đi thuộc tuyến
- Thống kê: tổng booking, doanh thu

**Chỉnh sửa tuyến:**

1. Kiểm tra tuyến không ở trạng thái CLOSED
2. Cho phép sửa:
   - Thông tin cơ bản (name, start_location, end_location, duration_days, image)
   - Danh sách điểm tham quan (thêm, xóa, sửa)
3. Kiểm tra tương tự như thêm mới
4. Cập nhật:

   ```sql
   UPDATE Route SET ... WHERE id = :route_id

   -- Xóa điểm tham quan cũ:
   DELETE FROM Route_Attraction WHERE route_id = :route_id

   -- Thêm lại điểm tham quan mới:
   INSERT INTO Route_Attraction ... (lặp)
   ```

**Xóa/Ngừng hoạt động tuyến:**

1. Hiển thị xác nhận: "Bạn có chắc muốn xóa tuyến này?"
2. Kiểm tra ràng buộc:
   ```sql
   SELECT COUNT(*) FROM Trip WHERE route_id = :route_id
   SELECT COUNT(*) FROM Favorite_Tour WHERE route_id = :route_id
   ```
3. Nếu không có ràng buộc nào:
   - XÓA vĩnh viễn:
     ```sql
     DELETE FROM Route_Attraction WHERE route_id = :route_id
     DELETE FROM Route WHERE id = :route_id
     ```
4. Nếu có ràng buộc:
   - Chuyển status = 'CLOSED':
     ```sql
     UPDATE Route SET status = 'CLOSED' WHERE id = :route_id
     ```
   - Thông báo: "Tuyến có dữ liệu liên quan, đã chuyển sang trạng thái ngừng hoạt động"

### 7.8. Nghiệp vụ Quản lý Chuyến đi (Staff/Admin)

**Xem danh sách chuyến:**

```sql
SELECT t.*, r.name as route_name,
       (t.total_seats - t.booked_seats) as available_seats
FROM Trip t
JOIN Route r ON t.route_id = r.id
ORDER BY t.departure_date DESC
```

**Lọc chuyến:**

- Theo tuyến du lịch
- Theo trạng thái (SCHEDULED, ONGOING, FINISHED, CANCELED)
- Theo khoảng ngày khởi hành
- Theo mức độ lấp đầy (còn chỗ, gần đầy, đầy)

**Thêm chuyến mới:**

1. Chọn tuyến du lịch (route_id)
2. Nhập thông tin:
   - departure_date (phải >= ngày hiện tại + 7 ngày)
   - return_date (= departure_date + route.duration_days - 1)
   - price
   - total_seats
   - pick_up_time, pick_up_location
   - status (mặc định SCHEDULED)
3. Kiểm tra:
   - departure_date hợp lệ
   - price > 0
   - total_seats > 0
4. Tạo:
   ```sql
   INSERT INTO Trip (route_id, departure_date, return_date, price,
                     total_seats, booked_seats, pick_up_time,
                     pick_up_location, status)
   VALUES (..., 0, ...) -- booked_seats = 0
   ```

**Chỉnh sửa chuyến:**
Chỉ cho phép nếu status = 'SCHEDULED' và chưa có booking:

```sql
SELECT COUNT(*) FROM Tour_Booking WHERE trip_id = :trip_id
```

Nếu = 0 → Cho phép sửa tất cả
Nếu > 0 → Chỉ cho phép sửa: price (tăng giá), total_seats (tăng số chỗ), pick_up_time, pick_up_location

**Hủy chuyến:**

1. Kiểm tra có booking không
2. Nếu có booking:
   - Thông báo: "Chuyến có booking, việc hủy sẽ hoàn tiền 100% cho khách"
   - Yêu cầu xác nhận
   - Nếu đồng ý:

     ```sql
     UPDATE Tour_Booking SET status = 'CANCELED'
     WHERE trip_id = :trip_id

     UPDATE Invoice SET payment_status = 'REFUNDED'
     WHERE booking_id IN (SELECT id FROM Tour_Booking WHERE trip_id = :trip_id)

     UPDATE Trip SET status = 'CANCELED' WHERE id = :trip_id
     ```

   - Gửi email thông báo cho TẤT CẢ khách hàng
3. Nếu không có booking:
   - Đơn giản cập nhật status = 'CANCELED'

**Cập nhật trạng thái chuyến tự động:**
Hệ thống chạy job hàng ngày:

```sql
-- Chuyến đang khởi hành:
UPDATE Trip SET status = 'ONGOING'
WHERE status = 'SCHEDULED'
AND departure_date = CURRENT_DATE

-- Chuyến đã hoàn thành:
UPDATE Trip SET status = 'FINISHED'
WHERE status = 'ONGOING'
AND return_date < CURRENT_DATE

-- Cập nhật booking tương ứng:
UPDATE Tour_Booking SET status = 'COMPLETED'
WHERE trip_id IN (SELECT id FROM Trip WHERE status = 'FINISHED')
AND status = 'CONFIRMED'
```

### 7.9. Nghiệp vụ Quản lý Điểm tham quan (Staff/Admin)

**Xem danh sách điểm tham quan:**

```sql
SELECT a.*, c.name as category_name
FROM Attraction a
JOIN Category c ON a.category_id = c.id
WHERE a.status != 'DELETED'
ORDER BY a.name
```

**Thêm điểm tham quan mới:**

```sql
INSERT INTO Attraction (name, description, location, category_id, status)
VALUES (:name, :desc, :location, :category_id, 'ACTIVE')
```

**Chỉnh sửa điểm tham quan:**
Cho phép sửa tất cả thông tin trừ id

**Xóa điểm tham quan:**

- Không xóa vật lý mà chuyển status = 'DELETED'
- Kiểm tra có tuyến nào đang dùng không:
  ```sql
  SELECT DISTINCT r.name FROM Route r
  JOIN Route_Attraction ra ON r.id = ra.route_id
  WHERE ra.attraction_id = :attraction_id AND r.status = 'OPEN'
  ```
- Nếu có → Cảnh báo nhưng vẫn cho phép xóa (chuyển DELETED)

### 7.10. Nghiệp vụ Quản lý Người dùng (Admin)

**Xem danh sách người dùng:**

```sql
SELECT * FROM User
WHERE role IN ('CUSTOMER', 'STAFF')
ORDER BY id DESC
```

**Lọc người dùng:**

- Theo vai trò (CUSTOMER, STAFF, ADMIN)
- Theo trạng thái (is_lock)
- Theo ngày đăng ký

**Khóa/Mở khóa tài khoản:**

```sql
UPDATE User SET is_lock = :lock_status WHERE id = :user_id
```

Gửi email thông báo cho người dùng

**Thêm nhân viên (STAFF):**
Admin có thể tạo tài khoản STAFF trực tiếp:

```sql
INSERT INTO User (username, password, full_name, email, phone_number,
                  role, is_lock)
VALUES (..., 'STAFF', false)
```

**Xóa người dùng:**

- Kiểm tra người dùng có booking, cart_item, favorite không
- Nếu có → Không cho xóa, chỉ cho phép khóa
- Nếu không → Cho phép xóa vật lý

## 8. Báo cáo và Thống kê

Hệ thống cần cung cấp các báo cáo:

### 8.1. Báo cáo về Tour

- Danh sách tuyến du lịch theo trạng thái
- Tuyến có nhiều đặt chỗ nhất
- Tuyến có doanh thu cao nhất
- Tỷ lệ lấp đầy của các chuyến đi

### 8.2. Báo cáo về Khách hàng

- Danh sách khách hàng mới trong tháng
- Khách hàng đặt nhiều tour nhất
- Khách hàng có tổng chi tiêu cao
- Danh sách khách hàng vi phạm

### 8.3. Báo cáo về Đặt chỗ

- Thống kê đặt chỗ theo ngày/tháng/năm
- Tỷ lệ hủy tour
- Tỷ lệ thanh toán đúng hạn
- Doanh thu theo thời gian

### 8.4. Báo cáo về Thanh toán

- Tổng doanh thu theo tháng/quý/năm
- Danh sách hóa đơn chưa thanh toán
- Danh sách hoàn tiền
- Thống kê theo phương thức thanh toán

## 9. Các ràng buộc và Quy định

### 9.1. Về Đặt tour

- Mỗi chuyến đi có số chỗ giới hạn
- Không cho phép đặt quá số chỗ còn trống
- Phải cung cấp đầy đủ thông tin hành khách
- Phải thanh toán ít nhất 30% để xác nhận

### 9.2. Về Hủy tour

- Khách hàng có thể hủy tour theo quy định hoàn tiền
- Công ty có thể hủy chuyến nếu không đủ số người (thông báo trước 7 ngày)
- Hoàn tiền 100% nếu công ty hủy

### 9.3. Về Chỉnh sửa

- Khách hàng có thể chỉnh sửa thông tin hành khách trước 3 ngày khởi hành
- Không cho phép thay đổi chuyến đi sau khi đã xác nhận
- Muốn đổi chuyến phải hủy và đặt lại

### 9.4. Về Quyền hạn

- CUSTOMER: Chỉ quản lý đặt chỗ của mình
- STAFF: Quản lý tuyến, chuyến đi, xử lý đặt chỗ
- ADMIN: Toàn quyền quản lý, cấu hình hệ thống

## 10. Mở rộng trong tương lai

Hệ thống có thể mở rộng thêm:

- Đánh giá và nhận xét sau chuyến đi
- Chương trình khuyến mãi, giảm giá theo mùa
- Tích điểm thành viên thân thiết
- Tích hợp thanh toán trực tuyến
- Thông báo qua email, SMS
- Hỗ trợ đa ngôn ngữ
- Quản lý hướng dẫn viên
- Quản lý phương tiện vận chuyển
- Tích hợp đặt khách sạn, vé máy bay
