Truy cập vào link: https://markdownlivepreview.com/ và dán nội dụng bên dưới để xem

# 📜 Tài Liệu Dự Án: Lộ Trình Clone Frontend Threads.com

## I. Mục Tiêu Dự Án

Mục tiêu duy nhất là xây dựng giao diện người dùng (Frontend) của Threads.com, mô phỏng gần nhất trải nghiệm người dùng trên thiết bị di động và desktop, hoàn thành trong **26 ngày** (khoảng 52-104 giờ làm việc).

## II. Công Nghệ Sử Dụng

Đây là bộ công nghệ hiện đại được lựa chọn để đảm bảo hiệu suất và khả năng mở rộng:

- **Dựng dự án:** Vite, React, JavaScript (JS)
- **Routing:** React Router
- **Quản lý Form:** React Hook Form
- **Validation:** Yup
- **CSS/Styling:** Tailwind CSS
- **UI Components:** Shadcn
- **State Management:** Redux Toolkit (RTK)
- **Data Fetching:** RTK Query (kết hợp với Axios)
- **HTTP Request:** Axios
- **Đa ngôn ngữ (i18n):** React i18next
- **Icon:** Fontawesome, Lucide icons (Shadcn), Hero icons (Tailwind)
- **Font Family:** `system-ui`

## III. Phân Tích Cấu Trúc Giao Diện

### 1. Cấu Trúc Layouts

Dự án sử dụng 3 loại layout chính để quản lý các nhóm trang:

- **Default Layout:** Chứa các thành phần chung như Navigation Bar (Sidebar/Footer), nút Thêm bài viết (`Add thread button`). Áp dụng cho hầu hết các trang chức năng.
- **Auth Layout:** Dành cho các trang đăng nhập/đăng ký, có một Wrapper với `background-image` đặc trưng.
- **No Layout:** Dành cho các trang đặc biệt như 404 hoặc trang nhúng (Embed).

### 2. Cấu Trúc Pages

| Nhóm Layout   | Trang (Pages)         | Tính năng nổi bật                                                                                                    |
| :------------ | :-------------------- | :------------------------------------------------------------------------------------------------------------------- |
| **Default**   | Home Page             | Chia thành nhiều Pages (For You, Following) với logic state nội bộ.                                                  |
|               | For You Page          | Danh sách bài viết (Thread List) và Modal đăng bài viết.                                                             |
|               | Post Detail Page      | Chi tiết bài viết và danh sách comment. Modal đăng comment.                                                          |
|               | Following Page        | Danh sách bài viết từ những người dùng đã theo dõi.                                                                  |
|               | Ghost Thread Page     | Danh sách bài viết đã lưu trữ quá 24h.                                                                               |
|               | Search Page           | Input tìm kiếm _on-change_, Filter, Gợi ý theo dõi.                                                                  |
|               | Activity Page         | Danh sách các hoạt động gợi ý.                                                                                       |
|               | Profile Page          | Thông tin User, hiển thị các nút hành động nếu là User chính.                                                        |
|               | Insight Page          | Hiển thị Card và Chart (dùng Shadcn) cho các chỉ số (views, tương tác, người theo dõi theo địa lý, tuổi, giới tính). |
|               | Setting Page          | Dùng Shadcn Sidebar, chứa 4 mục cài đặt.                                                                             |
|               | Saved Page            | Danh sách bài viết đã lưu.                                                                                           |
| **Auth**      | Login Page            | Form (RHF) với 2 trường, link "Quên mật khẩu", nút Đăng ký bằng Instagram.                                           |
|               | Register Page         | Trang đăng ký (nếu API có).                                                                                          |
|               | Forgot/Reset Password | Trang quên/đặt lại mật khẩu (nếu API có).                                                                            |
| **No Layout** | Not Found Page (404)  | Hiển thị thông báo và nút "Back".                                                                                    |
|               | Embed Thread Page     | Xuất khối code HTML và thẻ script logic nhúng iframe chứa Thread.                                                    |

## IV. Lộ Trình Dự Án Chi Tiết (26 Ngày)

Lộ trình được điều chỉnh để tập trung 75% thời gian cho việc phát triển tính năng (Giai đoạn 2 & 3).

### 🎯 Giai đoạn 1: Thiết Lập & Cấu Trúc Cơ Bản (2 Ngày)

Mục tiêu: Đưa dự án vào trạng thái sẵn sàng phát triển tính năng.

- **Ngày 1:** Khởi tạo dự án (Vite/React/JS), cấu trúc khung dự án, cài đặt và cấu hình **Tailwind CSS**, **Shadcn UI**, theme, **React i18next** (en/vi), **React Router**, **RTK Query**, **Axios**.
  - Khởi tại dự án với Vite/React/JS: npm create vite@latest threads-clone-ui -- --template react
  - Cấu trúc khung dự án, trong src có:
    - configs: index.js, routes.js
    - components:
      - ui (của Shadcn):
        (hệ form) button, spinner, input, select, textarea, radio group, progress, input otp, input group, field, date picker, card
        (hệ hiện thị dữ liệu) button, spinner, card, tabs, skeleton, tooltip, toggle, scroll area, typography
        (hệ hiện thị popup) sonner (toast), alert dialog, dialog, pop over, hover card, dropdown menu, drawer, context menu, command
    - pages: NotFound.jsx, Login.jsx, Register.jsx, Forgot.jsx, Reset.jsx, Home.jsx, ForYou.jsx, PostDetail.jsx, Following.jsx, Activity.jsx, Search.jsx, Profile.jsx, Insight.jsx, Setting.jsx, Saved.jsx, GhostPost.jsx, EmbedThread.jsx
    - layouts: DefaultLayout.jsx, AuthLayout.jsx, NoLayout.jsx
    - assets: images/placeholder-avatar.png
    - public: images/logo.png, images/favicon.png
    - .env: BASE_URL
- **Ngày 2:** Xây dựng 3 Layouts (`Default`, `Auth`, `NoLayout`) và `NotFoundPage`. Triển khai UI thanh Navigation cơ bản.

### 🎯 Giai đoạn 2: Phát Triển Tính Năng Lõi (12 Ngày)

Mục tiêu: Hoàn thành các tính năng cốt lõi nhất, đặc biệt là phần giao tiếp API và Trang chủ.

- **Ngày 3 (Auth):** Xây dựng `LoginPage`, `RegisterPage`, `ForgotPage`, `ResetPage`. Áp dụng **RHF + Yup** cho Form. Hoàn thiện UI **Auth Layout Wrapper**.
- **Ngày 4 - 5 (API Setup - Ưu tiên cao):** Cài đặt **Axios**. Thiết lập **RTK Query API Slice/Redux Toolkit Slice** với `axiosBaseQuery` tùy chỉnh. Định nghĩa endpoints ban đầu (login, fetch threads).
- **Ngày 6 - 8 (Home Page - Ưu tiên cao):** Xây dựng `HomePage`. Triển khai logic **Redux State** để quản lý các Tab con (For You, Following) và đảm bảo logic chuyển trang/thay đổi nội dung hoạt động chính xác.
- **Ngày 9 - 10 (Modal Post - Ưu tiên cao):** Xây dựng **Modal Đăng bài Thread** (Shadcn Dialog/Sheet). Thiết kế Form đăng bài (nội dung, ảnh) dùng RHF.
- **Ngày 11 - 12:** Xây dựng `ForYouPage` và component `ThreadItem`. Sử dụng **RTK Query Hook** để hiển thị danh sách bài viết.
- **Ngày 13:** Xây dựng `PostDetailPage` và UI danh sách Comment. Xây dựng **Modal đăng Comment**.
- **Ngày 14:** Xây dựng `ProfilePage` (Header, Tabs) và logic hiển thị nút hành động.

### 🎯 Giai đoạn 3: Phát Triển Tính Năng Phụ Trợ & Nâng Cao (10 Ngày)

Mục tiêu: Hoàn thành tất cả các trang UI còn lại, bao gồm các phần phức tạp như Insights.

- **Ngày 15 - 16:** Xây dựng `SearchPage`. Triển khai Input tìm kiếm và UI hiển thị kết quả/Filter.
- **Ngày 17 - 18 (Insights):** Xây dựng `InsightPage`. Thiết kế UI **Card và Chart** (sử dụng mockup data) cho các chỉ số phân tích.
- **Ngày 19:** Xây dựng `SettingPage`. Triển khai **Shadcn Sidebar** Navigation và UI cho 4 mục cài đặt.
- **Ngày 20:** Xây dựng `ActivityPage` (danh sách hoạt động) và `FollowingPage`.
- **Ngày 21:** Xây dựng `SavedPage` và `GhostThreadPage`.
- **Ngày 22 - 23:** Làm sạch UI của các trang phụ.
- **Ngày 24:** Xây dựng `EmbedThreadPage` (UI Thread nhỏ gọn và mockup code nhúng).

### 🎯 Giai đoạn 4: Tinh Chỉnh, Bảo trì và Hoàn thiện (2 Ngày)

Mục tiêu: Rà soát, làm sạch và đóng gói dự án.

- **Ngày 25:** Tối ưu hóa UI/UX và Fix Bugs. Kiểm tra **Responsive Design** trên các kích thước màn hình. Rà soát Validation Form và các luồng tương tác.
- **Ngày 26:** Hoàn thiện **i18n** (đảm bảo tất cả text đã được dịch). Dọn dẹp code, tối ưu hóa cơ bản và viết tài liệu `README.md`.

---

Đây là lộ trình chi tiết và sát sao theo thời gian 26 ngày của bạn. Với sự tập trung vào Giai đoạn 2, bạn sẽ nhanh chóng có được một ứng dụng hoạt động đầy đủ.

Bạn muốn tôi **cung cấp mã mẫu cho việc quản lý trạng thái của các Tab trong Home Page (Redux State)** để đảm bảo logic phức tạp này được triển khai chính xác ngay từ đầu không?
