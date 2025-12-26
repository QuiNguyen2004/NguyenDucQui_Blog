---
date: 2025-12-10
draft: false
hidemeta: true
---

<style>
/* =========================================
   1. CẤU HÌNH KHUNG TOÀN TRANG (Đã chỉnh lại cho 1 cột)
   ========================================= */
.main { 
    max-width: 100% !important; /* Để container ngoài cùng full */
    margin: 0 auto !important; 
    padding: 0 !important; 
}

/* Layout Chính: Căn giữa, giới hạn chiều rộng để dễ đọc */
.page-layout { 
    width: 100%;
    max-width: 960px; 
    margin: 40px auto; 
    padding: 0 20px;
    display: block; 
}

/* =========================================
   2. HEADER: ẢNH BANNER
   ========================================= */
.about-image { 
    display: block;
    width: 100%;
    text-align: center;
    margin: 0 auto 50px auto;
}
.my-photo {
    display: block;
    width: 100%;
    height: 1000px; 
    object-fit: cover;
    object-position: center 25%;
    border-radius: 12px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1); 
    border: none;
}

/* =========================================
   3. GIAO DIỆN THÔNG TIN (INFO + INTRO)
   ========================================= */
.profile-split-layout {
    display: flex;
    gap: 40px;
    align-items: flex-start;
    margin-bottom: 40px;
    padding-bottom: 30px;
    border-bottom: 1px dashed #eee; /* Đường gạch ngăn cách nhẹ */
}

/* Cột thông tin nhỏ bên trái */
.profile-info-side {
    flex: 0 0 200px; /
    display: flex;
    flex-direction: column;
    align-items: flex-start; /* Canh trái cho gọn */
    gap: 10px; 
    padding-right: 5px;
    border-right: 1px solid #eee;
}

.meta-item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    text-align: left;
    font-family: 'Segoe UI', sans-serif;
}
.meta-label {
    font-size: 0.75rem; color: #888; text-transform: uppercase;
    letter-spacing: 1px; margin-bottom: 5px; font-weight: 600;
}
.meta-value {
    font-size: 0.95rem; font-weight: 700; color: #333;
    display: flex; align-items: center; gap: 8px;
}
.meta-icon { font-size: 1rem; }

/* Cột Text giới thiệu bên phải */
.profile-text-side {
    flex: 1;
}

.content-style { 
    font-family: 'Segoe UI', sans-serif; 
    font-size: 1.05rem; 
    line-height: 1.8; 
    color: var(--primary); 
    text-align: justify; 
}
.content-style p { margin-bottom: 20px; }
.content-style strong { color: #000; font-weight: 700; }

/* Responsive cho Mobile */
@media (max-width: 768px) {
    .profile-split-layout { flex-direction: column; gap: 30px; border: none; }
    .profile-info-side { 
        width: 100%; 
        flex-direction: row; 
        flex-wrap: wrap; 
        justify-content: space-between;
        border-right: none; 
        border-bottom: 1px solid #eee; 
        padding-bottom: 20px; padding-right: 0;
    }
    .meta-item { margin-bottom: 10px; width: 48%; } /* Chia 2 cột trên mobile */
    .my-photo { height: 400px; } /* Ảnh nhỏ lại trên mobile */
}

/* =========================================
   4. TESTIMONIALS (GÓC NHÌN ĐỒNG ĐỘI)
   ========================================= */
.testimonials-section { margin-top: 40px; padding-top: 30px; border-top: 1px solid #eee; }
.tech-header {
    width: 100%; text-align: center; 
    font-weight: 800; font-size: 1.2rem; margin-bottom: 30px; color: #444; text-transform: uppercase; letter-spacing: 1px;
}
.testi-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 25px; }
@media (max-width: 768px) { .testi-grid { grid-template-columns: 1fr; } }

.testi-card { 
    background: var(--entry); 
    padding: 25px; 
    border-radius: 12px; 
    border: 1px solid var(--border); 
    font-size: 0.95rem; 
    box-shadow: 0 4px 10px rgba(0,0,0,0.03); 
    transition: transform 0.2s;
}
.testi-card:hover { transform: translateY(-3px); } /* Hiệu ứng hover nhẹ */

.quote-icon { font-size: 2.5rem; color: #ddd; line-height: 1; margin-bottom: 10px; font-family: serif; }
.testi-author { display: flex; align-items: center; gap: 12px; margin-top: 20px; }
.author-avatar { 
    width: 40px; height: 40px; border-radius: 50%; 
    display: flex; align-items: center; justify-content: center; 
    font-weight: bold; font-size: 1rem; 
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.author-info { display: flex; flex-direction: column; }
.author-name { font-weight: 700; font-size: 0.95rem; color: var(--primary); }
.author-role { font-size: 0.75rem; color: var(--secondary); margin-top: 2px; }

</style>

<div class="page-layout">    
    <div class="about-image">
        <img src="/NguyenDucQui_Blog/anhabout.jpg" class="my-photo" alt="Avatar">
    </div>                 
    <div class="profile-split-layout">               
        <div class="profile-info-side">
            <div class="meta-item">
                <span class="meta-label">Địa điểm</span>
                <div class="meta-value"></span> TP. Hồ Chí Minh</div>
            </div>
            <div class="meta-item">
                <span class="meta-label">Email</span>
                <div class="meta-value"></span> nguyenducqui2004@gmail.com</div>
            </div>
            <div class="meta-item">
                <span class="meta-label">Học vấn</span>
                <div class="meta-value"></span> HUTECH University</div>
            </div>
            <div class="meta-item">
                <span class="meta-label">Trạng thái</span>
                <div class="meta-value"></span> Sẵn sàng</div>
            </div>
        </div>
        <div class="profile-text-side">                   
            <div class="content-style">
                <p>Tên tôi là <strong>Đức Qui</strong>. Nếu như "Đức" đại diện cho sự tử tế trong đạo đức nghề nghiệp, thì "Qui" gợi nhắc tôi về sự Quy chuẩn và Kiên định – những yếu tố cốt lõi của một hệ thống mạng vững chắc. Tôi luôn mong muốn sống và làm việc đúng như tên mình: xây dựng những giải pháp công nghệ không chỉ hoạt động tốt mà còn phải chuẩn mực, minh bạch và đáng tin cậy. Sắp hoàn thành chương trình đại học, tôi đã sẵn sàng "Online", tự tin kết nối và truyền tải giá trị của mình vào thế giới công nghệ rộng lớn.</p>
            </div>
        </div>
    </div> 
    <div class="full-width-content content-style">              
        <p>Niềm đam mê với những dòng mã (code) của tôi bắt đầu từ thời trung học, khi tôi lần đầu tiên tò mò về cách hai chiếc máy tính có thể "trò chuyện" với nhau qua mạng. Sự tò mò ấy đã thôi thúc tôi theo đuổi tấm bằng Kỹ sư Công nghệ thông tin (chuyên ngành Mạng & Truyền thông).</p>                
        <p>Từ đó, tôi luôn nỗ lực hết mình để không chỉ nắm vững lý thuyết mà còn làm chủ công nghệ thực tế. Tôi chủ động tham gia các dự án cá nhân (như blog bạn đang xem), nghiên cứu sâu về nhiều lĩnh vực, nhằm mở rộng kiến thức và mài giũa tư duy logic của bản thân.</p>                
        <p>Dù thế giới số luôn vận động không ngừng, tôi vẫn trân trọng những khoảng thời gian riêng tư bên ly cà phê, nghiền ngẫm một thuật toán hay hoặc đọc sách về kiến trúc phần mềm. Sở thích của tôi là sưu tầm những công nghệ mới và những tư duy đột phá, coi đó là nhiên liệu giúp tôi tiến về phía trước.</p>
        <p>Hiện tại, tôi đang tìm kiếm cơ hội tại một môi trường công nghệ năng động, chuyên nghiệp, nơi tôi có thể cống hiến tư duy logic và kỹ năng lập trình của mình. Mời bạn dành chút thời gian xem qua Danh mục đầu tư (Projects) và Hồ sơ năng lực của tôi. Đừng ngần ngại liên hệ nếu chúng ta có cùng tần số!</p>
        <div class="testimonials-section">
            <div class="tech-header">💬 GÓC NHÌN TỪ ĐỒNG ĐỘI</div>
            <div class="testi-grid">                
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">"Qui có tư duy logic rất tốt, đặc biệt khi xử lý các vấn đề. Cậu ấy luôn là người bình tĩnh nhất nhóm khi hệ thống gặp lỗi."</p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #e74c3c; color: white;">Đ</div>
                        <div class="author-info"><span class="author-name">Nguyễn Ngọc Đầy</span><span class="author-role">Bạn cùng nhóm Đồ án</span></div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">"Qui là một học sinh luôn tìm kiếm công nghệ mới. Thái độ nghiêm túc và sự tò mò khoa học của em là tố chất của một kỹ sư giỏi."</p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #8e44ad; color: white;">T</div>
                        <div class="author-info"><span class="author-name">Th.S Nguyễn Thanh Phong</span><span class="author-role">GV Hướng dẫn DACN</span></div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">"Qui không chỉ code phần của mình mà còn hỗ trợ review code cho cả nhóm để đảm bảo mọi thứ chạy mượt mà."</p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #3498db; color: white;">P</div>
                        <div class="author-info"><span class="author-name">Huỳnh Minh Phú</span><span class="author-role">Bạn cùng lớp</span></div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">"Tôi ấn tượng với cách Qui tiếp nhận góp ý. Cậu ấy không bao giờ tự ái mà luôn coi feedback là cơ hội để nâng cấp bản thân và hoàn thiện sản phẩm."</p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #9b59b6; color: white;">M</div>
                        <div class="author-info"><span class="author-name">Vũ Thanh Minh</span><span class="author-role">Bạn cùng lớp</span></div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">"Qui là người tạo không khí rất tốt. Sự điềm đạm nhưng hóm hỉnh của cậu ấy giúp cả nhóm giảm bớt căng thẳng trong những ngày chạy deadline."</p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #e67e22; color: white;">Đ</div>
                        <div class="author-info"><span class="author-name">Hoàng Tiến Đạt</span><span class="author-role">Bạn cùng lớp</span></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>