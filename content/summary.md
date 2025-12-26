---
date: 2025-12-10
draft: false
hidemeta: true
layout: "page"
---

<style>
/* =========================================
   1. CẤU HÌNH KHUNG CV
   ========================================= */
.post-content { max-width: 100% !important; padding: 0 !important; background: transparent !important; }

.cv-container {
    display: flex;
    gap: 40px;
    margin-top: 20px;
    font-family: 'Segoe UI', sans-serif;
    color: var(--primary);
}

/* =========================================
   2. CỘT TRÁI (THÔNG TIN & KỸ NĂNG)
   ========================================= */
.cv-sidebar {
    flex: 0 0 280px; /* Chiều rộng cố định cột trái */
    background: var(--entry);
    padding: 30px;
    border-radius: 12px;
    border: 1px solid var(--border);
    height: fit-content;
}
/* --- PHẦN CHỈNH SỬA ẢNH TRÒN (FIXED) --- */
.cv-avatar {
    /* Dùng !important để ghi đè CSS mặc định của theme */
    width: 200px !important;
    height: 200px !important;   
    border-radius: 50% !important;
    object-fit: cover !important;
    border: 5px solid #ffffff !important;
    margin: 0 auto 25px auto !important;
    display: block !important;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15) !important;
    background-color: #fff !important; 
    padding: 0 !important;
    max-width: unset !important;
}
/* Tiêu đề mục nhỏ */
.sidebar-title {
    font-size: 14px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 15px;
    padding-bottom: 10px;
    border-bottom: 2px solid #eee;
    color: #555;
}

/* Kỹ năng dạng Tag */
.skill-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 30px; }
.tag {
    background: #eef2ff;
    color: #6c8af1;
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 13px;
    font-weight: 600;
}
/* Dark mode fix cho tag */
@media (prefers-color-scheme: dark) {
    .tag { background: #333; color: #a2b9ff; }
}

/* Thông tin liên hệ */
.contact-list { list-style: none; padding: 0; margin-bottom: 30px; }
.contact-list li {
    font-size: 14px;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 10px;
}
.icon { width: 16px; color: #888; }

/* =========================================
   3. CỘT PHẢI (NỘI DUNG CHÍNH)
   ========================================= */
.cv-main { flex: 1; }

.section-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 25px;
    margin-top: 10px;
}
.section-icon {
    width: 40px; height: 40px;
    background: #6c8af1;
    color: white;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
}
.section-title {
    font-size: 20px;
    font-weight: 800;
    text-transform: uppercase;
    color: var(--primary);
    margin: 0;
}

/* Timeline Item (Dùng cho Kinh nghiệm & Giáo dục) */
.timeline-box {
    border-left: 2px solid #e0e0e0;
    padding-left: 30px;
    margin-left: 20px;
    margin-bottom: 40px;
    position: relative;
}

.timeline-item {
    position: relative;
    margin-bottom: 30px;
}
/* Dấu chấm tròn trên timeline */
.timeline-item::before {
    content: "";
    position: absolute;
    left: -37px;
    top: 5px;
    width: 12px;
    height: 12px;
    background: #fff;
    border: 3px solid #6c8af1;
    border-radius: 50%;
}

.time-badge {
    display: inline-block;
    background: #6c8af1;
    color: white;
    font-size: 12px;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 20px;
    margin-bottom: 8px;
}

.item-title {
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 5px;
    color: var(--primary);
}

.item-subtitle {
    font-size: 15px;
    font-weight: 600;
    color: #888;
    margin-bottom: 10px;
    display: block;
}

.item-desc {
    font-size: 15px;
    line-height: 1.6;
    color: var(--secondary);
    text-align: justify;
}
.item-desc ul { margin-left: 20px; margin-top: 5px; }

/* Grid cho Chứng chỉ & Giải thưởng */
.grid-box {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}
/* --- SỬA LẠI CSS CARD-SIMPLE --- */
.card-simple {
    background: var(--entry);
    padding: 25px 15px; /* Tăng khoảng cách đệm */
    border: 1px solid var(--border);
    border-radius: 16px; /* Bo góc tròn nhiều hơn giống hình mẫu */
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    
    /* Hiệu ứng bóng đổ nhẹ giống thẻ bài */
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    transition: transform 0.3s ease;
}

.card-simple:hover {
    transform: translateY(-5px); /* Hiệu ứng bay lên khi di chuột */
}

/* --- THÊM CLASS MỚI CHO ẢNH CHỨNG CHỈ --- */
.cert-img {
    width: 350px; /* Kích thước ảnh */
    height: 350px;
    object-fit: contain;
    margin-bottom: 15px;
    border-radius: 8px; 
}

.card-title {
    font-weight: 700;
    font-size: 16px;
    margin-bottom: 5px;
    display: block;
    color: var(--primary);
}
/* =========================================
   4. LIGHTBOX (HIỆU ỨNG PHÓNG TO ẢNH)
   ========================================= */
/* Lớp phủ nền đen mờ */
.lightbox-overlay {
    display: none; /* Mặc định ẩn */
    position: fixed; /* Cố định trên màn hình */
    z-index: 9999; /* Nổi lên trên cùng mọi thứ */
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.85); /* Màu đen mờ 85% */
    align-items: center;
    justify-content: center;
    cursor: zoom-out; /* Con trỏ chuột báo hiệu bấm để thoát */
    padding: 20px;
    backdrop-filter: blur(5px); /* Hiệu ứng làm mờ nền phía sau (tùy chọn) */
}

/* Class này được thêm vào bằng JS để hiện overlay lên */
.lightbox-overlay.active {
    display: flex;
    animation: fadeIn 0.3s ease;
}

/* Ảnh lớn bên trong overlay */
.lightbox-overlay img {
    max-width: 90%;
    max-height: 90%;
    object-fit: contain;
    border-radius: 8px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    border: 2px solid #fff;
    animation: zoomIn 0.3s ease;
}

/* Thêm hiệu ứng chuyển động nhẹ nhàng */
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
@keyframes zoomIn { from { transform: scale(0.9); } to { transform: scale(1); } }

/* Con trỏ chuột khi di vào ảnh nhỏ để biết là bấm được */
.cert-img.lightbox-trigger {
    cursor: zoom-in;
    transition: transform 0.2s;
}
.cert-img.lightbox-trigger:hover {
   transform: scale(1.05);
}
/* =========================================
   5. SKILL RATING (CHẤM ĐIỂM KỸ NĂNG)
   ========================================= */
.skill-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); /* Tự động chia cột */
    gap: 15px;
    margin-left: 20px; /* Căn lề giống timeline-box cũ */
    margin-bottom: 40px;
}

.skill-card-rating {
    background: var(--entry);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 15px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    transition: transform 0.2s;
    position: relative;
    overflow: hidden;
}

.skill-card-rating:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
}

/* Thanh màu trang trí dưới đáy giống hình 1 */
.skill-card-rating::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 100%; height: 3px;
    background: #e0e0e0;
}
/* Các màu sắc riêng cho từng loại (Tùy chọn) */
.skill-card-rating.blue::after { background: #6c8af1; }
.skill-card-rating.orange::after { background: #ff9f43; }
.skill-card-rating.purple::after { background: #a55eea; }
.skill-card-rating.green::after { background: #2bcbba; }

.skill-header-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.skill-name {
    font-weight: 700;
    color: var(--primary);
    font-size: 15px;
    display: flex;
    align-items: center;
    gap: 8px;
}

/* HỆ THỐNG CHẤM ĐIỂM (DOTS) */
.rating-dots {
    display: flex;
    gap: 4px;
}

.dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: #e0e0e0; /* Màu xám cho điểm chưa đạt */
}

.dot.filled {
    background-color: #6c8af1; /* Màu xanh cho điểm đã đạt */
}
/* =========================================
   6. MỤC TIÊU VÀ ĐỊNH HƯỚNG (NEW)
   ========================================= */
.goals-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 25px;
    margin-left: 20px; /* Thụt vào thẳng hàng với timeline */
    margin-bottom: 40px;
}

.goal-card {
    background: var(--entry);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 25px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.03);
    transition: transform 0.3s;
}

.goal-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.08);
}

.goal-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 20px;
}

.goal-icon-box {
    width: 45px;
    height: 45px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
}

.short-term .goal-icon-box {
    background-color: #e3f2fd;
    color: #1976d2;
}

.long-term .goal-icon-box {
    background-color: #ffebee;
    color: #e53935;
}

.goal-title {
    margin: 0;
    font-size: 18px;
    font-weight: 800;
    color: var(--primary);
}

.goal-list {
    margin: 0;
    padding-left: 20px;
}

.goal-list li {
    font-size: 15px;
    color: var(--secondary);
    margin-bottom: 10px;
    line-height: 1.5;
}

/* Dark mode overrides for goals */
@media (prefers-color-scheme: dark) {
    .goal-card { background: #1e1e1e; border-color: #333; }
    .short-term .goal-icon-box { background-color: #15202b; color: #64b5f6; }
    .long-term .goal-icon-box { background-color: #2c1a1a; color: #ef9a9a; }
}
</style>

<div class="cv-container">
    <div class="cv-sidebar">
        <img src="/NguyenDucQui_Blog/avarta1.jpg" class="cv-avatar" alt="Avatar">      
        <div class="sidebar-title">LIÊN HỆ</div>
        <ul class="contact-list">
            <li></span> TP. Hồ Chí Minh</li>
            <li></span> nguyenducqui2004@gmail.com</li>
            <li></span> Đại học HUTECH</li>
        </ul>
        <div class="sidebar-title">KỸ NĂNG CHUYÊN MÔN</div>
        <div class="skill-tags">
            <span class="tag">Java Core</span>
            <span class="tag">Socket Programming</span>
            <span class="tag">Network Security</span>
            <span class="tag">Wazuh / OPNsense</span>
            <span class="tag">Linux / Ubuntu</span>
            <span class="tag">Git / Github</span>
        </div>
        <div class="sidebar-title">KỸ NĂNG MỀM</div>
        <div class="skill-tags">
            <span class="tag">Làm việc nhóm</span>
            <span class="tag">Tư duy phản biện</span>
            <span class="tag">Giải quyết vấn đề</span>
            <span class="tag">Quản lý thời gian</span>
        </div>
        <a href="https://drive.google.com/file/d/1OFvfhNxF8TCTsTdroENzYTbKmw6mQpUr/view?usp=drive_link" style="display:block; text-align:center; background:#6c8af1; color:white; padding:10px; border-radius:6px; margin-top:20px; font-weight:bold; text-decoration:none;">📥 TẢI CV (PDF)</a>
    </div>
    <div class="cv-main">
        <div class="section-header">
            <div class="section-icon">🎓</div>
            <h2 class="section-title">GIÁO DỤC</h2>
        </div>
        <div class="timeline-box">
            <div class="timeline-item">
                <span class="time-badge">2025 - Hiện tại</span>
                <h3 class="item-title">Sinh viên ngành Công nghệ thông tin</h3>
                <span class="item-subtitle">Đại học Công nghệ TP.HCM (HUTECH)</span>
                <div class="item-desc">
                    <p>Chuyên ngành: <strong>An Ninh Mạng</strong>.</p>
                    <ul>
                        <li>GPA hiện tại: <strong>3.2/4.0</strong> (Giỏi)</li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="section-header">
            <div class="section-icon">💼</div>
            <h2 class="section-title">KINH NGHIỆM & DỰ ÁN</h2>
        </div>
        <div class="timeline-box">
            <div class="timeline-item">
                <span class="time-badge">12/2025</span>
                <h3 class="item-title">Dự án: Xây dựng và triển khai hệ thông SIEM Wazuh: phát hiện, hiệu chỉnh và đo lường</h3>
                <span class="item-subtitle">Vai trò: Trưởng nhóm</span>
                <div class="item-desc">
                    <ul>
                        <li>Xây dựng hệ thống giám sát an ninh sử dụng <strong>Wazuh SIEM</strong> và <strong>OPNsense</strong>.</li>
                        <li>Viết module Python tích hợp cảnh báo qua Telegram/Email khi phát hiện tấn công Brute Force.</li>
                        <li>Kết quả: Giảm thời gian phát hiện sự cố từ 30 phút xuống còn 2 phút.</li>
                    </ul>
                </div>
            </div>
            <div class="timeline-item">
                <span class="time-badge">06/2025</span>
                <h3 class="item-title">Dự án: Ứng dụng giám sát máy tính nội bộ </h3>
                <span class="item-subtitle">Vai trò: Lập trình viên </span>
                <div class="item-desc">
                    <ul>
                        <li>Phát hiện các thao tác bất thường trên máy client và máy chủ.</li>
                        <li>Tính năng: Tìm kiếm, thông báo, chặn các ip bất thường gây nguy hiểm cho máy tính.</li>
                    </ul>
                </div>
            </div>
        </div>       
        <div class="section-header">
        <div class="section-icon">🚀</div>
            <h2 class="section-title">Kỹ năng & Công nghệ</h2>
        </div>
        <div class="skill-grid">
            <div class="skill-card-rating orange">
                <div class="skill-header-row">
                    <span class="skill-name">☕ Java Core</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                </div>
                <span style="font-size: 12px; color: #888;">Spring Boot, Hibernate</span>
            </div>
            <div class="skill-card-rating blue">
                <div class="skill-header-row">
                    <span class="skill-name">⚡ JavaScript</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot"></span>
                </div>
                <span style="font-size: 12px; color: #888;">ReactJS, Node.js basics</span>
            </div>
            <div class="skill-card-rating green">
                <div class="skill-header-row">
                    <span class="skill-name">🛡️ Net Security</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                </div>
                <span style="font-size: 12px; color: #888;">Wazuh, OPNsense, Snort</span>
            </div>
            <div class="skill-card-rating purple">
                <div class="skill-header-row">
                    <span class="skill-name">🐧 Linux / OS</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot"></span>
                </div>
                <span style="font-size: 12px; color: #888;">Ubuntu, CentOS, Bash Script</span>
            </div>   
            <div class="skill-card-rating blue">
                <div class="skill-header-row">
                    <span class="skill-name">🗄️ Database</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot"></span>
                </div>
                <span style="font-size: 12px; color: #888;">MySQL, SQL Server</span>
            </div>
            <div class="skill-card-rating orange">
                <div class="skill-header-row">
                    <span class="skill-name"> English</span>
                </div>
                <div class="rating-dots">
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                    <span class="dot filled"></span>
                </div>
                <span style="font-size: 12px; color: #888;">Đọc hiểu tài liệu, B1</span>
            </div>
        </div>
        <div class="section-header">
            <div class="section-icon">🎯</div>
            <h2 class="section-title">MỤC TIÊU & ĐỊNH HƯỚNG</h2>
        </div>
        <div class="goals-container">
            <div class="goal-card short-term">
                <div class="goal-header">
                    <div class="goal-icon-box">🎯</div>
                    <h3 class="goal-title">Mục tiêu ngắn hạn</h3>
                </div>
                <ul class="goal-list">
                    <li>Hoàn thành khóa học lập trình mạng</li>
                    <li>Thành thạo Java và JavaScript</li>
                    <li>Xây dựng profile cá nhân</li>
                    <li>Hoàn thành đồ án môn học</li>
                </ul>
            </div> 
            <div class="goal-card long-term">
                <div class="goal-header">
                    <div class="goal-icon-box">🚀</div>
                    <h3 class="goal-title">Mục tiêu dài hạn</h3>
                </div>
                <ul class="goal-list">
                    <li>Trở thành Coder chuyên nghiệp</li>
                    <li>Làm việc tại công ty công nghệ lớn</li>
                    <li>Bảo vệ hệ thống khỏi tấn công mạng</li>
                    <li>Chia sẻ kiến thức qua blog và video</li>
                </ul>
            </div>
        </div>
        <div class="section-header">
            <div class="section-icon">📜</div>
            <h2 class="section-title">CHỨNG CHỈ</h2>
            </div>
            <div class="timeline-box" style="border:none; padding-left:0; margin-left:0;">
            <div class="grid-box" style="grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));">           
                <div class="card-simple">
                    <img src="/NguyenDucQui_Blog/NetworkingBasics.png" class="cert-img lightbox-trigger" alt="Networking Basics">
                    <span class="card-title">Networking Basics</span>
                    <span class="card-sub">Cấp bởi: Cisco Networking</span>
                </div>
                <div class="card-simple">
                    <img src="/NguyenDucQui_Blog/JavaScriptEssentials1.png" class="cert-img lightbox-trigger" alt="JavaScript Essentials 1">
                    <span class="card-title">JavaScript Essentials 1</span>
                    <span class="card-sub">Cấp bởi: Cisco Networking</span>
                </div>
                <div class="card-simple">
                    <img src="/NguyenDucQui_Blog/JavaScriptEssentials2.png" class="cert-img lightbox-trigger" alt="JavaScript Essentials 2">
                    <span class="card-title">JavaScript Essentials 2</span>
                    <span class="card-sub">Cấp bởi: Cisco Networking</span>
                </div>
            </div>
        </div>
    </div>
</div>
<script>
document.addEventListener('DOMContentLoaded', function() {
    // 1. Tạo các phần tử HTML cho lớp phủ (overlay) một cách tự động
    const overlay = document.createElement('div');
    overlay.className = 'lightbox-overlay'; 
    const overlayImg = document.createElement('img');
    overlay.appendChild(overlayImg);   
    // Thêm lớp phủ vào thân trang web
    document.body.appendChild(overlay);
    // 2. Tìm tất cả các ảnh có class 'lightbox-trigger'
    const triggers = document.querySelectorAll('.lightbox-trigger');
    // 3. Gắn sự kiện click cho từng ảnh nhỏ
    triggers.forEach(trigger => {
        trigger.addEventListener('click', function() {
            // Lấy đường dẫn ảnh (src) của ảnh vừa bấm
            const imgSrc = this.getAttribute('src');
            // Gán đường dẫn đó cho ảnh lớn trong overlay
            overlayImg.src = imgSrc;
            // Hiện overlay lên
            overlay.classList.add('active');
            // Ngăn cuộn trang khi đang xem ảnh lớn
            document.body.style.overflow = 'hidden';
        });
    });
    // 4. Gắn sự kiện click để đóng overlay (khi bấm vào vùng đen hoặc ảnh lớn)
    overlay.addEventListener('click', function() {
        // Ẩn overlay đi
        overlay.classList.remove('active');
        // Cho phép cuộn trang trở lại
        document.body.style.overflow = 'auto';
        // Xóa src ảnh để lần sau mở không bị nháy ảnh cũ
        setTimeout(() => { overlayImg.src = ''; }, 300);
    });
});
</script>