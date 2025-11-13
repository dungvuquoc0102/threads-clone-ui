# Cách tiếp cận một dự án

1. Đi từ bao quát tới chi tiết

2. Mô tả càng chi tiết càng tốt

# Mục tiêu duy nhất là xây dựng lộ trình dự án clone Frontend của threads.com

## Mô tả lộ trình làm dự án

1. Lựa chọn công nghệ:

- Vite
- React
- JS
- Routing: React Router
- Form: React Hook Form
- i18n: React i18next
- Validation: Yup
- CSS: Tailwind CSS
- UI Component: Shadcn
- State management: Redux Toolkit/RTK Query
- HTTP request: Axios
- Font icon: Fontawesome, Lucide icons (Shadcn), Hero icons (Tailwind)
- Font family: system-ui

2. Phân tích cấu trúc:

- Layouts: default layout, auth layout, no layout
  - Default layout:
    - Navigation
    - Add thread button
  - Auth layout:
    - Wrapper có background-image
  - No layout
- Pages:
  - Pages trong default layout:
    - Home page
      - Có nhiều pages, các pages xếp hàng ngang
      - Mỗi page có một state trong store
      - Khi có một page trong Home page thì click tên user hay bài thread thì chuyển trang. Nhưng nếu có nhiều page thì chỉ thay đổi nội dung của page đó.
    - For you page
      - Danh sách các bài thread
      - Modal đăng bài thread
    - Post detail page
      - Nội dung bài thread và danh sách comment
      - Modal đăng comment
    - Following page
      - Danh sách bài thread của những user đã follow
    - Ghost thread page
      - Danh sách bài thread đã lưu trữ quá 24h
    - Search page
      - Input on change hiển thị danh sách kết quả bên dưới
      - Filter
      - Follow suggestion
    - Activity page
      - Danh sách bài thread được gợi ý
    - Profile page
      - Thông tin của user (nếu user chính là mình thì hiển thị các nút action)
    - Insight page
      - Card và Chart của Shadcn để hiển thị insights (views, interactions, followers: by location, by age, by gender)
    - Setting page
      - Dùng Sidebar của Shadcn
      - Có 4 item trong Sidebar
    - Saved page
      - Danh sách bài thread đã lưu
  - Pages trong auth layout:
    - Login page
      - Form dùng RHF có 2 trường: email/username/phone và password
      - Có link dẫn tới trang "Quên mật khẩu"
      - Có nút đăng ký bằng Instagram
    - Register page
      - Nếu API có thì làm trang này
    - Forgot password page
      - Nếu API có thì làm trang này
    - Reset password page
      - Nếu API có thì làm trang này
  - Pages trong no layout:
    - Not found page
      - Hiển thị thông báo và nút "Back" quay lại trang chủ
    - Embed thread page
      - Xuất 1 khối code HTML và 1 thẻ script chứa logic nhúng iframe chứa thread vào khối code HTML

3. Thời gian

- Có 26 ngày, mỗi ngày dành khoảng 2-4 tiếng

## Yêu cầu

1. Dựa vào mô tả trên, làm chi tiết từng mô tả với code triển khai

2. Đưa ra kế hoạch, chia từng giai đoạn dựa trên thời gian trong mô tả để hoàn thành dự án đúng thời hạn
