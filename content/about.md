---
date: 2025-12-10
draft: false
hidemeta: true
---
<style>
/* 1. Cấu hình khung chung */
.about-wrapper {
    max-width: 800px;
    margin: 0 auto;
    padding-top: 20px;
    font-family: sans-serif;
}

/* 2. Phần Ảnh (Nằm trên cùng) */
.about-image {
    position: relative;
    display: flex;
    justify-content: center;
    margin-bottom: 40px;
}

.my-photo {
    width: 160px;
    height: 160px;
    border-radius: 50%; /* Bo tròn ảnh đại diện */
    object-fit: cover;
    border: 4px solid var(--primary);
    box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    z-index: 2;
    transition: transform 0.3s ease;
}

.my-photo:hover {
    transform: scale(1.05);
}

/* 3. Phần Chữ */
.about-text {
    text-align: center;
}

.main-name {
    font-size: 2.2rem;
    font-weight: 800;
    margin-bottom: 5px;
    color: var(--primary);
}

.sub-title {
    font-size: 1rem;
    color: var(--secondary);
    font-weight: 500;
    margin-bottom: 30px;
    letter-spacing: 1px;
    text-transform: uppercase;
}

.intro-block {
    background: var(--entry);
    padding: 30px;
    border-radius: 15px;
    border: 1px solid var(--border);
    text-align: justify; /* Căn đều 2 bên cho đẹp mắt với văn bản dài */
    margin-bottom: 30px;
    line-height: 1.8;
    color: var(--primary);
}

.intro-block p {
    margin-bottom: 15px; /* Khoảng cách giữa các đoạn văn */
}

.intro-block strong {
    color: var(--primary);
    font-weight: bold;
}

.intro-block em {
    font-style: italic;
    color: var(--secondary);
}

/* 4. Tech Stack */
.tech-container {
    margin-bottom: 40px;
}

.tech-header {
    font-weight: bold;
    margin-bottom: 15px;
    display: inline-block;
    border-bottom: 2px solid var(--primary);
    text-transform: uppercase;
}

.tech-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
}

.tech-badge {
    background: var(--theme);
    border: 1px solid var(--border);
    padding: 8px 16px;
    border-radius: 50px;
    font-size: 0.9rem;
    font-weight: 600;
    transition: all 0.2s;
}

.tech-badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

/* Màu sắc riêng cho từng công nghệ */
.badge-java { color: #e74c3c; border-color: #e74c3c; } 
.badge-socket { color: #3498db; border-color: #3498db; } 
.badge-js { color: #f1c40f; border-color: #f1c40f; } 

/* 5. Footer liên hệ */
.contact-links {
    margin-top: 20px;
    display: flex;
    justify-content: center;
    gap: 20px;
}

.contact-links a {
    text-decoration: none;
    font-weight: bold;
    color: var(--primary);
    padding: 10px 20px;
    border: 1px solid var(--border);
    border-radius: 8px;
    transition: background 0.3s;
}

.contact-links a:hover {
    background: var(--entry);
}
/* --- PHẦN MỚI: TESTIMONIALS (ĐÁNH GIÁ) --- */
.testimonials-section {
    margin-top: 50px;
    text-align: left;
}
.testi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}
.testi-card {
    background: var(--entry);
    padding: 20px;
    border-radius: 12px;
    border: 1px solid var(--border);
    position: relative;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}
.quote-icon {
    font-size: 2rem;
    color: var(--secondary);
    opacity: 0.3;
    position: absolute;
    top: 10px;
    left: 15px;
    font-family: serif;
}
.testi-content {
    font-style: italic;
    font-size: 0.95rem;
    margin-top: 15px;
    margin-bottom: 15px;
    color: var(--primary);
    line-height: 1.6;
}
.testi-author {
    display: flex;
    align-items: center;
    gap: 10px;
    border-top: 1px solid var(--border);
    padding-top: 10px;
}
.author-avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #ddd; /* Màu nền tạm nếu không có ảnh */
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    color: #555;
    font-size: 14px;
}
.author-info {
    display: flex;
    flex-direction: column;
}
.author-name {
    font-weight: bold;
    font-size: 0.9rem;
}
.author-role {
    font-size: 0.8rem;
    color: var(--secondary);
}
</style>

<div class="about-wrapper">
    <div class="about-image">
        <img src="/anhtrangchu.jpg" class="my-photo" alt="Avatar">
    </div>   
    <div class="about-text">
        <div class="main-name">Nguyễn Đức Qui</div>
        <div class="sub-title">Kỹ sư Công nghệ Thông tin (Tương lai)</div>        
        <div class="intro-block">
            <p>Tên tôi là <strong>Đức Qui</strong>. Nếu như "Đức" đại diện cho sự tử tế trong đạo đức nghề nghiệp, thì "Qui" gợi nhắc tôi về sự <strong>Quy chuẩn</strong> và <strong>Kiên định</strong> – những yếu tố cốt lõi của một hệ thống mạng vững chắc. Tôi luôn mong muốn sống và làm việc đúng như tên mình: xây dựng những giải pháp công nghệ không chỉ hoạt động tốt mà còn phải chuẩn mực, minh bạch và đáng tin cậy. Sắp hoàn thành chương trình đại học, tôi đã sẵn sàng "Online", tự tin kết nối và truyền tải giá trị của mình vào thế giới công nghệ rộng lớn.</p>
            <p></p>
            <p>Niềm đam mê với những dòng mã (code) của tôi bắt đầu từ thời trung học, khi tôi lần đầu tiên tò mò về cách hai chiếc máy tính có thể "trò chuyện" với nhau qua mạng. Sự tò mò ấy đã thôi thúc tôi theo đuổi tấm bằng <strong>Kỹ sư Công nghệ thông tin</strong> (chuyên ngành Mạng & Truyền thông).</p>
            <p></p>
            <p>Từ đó, tôi luôn nỗ lực hết mình để không chỉ nắm vững lý thuyết mà còn làm chủ công nghệ thực tế. Tôi chủ động tham gia các dự án cá nhân (như blog bạn đang xem), nghiên cứu sâu về <strong>Java Core, Socket và JavaScript</strong>, nhằm mở rộng kiến thức và mài giũa tư duy logic của bản thân.</p>
            <p></p>
            <p>Trong công việc, tôi tin vào triết lý <em>"Talk is cheap, show me the code"</em> (Nói ít, làm nhiều). Tôi muốn khẳng định bản thân bằng chất lượng sản phẩm và những dòng code sạch (clean code) hơn là lời nói suông. Tôi có kinh nghiệm làm việc nhóm và thường được tin tưởng nhờ khả năng tư duy phản biện và tinh thần trách nhiệm cao. Tôi luôn hào hứng khi cùng đồng đội giải quyết các bài toán khó (bug) và tìm ra giải pháp tối ưu nhất cho hệ thống.</p>
            <p></p>
            <p>Dù thế giới số luôn vận động không ngừng, tôi vẫn trân trọng những khoảng thời gian riêng tư bên ly cà phê, nghiền ngẫm một thuật toán hay hoặc đọc sách về kiến trúc phần mềm. Sở thích của tôi là sưu tầm những công nghệ mới và những tư duy đột phá, coi đó là nhiên liệu giúp tôi tiến về phía trước.</p>
            <p></p>
            <p>Hiện tại, tôi đang tìm kiếm cơ hội tại một môi trường công nghệ năng động, chuyên nghiệp, nơi tôi có thể cống hiến tư duy logic và kỹ năng lập trình của mình. Mời bạn dành chút thời gian xem qua <strong>Danh mục đầu tư (Projects)</strong> và <strong>Hồ sơ năng lực</strong> của tôi. Đừng ngần ngại liên hệ nếu chúng ta có cùng tần số!</p>
        </div>          
        <div class="testimonials-section">
            <div class="tech-header" style="width: 100%; text-align: center; border: none;">💬 GÓC NHÌN TỪ ĐỒNG ĐỘI</div>
            <div class="testi-grid">               
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">
                        "Qui có tư duy logic rất tốt, đặc biệt khi xử lý các vấn đề. Cậu ấy luôn là người bình tĩnh nhất nhóm khi hệ thống gặp lỗi."
                    </p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #e74c3c; color: white;">Đ</div>
                        <div class="author-info">
                            <span class="author-name">Nguyễn Ngọc Đầy</span>
                            <span class="author-role">Bạn cùng nhóm Đồ án</span>
                        </div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">
                        "Qui là một học sinh luôn tìm kiếm công nghệ mới. Thái độ nghiêm túc và sự tò mò khoa học của em là tố chất của một kỹ sư giỏi."
                    </p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #8e44ad;">T</div>
                        <div class="author-info">
                            <span class="author-name">Th.S Nguyễn Thanh Phong</span>
                            <span class="author-role">GV Hướng dẫn DACN</span>
                        </div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">
                        "Qui không chỉ code phần của mình mà còn hỗ trợ review code cho cả nhóm để đảm bảo mọi thứ chạy mượt mà."
                    </p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #3498db; color: white;">Phú</div>
                        <div class="author-info">
                            <span class="author-name">Huỳnh Minh Phú</span>
                            <span class="author-role">Bạn cùng lớp</span>
                        </div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">
                        "Tôi ấn tượng với cách Qui tiếp nhận góp ý. Cậu ấy không bao giờ tự ái mà luôn coi feedback là cơ hội để nâng cấp bản thân và hoàn thiện sản phẩm."
                    </p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #9b59b6;">M</div>
                        <div class="author-info">
                            <span class="author-name">Vũ Thanh Minh</span>
                            <span class="author-role">Bạn cùng lớp</span>
                        </div>
                    </div>
                </div>
                <div class="testi-card">
                    <div class="quote-icon">❝</div>
                    <p class="testi-content">
                        "Qui là người tạo không khí rất tốt. Sự điềm đạm nhưng hóm hỉnh của cậu ấy giúp cả nhóm giảm bớt căng thẳng trong những ngày chạy deadline."
                    </p>
                    <div class="testi-author">
                        <div class="author-avatar" style="background: #e67e22;">D</div>
                        <div class="author-info">
                            <span class="author-name">Hoàng Tiến Đạt</span>
                            <span class="author-role">Bạn cùng lớp</span>
                        </div>
                    </div>
                </div>
            </div>
    </div>
</div>