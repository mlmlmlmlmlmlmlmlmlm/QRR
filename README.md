<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QR Сабақ Қатысу Жүйесі - Кеңейтілген</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <script src="https://unpkg.com/html5-qrcode"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        .header {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            border: 5px solid #1a2980;
            position: relative;
        }

        .header h1 {
            color: #1a2980;
            font-size: 2.5rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
        }

        .header-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: #ff7e5f;
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.9rem;
        }

        /* Dashboard Grid */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .dashboard-card {
            background: white;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .dashboard-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }

        .card-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f0f0f0;
        }

        .card-header h3 {
            color: #1a2980;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: #ff7e5f;
            text-align: center;
            margin: 20px 0;
        }

        /* Course Management */
        .course-management {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .course-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .course-item {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 15px;
            border: 2px solid #e0e0e0;
            cursor: pointer;
            transition: all 0.3s;
        }

        .course-item.active {
            border-color: #4CAF50;
            background: #e8f5e9;
        }

        .course-item:hover {
            transform: translateY(-5px);
        }

        /* Schedule */
        .schedule-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .schedule-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .schedule-item {
            background: #f0f7ff;
            padding: 15px;
            border-radius: 12px;
            border-left: 4px solid #1a2980;
        }

        .schedule-time {
            font-weight: bold;
            color: #1a2980;
            margin-bottom: 5px;
        }

        /* Reports */
        .reports-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .report-actions {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        /* Analytics */
        .analytics-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .chart-container {
            height: 300px;
            margin-top: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #f8f9fa;
            border-radius: 15px;
            overflow: hidden;
        }

        /* Timer */
        .timer-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .timer-display {
            font-size: 4rem;
            font-weight: bold;
            color: #1a2980;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
        }

        /* Announcements */
        .announcements-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .announcement-form {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
        }

        /* Polls */
        .polls-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
        }

        .poll-option {
            background: #f0f7ff;
            padding: 15px;
            border-radius: 12px;
            margin: 10px 0;
            cursor: pointer;
            transition: all 0.3s;
        }

        .poll-option:hover {
            background: #e3f2fd;
        }

        /* Buttons */
        .btn {
            padding: 15px 25px;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin: 5px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
        }

        .btn-success {
            background: linear-gradient(135deg, #4CAF50, #2E7D32);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(135deg, #ff9800, #ff5722);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(135deg, #f44336, #c62828);
            color: white;
        }

        .btn-info {
            background: linear-gradient(135deg, #2196F3, #0D47A1);
            color: white;
        }

        .btn:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .btn:disabled {
            background: #cccccc;
            cursor: not-allowed;
            transform: none !important;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
            background: white;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .tab-btn {
            padding: 15px 25px;
            background: #f0f0f0;
            border: none;
            border-radius: 12px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .tab-btn.active {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: white;
            padding: 40px;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .schedule-grid {
                grid-template-columns: 1fr;
            }
            
            .course-list {
                grid-template-columns: 1fr;
            }
            
            .btn, .tab-btn {
                width: 100%;
                justify-content: center;
            }
        }

        /* Badges */
        .badge {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            margin-left: 10px;
        }

        .badge-success {
            background: #e8f5e9;
            color: #2e7d32;
        }

        .badge-warning {
            background: #fff8e1;
            color: #ff8f00;
        }

        .badge-danger {
            background: #ffebee;
            color: #c62828;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>
                <i class="fas fa-chalkboard-teacher"></i>
                QR САБАҚ БАСҚАРУ ЖҮЙЕСІ
            </h1>
            <p>Мұғалімдерге арналған кеңейтілген платформа</p>
            <div class="header-badge">
                <i class="fas fa-star"></i> КЕҢЕЙТІЛГЕН НҰСҚА
            </div>
        </div>

        <!-- Tabs -->
        <div class="tabs">
            <button class="tab-btn active" data-tab="dashboard">
                <i class="fas fa-tachometer-alt"></i> Басқару тақтасы
            </button>
            <button class="tab-btn" data-tab="attendance">
                <i class="fas fa-users"></i> Қатысу бақылауы
            </button>
            <button class="tab-btn" data-tab="courses">
                <i class="fas fa-book"></i> Пәндер мен сабақтар
            </button>
            <button class="tab-btn" data-tab="materials">
                <i class="fas fa-file-upload"></i> Материалдар
            </button>
            <button class="tab-btn" data-tab="analytics">
                <i class="fas fa-chart-bar"></i> Статистика
            </button>
            <button class="tab-btn" data-tab="tools">
                <i class="fas fa-tools"></i> Құралдар
            </button>
        </div>

        <!-- Dashboard Tab -->
        <div id="dashboard" class="tab-content active">
            <div class="dashboard-grid">
                <div class="dashboard-card">
                    <div class="card-header">
                        <h3><i class="fas fa-users"></i> Бүгінгі қатысушылар</h3>
                    </div>
                    <div class="card-value" id="todayAttendance">0</div>
                    <div style="text-align: center; color: #666;">Сабаққа қатысқан оқушылар</div>
                </div>

                <div class="dashboard-card">
                    <div class="card-header">
                        <h3><i class="fas fa-calendar-alt"></i> Белсенді пәндер</h3>
                    </div>
                    <div class="card-value" id="activeCourses">0</div>
                    <div style="text-align: center; color: #666;">Белсенді сабақтар саны</div>
                </div>

                <div class="dashboard-card">
                    <div class="card-header">
                        <h3><i class="fas fa-clock"></i> Орташа кешігу</h3>
                    </div>
                    <div class="card-value" id="avgDelay">0мин</div>
                    <div style="text-align: center; color: #666;">Орташа кешігу уақыты</div>
                </div>

                <div class="dashboard-card">
                    <div class="card-header">
                        <h3><i class="fas fa-percentage"></i> Қатысу пайызы</h3>
                    </div>
                    <div class="card-value" id="attendanceRate">0%</div>
                    <div style="text-align: center; color: #666;">Жалпы қатысу деңгейі</div>
                </div>
            </div>

            <!-- Quick Actions -->
            <div class="dashboard-card" style="margin-top: 30px;">
                <div class="card-header">
                    <h3><i class="fas fa-bolt"></i> Жедел әрекеттер</h3>
                </div>
                <div style="display: flex; gap: 15px; flex-wrap: wrap; margin-top: 20px;">
                    <button class="btn btn-primary" id="quickStartQR">
                        <i class="fas fa-qrcode"></i> QR кодты бастау
                    </button>
                    <button class="btn btn-success" id="quickAnnouncement">
                        <i class="fas fa-bullhorn"></i> Хабарлама жіберу
                    </button>
                    <button class="btn btn-warning" id="quickPoll">
                        <i class="fas fa-poll"></i> Жедел сауалнама
                    </button>
                    <button class="btn btn-info" id="quickReport">
                        <i class="fas fa-download"></i> Есепті жүктеу
                    </button>
                </div>
            </div>

            <!-- Today's Schedule -->
            <div class="schedule-container">
                <div class="card-header">
                    <h3><i class="fas fa-calendar-day"></i> Бүгінгі кесте</h3>
                    <button class="btn btn-primary" id="addScheduleBtn">
                        <i class="fas fa-plus"></i> Қосу
                    </button>
                </div>
                <div class="schedule-grid" id="todaySchedule">
                    <!-- Schedule items will be added here -->
                </div>
            </div>
        </div>

        <!-- Attendance Tab -->
        <div id="attendance" class="tab-content">
            <div class="dashboard-card">
                <div class="card-header">
                    <h3><i class="fas fa-qrcode"></i> QR кодты басқару</h3>
                </div>
                <div style="text-align: center; margin: 30px 0;">
                    <div id="qrcode" style="display: inline-block; margin: 20px 0;"></div>
                    <div class="token-display" style="font-size: 2rem; margin: 20px 0;">
                        <span id="currentToken">ТОКЕН ЖОҚ</span>
                    </div>
                    <div style="display: flex; gap: 15px; justify-content: center; flex-wrap: wrap;">
                        <button class="btn btn-success" id="startQRBtn">
                            <i class="fas fa-play"></i> QR кодты бастау
                        </button>
                        <button class="btn btn-danger" id="stopQRBtn" disabled>
                            <i class="fas fa-stop"></i> Тоқтату
                        </button>
                        <button class="btn btn-warning" id="newTokenBtn">
                            <i class="fas fa-sync"></i> Жаңа токен
                        </button>
                    </div>
                </div>
            </div>

            <!-- Attendance Table -->
            <div class="dashboard-card" style="margin-top: 30px;">
                <div class="card-header">
                    <h3><i class="fas fa-list"></i> Қатысушылар тізімі</h3>
                    <div>
                        <button class="btn btn-info" id="exportAttendance">
                            <i class="fas fa-file-excel"></i> Excel-ге экспорттау
                        </button>
                        <button class="btn btn-warning" id="filterAttendance">
                            <i class="fas fa-filter"></i> Сүзгілеу
                            </button>
                    </div>
                </div>
                <div style="overflow-x: auto; margin-top: 20px;">
                    <table style="width: 100%; border-collapse: collapse;">
                        <thead style="background: linear-gradient(135deg, #1a2980, #26d0ce); color: white;">
                            <tr>
                                <th style="padding: 15px; text-align: left;">Оқушы аты</th>
                                <th style="padding: 15px; text-align: left;">Пән</th>
                                <th style="padding: 15px; text-align: left;">Күні</th>
                                <th style="padding: 15px; text-align: left;">Уақыты</th>
                                <th style="padding: 15px; text-align: left;">Күйі</th>
                            </tr>
                        </thead>
                        <tbody id="attendanceTable">
                            <!-- Attendance data will be here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Courses Tab -->
        <div id="courses" class="tab-content">
            <div class="course-management">
                <div class="card-header">
                    <h3><i class="fas fa-book-open"></i> Пәндер мен сабақтар</h3>
                    <button class="btn btn-success" id="addCourseBtn">
                        <i class="fas fa-plus"></i> Жаңа пән қосу
                    </button>
                </div>
                
                <div class="course-list" id="courseList">
                    <!-- Courses will be added here -->
                </div>

                <!-- Course Details -->
                <div id="courseDetails" style="display: none; margin-top: 30px;">
                    <div class="card-header">
                        <h3 id="courseTitle">Пән атауы</h3>
                        <button class="btn btn-primary" id="startClassBtn">
                            <i class="fas fa-play"></i> Сабақты бастау
                        </button>
                    </div>
                    
                    <div style="margin-top: 20px;">
                        <h4 style="color: #1a2980; margin-bottom: 15px;">
                            <i class="fas fa-users"></i> Пәннің оқушылары
                        </h4>
                        <div id="courseStudents" style="display: flex; flex-wrap: wrap; gap: 10px;">
                            <!-- Students will be added here -->
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Materials Tab -->
        <div id="materials" class="tab-content">
            <div class="dashboard-card">
                <div class="card-header">
                    <h3><i class="fas fa-cloud-upload-alt"></i> Материалдарды жүктеу</h3>
                </div>
                <div style="margin-top: 20px;">
                    <input type="file" id="materialFile" multiple style="display: none;">
                    <button class="btn btn-primary" onclick="document.getElementById('materialFile').click()">
                        <i class="fas fa-folder-open"></i> Файлдарды таңдау
                    </button>
                    <button class="btn btn-success" id="uploadMaterialBtn">
                        <i class="fas fa-upload"></i> Жүктеу
                    </button>
                    
                    <div style="margin-top: 20px;">
                        <label>Пән:</label>
                        <select id="materialCourse" style="padding: 10px; border-radius: 8px; margin-left: 10px;">
                            <option value="all">Барлық пәндер</option>
                        </select>
                    </div>
                </div>
            </div>

            <!-- Materials List -->
            <div class="dashboard-card" style="margin-top: 30px;">
                <div class="card-header">
                    <h3><i class="fas fa-folder"></i> Жүктелген материалдар</h3>
                </div>
                <div id="materialsList" style="margin-top: 20px;">
                    <!-- Materials will be listed here -->
                </div>
            </div>
        </div>

        <!-- Analytics Tab -->
        <div id="analytics" class="tab-content">
            <div class="analytics-container">
                <div class="card-header">
                    <h3><i class="fas fa-chart-line"></i> Статистикалық талдау</h3>
                    <select id="analyticsPeriod" style="padding: 10px; border-radius: 8px;">
                        <option value="week">Соңғы апта</option>
                        <option value="month">Соңғы ай</option>
                        <option value="semester">Семестр</option>
                    </select>
                </div>
                
                <div class="dashboard-grid" style="margin-top: 30px;">
                    <div class="dashboard-card">
                        <h4 style="color: #1a2980; margin-bottom: 15px;">
                            <i class="fas fa-chart-bar"></i> Қатысу тенденциясы
                        </h4>
                        <div class="chart-container">
                            <canvas id="attendanceChart" width="400" height="300"></canvas>
                        </div>
                    </div>
                    
                    <div class="dashboard-card">
                        <h4 style="color: #1a2980; margin-bottom: 15px;">
                            <i class="fas fa-chart-pie"></i> Пәндер бойынша үлес
                        </h4>
                        <div class="chart-container">
                            <canvas id="courseChart" width="400" height="300"></canvas>
                        </div>
                    </div>
                </div>

                <!-- Detailed Analytics -->
                <div class="dashboard-card" style="margin-top: 30px;">
                    <h4 style="color: #1a2980; margin-bottom: 20px;">
                        <i class="fas fa-table"></i> Егжей-тегжейлі статистика
                    </h4>
                    <div style="overflow-x: auto;">
                        <table style="width: 100%; border-collapse: collapse;">
                            <thead style="background: #f0f7ff;">
                                <tr>
                                    <th style="padding: 12px; text-align: left;">Оқушы</th>
                                    <th style="padding: 12px; text-align: left;">Қатысу %</th>
                                    <th style="padding: 12px; text-align: left;">Орташа кешігу</th>
                                    <th style="padding: 12px; text-align: left;">Белсенділік</th>
                                </tr>
                            </thead>
                            <tbody id="analyticsTable">
                                <!-- Analytics data will be here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- Tools Tab -->
        <div id="tools" class="tab-content">
            <!-- Timer Tool -->
            <div class="timer-container">
                <div class="card-header">
                    <h3><i class="fas fa-stopwatch"></i> Сабақ таймері</h3>
                </div>
                <div class="timer-display" id="timerDisplay">45:00</div>
                <div style="display: flex; gap: 15px; justify-content: center; flex-wrap: wrap;">
                    <button class="btn btn-success" id="startTimerBtn">
                        <i class="fas fa-play"></i> Бастау
                    </button>
                    <button class="btn btn-danger" id="stopTimerBtn" disabled>
                        <i class="fas fa-stop"></i> Тоқтату
                    </button>
                    <button class="btn btn-warning" id="resetTimerBtn">
                        <i class="fas fa-redo"></i> Қалпына келтіру
                    </button>
                </div>
                
                <div style="margin-top: 30px;">
                    <label>Таймер уақыты (минут):</label>
                    <input type="number" id="timerMinutes" value="45" min="1" max="120" 
                           style="padding: 10px; border-radius: 8px; width: 80px; margin-left: 10px;">
                </div>
            </div>

            <!-- Announcements Tool -->
            <div class="announcements-container" style="margin-top: 30px;">
                <div class="card-header">
                    <h3><i class="fas fa-bullhorn"></i> Хабарламалар</h3>
                </div>
                <div class="announcement-form">
                    <textarea id="announcementText" placeholder="Хабарлама мәтінін енгізіңіз..." 
                              style="width: 100%; padding: 15px; border-radius: 10px; border: 2px solid #ddd; min-height: 100px;"></textarea>
                    <div style="margin-top: 15px; display: flex; gap: 15px; flex-wrap: wrap;">
                        <button class="btn btn-primary" id="sendAnnouncementBtn">
                            <i class="fas fa-paper-plane"></i> Жіберу
                        </button>
                        <button class="btn btn-success" id="scheduleAnnouncementBtn">
                            <i class="fas fa-clock"></i> Уақыттау
                        </button>
                    </div>
                </div>
                
                <div style="margin-top: 30px;">
                    <h4 style="color: #1a2980; margin-bottom: 15px;">
                        <i class="fas fa-history"></i> Соңғы хабарламалар
                    </h4>
                    <div id="announcementsList">
                        <!-- Announcements will be listed here -->
                    </div>
                </div>
            </div>

            <!-- Polls Tool -->
            <div class="polls-container" style="margin-top: 30px;">
                <div class="card-header">
                    <h3><i class="fas fa-poll"></i> Сауалнамалар</h3>
                    <button class="btn btn-success" id="createPollBtn">
                        <i class="fas fa-plus"></i> Жаңа сауалнама
                    </button>
                </div>
                
                <div id="pollForm" style="display: none; margin-top: 20px; background: #f8f9fa; padding: 20px; border-radius: 15px;">
                    <input type="text" id="pollQuestion" placeholder="Сұрақ..." 
                           style="width: 100%; padding: 15px; border-radius: 10px; border: 2px solid #ddd; margin-bottom: 15px;">
                    
                    <div id="pollOptions">
                        <input type="text" class="poll-option-input" placeholder="1-нұсқа" 
                               style="width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 10px;">
                        <input type="text" class="poll-option-input" placeholder="2-нұсқа" 
                               style="width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 10px;">
                    </div>
                    
                    <button class="btn btn-warning" id="addOptionBtn" style="margin-top: 10px;">
                        <i class="fas fa-plus"></i> Нұсқа қосу
                    </button>
                    
                    <div style="margin-top: 20px; display: flex; gap: 15px;">
                        <button class="btn btn-success" id="savePollBtn">
                            <i class="fas fa-save"></i> Сақтау
                        </button>
                        <button class="btn btn-danger" id="cancelPollBtn">
                            <i class="fas fa-times"></i> Бас тарту
                        </button>
                    </div>
                </div>
                
                <div id="pollsList" style="margin-top: 30px;">
                    <!-- Polls will be listed here -->
                </div>
            </div>
        </div>

        <!-- Modals -->
        <div id="courseModal" class="modal">
            <div class="modal-content">
                <h3 style="color: #1a2980; margin-bottom: 20px;">
                    <i class="fas fa-book"></i> Жаңа пән қосу
                </h3>
                <input type="text" id="courseName" placeholder="Пән атауы" 
                       style="width: 100%; padding: 15px; border-radius: 10px; border: 2px solid #ddd; margin-bottom: 15px;">
                <input type="text" id="courseCode" placeholder="Пән коды" 
                       style="width: 100%; padding: 15px; border-radius: 10px; border: 2px solid #ddd; margin-bottom: 15px;">
                <textarea id="courseDescription" placeholder="Сипаттама" 
                          style="width: 100%; padding: 15px; border-radius: 10px; border: 2px solid #ddd; min-height: 100px; margin-bottom: 20px;"></textarea>
                <div style="display: flex; gap: 15px;">
                    <button class="btn btn-success" id="saveCourseBtn">
                        <i class="fas fa-save"></i> Сақтау
                    </button>
                    <button class="btn btn-danger" id="closeCourseModalBtn">
                        <i class="fas fa-times"></i> Бас тарту
                    </button>
                </div>
            </div>
        </div>

        <div id="scheduleModal" class="modal">
            <div class="modal-content">
                <h3 style="color: #1a2980; margin-bottom: 20px;">
                    <i class="fas fa-calendar-plus"></i> Кестеге қосу
                </h3>
                <!-- Schedule form will be here -->
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // ============================================
        // НЕГІЗГІ АЙНЫМАЛЫЛАР
        // ============================================
        let qrcode = null;
        let tokenInterval = null;
        let currentToken = "";
        let timerInterval = null;
        let timerSeconds = 45 * 60;
        let currentCourse = null;
        let courses = [];
        let materials = [];
        let announcements = [];
        let polls = [];

        // ============================================
        // БАСТАПҚЫ БЕЛСЕНДІРУ
        // ============================================
        document.addEventListener('DOMContentLoaded', function() {
            loadAllData();
            initializeDashboard();
            setupEventListeners();
            generateInitialToken();
        });

        // ============================================
        // ДЕРЕКТЕРДІ ЖҮКТЕУ
        // ============================================
        function loadAllData() {
            // Курстарды жүктеу
            const savedCourses = localStorage.getItem('courses');
            if (savedCourses) {
                courses = JSON.parse(savedCourses);
                updateCourseList();
            }

            // Материалдарды жүктеу
            const savedMaterials = localStorage.getItem('materials');
            if (savedMaterials) {
                materials = JSON.parse(savedMaterials);
                updateMaterialsList();
            }

            // Хабарламаларды жүктеу
            const savedAnnouncements = localStorage.getItem('announcements');
            if (savedAnnouncements) {
                announcements = JSON.parse(savedAnnouncements);
                updateAnnouncementsList();
            }

            // Сауалнамаларды жүктеу
            const savedPolls = localStorage.getItem('polls');
            if (savedPolls) {
                polls = JSON.parse(savedPolls);
                updatePollsList();
            }

            // Токенді жүктеу
            const savedToken = localStorage.getItem('currentToken');
            if (savedToken) {
                currentToken = savedToken;
                document.getElementById('currentToken').textContent = currentToken;
                renderQRCode(currentToken);
            }

            // Қатысу тізімін жаңарту
            updateAttendanceTable();
            updateDashboardStats();
        }

        // ============================================
        // ТАБТАРДЫ БАСҚАРУ
        // ============================================
        function setupEventListeners() {
            // Таб түймелері
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    
                    // Барлық табтарды жабу
                    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                    document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                    
                    // Белсенді табты көрсету
                    this.classList.add('active');
                    document.getElementById(tabId).classList.add('active');
                    
                    // Таб өзгергенде деректерді жаңарту
                    if (tabId === 'dashboard') {
                        updateDashboardStats();
                    } else if (tabId === 'attendance') {
                        updateAttendanceTable();
                    } else if (tabId === 'analytics') {
                        updateCharts();
                    }
                });
            });

            // QR код түймелері
            document.getElementById('startQRBtn').addEventListener('click', startQRCodeRotation);
            document.getElementById('stopQRBtn').addEventListener('click', stopQRCodeRotation);
            document.getElementById('newTokenBtn').addEventListener('click', generateNewToken);
            document.getElementById('quickStartQR').addEventListener('click', startQRCodeRotation);

            // Курс түймелері
            document.getElementById('addCourseBtn').addEventListener('click', showCourseModal);
            document.getElementById('saveCourseBtn').addEventListener('click', saveCourse);
            document.getElementById('closeCourseModalBtn').addEventListener('click', hideCourseModal);

            // Таймер түймелері
            document.getElementById('startTimerBtn').addEventListener('click', startTimer);
            document.getElementById('stopTimerBtn').addEventListener('click', stopTimer);
            document.getElementById('resetTimerBtn').addEventListener('click', resetTimer);
            document.getElementById('timerMinutes').addEventListener('change', updateTimer);

            // Хабарлама түймелері
            document.getElementById('sendAnnouncementBtn').addEventListener('click', sendAnnouncement);
            document.getElementById('quickAnnouncement').addEventListener('click', function() {
                document.getElementById('tools').click();
                document.getElementById('announcementText').focus();
            });

            // Сауалнама түймелері
            document.getElementById('createPollBtn').addEventListener('click', showPollForm);
            document.getElementById('savePollBtn').addEventListener('click', savePoll);
            document.getElementById('cancelPollBtn').addEventListener('click', hidePollForm);
            document.getElementById('addOptionBtn').addEventListener('click', addPollOption);

            // Материалдар түймелері
            document.getElementById('uploadMaterialBtn').addEventListener('click', uploadMaterial);

            // Есеп түймелері
            document.getElementById('exportAttendance').addEventListener('click', exportToExcel);
            document.getElementById('quickReport').addEventListener('click', exportToExcel);

            // Кесте түймелері
            document.getElementById('addScheduleBtn').addEventListener('click', addScheduleItem);
        }

        // ============================================
        // БАСҚАРУ ТАҚТАСЫ
        // ============================================
        function initializeDashboard() {
            updateTodaySchedule();
            updateDashboardStats();
        }

        function updateDashboardStats() {
            // Бүгінгі қатысушылар
            const today = new Date().toLocaleDateString('kk-KZ');
            const attendance = JSON.parse(localStorage.getItem('attendance') || '[]');
            const todayAttendance = attendance.filter(a => a.date === today).length;
            document.getElementById('todayAttendance').textContent = todayAttendance;

            // Белсенді пәндер
            document.getElementById('activeCourses').textContent = courses.length;

            // Орташа кешігу (мысалдық мән)
            document.getElementById('avgDelay').textContent = '5мин';

            // Қатысу пайызы
            const totalStudents = 30; // Мысалдық мән
            const attendanceRate = Math.round((todayAttendance / totalStudents) * 100);
            document.getElementById('attendanceRate').textContent = attendanceRate + '%';
        }

        function updateTodaySchedule() {
            const scheduleContainer = document.getElementById('todaySchedule');
            const scheduleItems = [
                { time: '09:00', subject: 'Математика', room: '202' },
                { time: '10:30', subject: 'Физика', room: '305' },
                { time: '14:00', subject: 'Ағылшын тілі', room: '101' }
            ];

            scheduleContainer.innerHTML = scheduleItems.map(item => `
                <div class="schedule-item">
                    <div class="schedule-time">${item.time}</div>
                    <div style="font-weight: bold;">${item.subject}</div>
                    <div style="color: #666;">${item.room} кабинет</div>
                </div>
            `).join('');
        }

        // ============================================
        // QR КОД ЖҮЙЕСІ
        // ============================================
        function renderQRCode(text) {
            if (qrcode) {
                document.getElementById('qrcode').innerHTML = '';
            }
            
            qrcode = new QRCode(document.getElementById('qrcode'), {
                text: text,
                width: 200,
                height: 200,
                colorDark: "#1a2980",
                colorLight: "#ffffff",
                correctLevel: QRCode.CorrectLevel.H
            });
        }

        function generateNewToken() {
            const chars = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
            currentToken = '';
            for (let i = 0; i < 6; i++) {
                currentToken += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            
            document.getElementById('currentToken').textContent = currentToken;
            localStorage.setItem('currentToken', currentToken);
            renderQRCode(currentToken);
            
            showNotification('Жаңа токен жасалды!', 'success');
        }

        function generateInitialToken() {
            if (!currentToken) {
                generateNewToken();
            }
        }

        function startQRCodeRotation() {
            generateNewToken();
            
            // Интервалды орнату (60 секунд сайын)
            if (tokenInterval) clearInterval(tokenInterval);
            tokenInterval = setInterval(generateNewToken, 60000);
            
            // Түймелерді белсендіру/өшіру
            document.getElementById('startQRBtn').disabled = true;
            document.getElementById('stopQRBtn').disabled = false;
            document.getElementById('quickStartQR').disabled = true;
            
            showNotification('QR код айналдыру басталды (әр 1 минут сайын)', 'success');
        }

        function stopQRCodeRotation() {
            if (tokenInterval) {
                clearInterval(tokenInterval);
                tokenInterval = null;
                
                // Түймелерді белсендіру/өшіру
                document.getElementById('startQRBtn').disabled = false;
                document.getElementById('stopQRBtn').disabled = true;
                document.getElementById('quickStartQR').disabled = false;
                
                showNotification('QR код айналдыру тоқтатылды', 'info');
            }
        }

        // ============================================
        // ПӘНДЕРДІ БАСҚАРУ
        // ============================================
        function showCourseModal() {
            document.getElementById('courseModal').style.display = 'flex';
        }

        function hideCourseModal() {
            document.getElementById('courseModal').style.display = 'none';
        }

        function saveCourse() {
            const name = document.getElementById('courseName').value.trim();
            const code = document.getElementById('courseCode').value.trim();
            const description = document.getElementById('courseDescription').value.trim();
            
            if (!name) {
                showNotification('Пән атауын енгізіңіз!', 'error');
                return;
            }
            
            const newCourse = {
                id: Date.now(),
                name: name,
                code: code,
                description: description,
                students: [],
                createdAt: new Date().toISOString()
            };
            
            courses.push(newCourse);
            localStorage.setItem('courses', JSON.stringify(courses));
            
            updateCourseList();
            hideCourseModal();
            
            // Өрістерді тазарту
            document.getElementById('courseName').value = '';
            document.getElementById('courseCode').value = '';
            document.getElementById('courseDescription').value = '';
            
            showNotification('Пән сәтті қосылды!', 'success');
        }

        function updateCourseList() {
            const courseList = document.getElementById('courseList');
            
            if (courses.length === 0) {
                courseList.innerHTML = `
                    <div style="grid-column: 1 / -1; text-align: center; padding: 40px; color: #666;">
                        <i class="fas fa-book" style="font-size: 3rem; margin-bottom: 20px; display: block; color: #ccc;"></i>
                        ӘЛІ ПӘН ҚОСЫЛМАҒАН
                        <p style="margin-top: 10px; font-size: 0.9rem;">Жаңа пән қосу үшін жоғарыдағы түймені басыңыз</p>
                    </div>
                `;
                return;
            }
            
            courseList.innerHTML = courses.map(course => `
                <div class="course-item" data-course-id="${course.id}">
                    <div style="font-weight: bold; color: #1a2980; margin-bottom: 5px;">${course.name}</div>
                    <div style="color: #666; font-size: 0.9rem; margin-bottom: 10px;">${course.code}</div>
                    <div style="color: #888; font-size: 0.85rem;">${course.students.length} оқушы</div>
                </div>
            `).join('');
            
            // Курсты таңдау оқиғасын қосу
            document.querySelectorAll('.course-item').forEach(item => {
                item.addEventListener('click', function() {
                    const courseId = parseInt(this.getAttribute('data-course-id'));
                    selectCourse(courseId);
                });
            });
        }

        function selectCourse(courseId) {
            currentCourse = courses.find(c => c.id === courseId);
            
            // Барлық курс элементтерінен актив класын алып тастау
            document.querySelectorAll('.course-item').forEach(item => {
                item.classList.remove('active');
            });
            
            // Таңдалған курсты белсенді ету
            const selectedItem = document.querySelector(`[data-course-id="${courseId}"]`);
            if (selectedItem) {
                selectedItem.classList.add('active');
            }
            
            // Курс мәліметтерін көрсету
            document.getElementById('courseDetails').style.display = 'block';
            document.getElementById('courseTitle').textContent = currentCourse.name;
            
            // Оқушылар тізімін жаңарту
            updateCourseStudents();
        }

        function updateCourseStudents() {
            if (!currentCourse) return;
            
            const studentsContainer = document.getElementById('courseStudents');
            
            if (currentCourse.students.length === 0) {
                studentsContainer.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666; width: 100%;">
                        Оқушылар қосылмаған
                    </div>
                `;
                return;
            }
            
            studentsContainer.innerHTML = currentCourse.students.map(student => `
                <div style="background: #e3f2fd; padding: 10px 15px; border-radius: 20px; display: flex; align-items: center; gap: 10px;">
                    <i class="fas fa-user"></i>
                    ${student}
                </div>
            `).join('');
        }

        // ============================================
        // ҚАТЫСУ ТІЗІМІ
        // ============================================
        function updateAttendanceTable() {
            const attendance = JSON.parse(localStorage.getItem('attendance') || '[]');
            const tableBody = document.getElementById('attendanceTable');
            
            if (attendance.length === 0) {
                tableBody.innerHTML = `
                    <tr>
                        <td colspan="5" style="text-align: center; padding: 50px; color: #666;">
                            <i class="fas fa-users-slash" style="font-size: 2rem; margin-bottom: 20px; display: block; color: #ccc;"></i>
                            ӘЛІ ҚАТЫСУ ЖОҚ
                        </td>
                    </tr>
                `;
                return;
            }
            
            // Соңғы 50 тіркеуді көрсету
            const recentAttendance = attendance.slice(-50).reverse();
            
            tableBody.innerHTML = recentAttendance.map(record => `
                <tr style="border-bottom: 1px solid #eee;">
                    <td style="padding: 12px;">${record.name || 'Белгісіз'}</td>
                    <td style="padding: 12px;">${record.course || 'Пәнсіз'}</td>
                    <td style="padding: 12px;">${record.date || 'Белгісіз'}</td>
                    <td style="padding: 12px;">${record.time || 'Белгісіз'}</td>
                    <td style="padding: 12px;">
                        <span class="badge badge-success">ҚАТЫСТЫ</span>
                    </td>
                </tr>
            `).join('');
        }

        // ============================================
        // МАТЕРИАЛДАР
        // ============================================
        function uploadMaterial() {
            const fileInput = document.getElementById('materialFile');
            const course = document.getElementById('materialCourse').value;
            
            if (fileInput.files.length === 0) {
                showNotification('Алдымен файл таңдаңыз!', 'error');
                return;
            }
            
            // Әрбір файлды өңдеу
            Array.from(fileInput.files).forEach(file => {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    const newMaterial = {
                        id: Date.now(),
                        name: file.name,
                        size: formatFileSize(file.size),
                        type: file.type,
                        course: course,
                        url: e.target.result,
                        uploadedAt: new Date().toLocaleString('kk-KZ')
                    };
                    
                    materials.push(newMaterial);
                    localStorage.setItem('materials', JSON.stringify(materials));
                    
                    updateMaterialsList();
                    showNotification(`${file.name} жүктелді!`, 'success');
                };
                
                reader.readAsDataURL(file);
            });
            
            // Файл өрісін тазарту
            fileInput.value = '';
        }

        function updateMaterialsList() {
            const materialsList = document.getElementById('materialsList');
            
            if (materials.length === 0) {
                materialsList.innerHTML = `
                    <div style="text-align: center; padding: 30px; color: #666;">
                        <i class="fas fa-file-alt" style="font-size: 2rem; margin-bottom: 15px; display: block; color: #ccc;"></i>
                        ӘЛІ МАТЕРИАЛ ЖОҚ
                    </div>
                `;
                return;
            }
            
            // Соңғы 10 материалды көрсету
            const recentMaterials = materials.slice(-10).reverse();
            
            materialsList.innerHTML = recentMaterials.map(material => `
                <div style="background: #f8f9fa; padding: 15px; border-radius: 12px; margin-bottom: 10px; display: flex; align-items: center; justify-content: space-between;">
                    <div>
                        <div style="font-weight: bold; color: #1a2980;">
                            <i class="fas fa-file"></i> ${material.name}
                        </div>
                        <div style="color: #666; font-size: 0.9rem; margin-top: 5px;">
                            ${material.course} | ${material.size} | ${material.uploadedAt}
                        </div>
                    </div>
                    <a href="${material.url}" download="${material.name}" class="btn btn-primary" style="padding: 8px 15px; font-size: 0.9rem;">
                        <i class="fas fa-download"></i>
                    </a>
                </div>
            `).join('');
        }

        // ============================================
        // СТАТИСТИКА ЖӘНЕ ГРАФИКТЕР
        // ============================================
        function updateCharts() {
            // Қатысу графигі
            const attendanceCtx = document.getElementById('attendanceChart').getContext('2d');
            new Chart(attendanceCtx, {
                type: 'line',
                data: {
                    labels: ['Дүй.', 'Сей.', 'Сәр.', 'Бей.', 'Жұм.', 'Сен.', 'Жек.'],
                    datasets: [{
                        label: 'Қатысушылар саны',
                        data: [25, 28, 30, 22, 27, 24, 29],
                        borderColor: '#1a2980',
                        backgroundColor: 'rgba(26, 41, 128, 0.1)',
                        tension: 0.4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false
                }
            });

            // Пәндер бойынша үлес
            const courseCtx = document.getElementById('courseChart').getContext('2d');
            new Chart(courseCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Математика', 'Физика', 'Ағылшын', 'Тарих', 'Биология'],
                    datasets: [{
                        data: [30, 25, 20, 15, 10],
                        backgroundColor: ['#1a2980', '#26d0ce', '#4CAF50', '#ff9800', '#f44336']
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false
                }
            });

            // Статистика кестесін жаңарту
            updateAnalyticsTable();
        }

        function updateAnalyticsTable() {
            const analyticsTable = document.getElementById('analyticsTable');
            
            // Мысалдық деректер
            const analyticsData = [
                { student: 'Әлия Нұрғалиева', attendance: 95, delay: '3мин', activity: 'Жоғары' },
                { student: 'Бекзат Серік', attendance: 88, delay: '7мин', activity: 'Орташа' },
                { student: 'Гүлмира Асан', attendance: 92, delay: '2мин', activity: 'Жоғары' },
                { student: 'Дәулет Жанбыр', attendance: 78, delay: '12мин', activity: 'Төмен' },
                { student: 'Ержан Тоқтар', attendance: 96, delay: '1мин', activity: 'Жоғары' }
            ];
            
            analyticsTable.innerHTML = analyticsData.map(item => `
                <tr style="border-bottom: 1px solid #eee;">
                    <td style="padding: 12px;">${item.student}</td>
                    <td style="padding: 12px;">
                        <div style="background: #e8f5e9; padding: 5px 10px; border-radius: 20px; text-align: center; color: #2e7d32; font-weight: bold;">
                            ${item.attendance}%
                        </div>
                    </td>
                    <td style="padding: 12px;">${item.delay}</td>
                    <td style="padding: 12px;">
                        <span class="badge ${item.activity === 'Жоғары' ? 'badge-success' : item.activity === 'Орташа' ? 'badge-warning' : 'badge-danger'}">
                            ${item.activity}
                        </span>
                    </td>
                </tr>
            `).join('');
        }

        // ============================================
        // ҚҰРАЛДАР
        // ============================================
        // ТАЙМЕР
        function startTimer() {
            if (timerInterval) return;
            
            timerInterval = setInterval(() => {
                timerSeconds--;
                updateTimerDisplay();
                
                if (timerSeconds <= 0) {
                    stopTimer();
                    showNotification('Уақыт бітті!', 'warning');
                    playTimerSound();
                }
            }, 1000);
            
            document.getElementById('startTimerBtn').disabled = true;
            document.getElementById('stopTimerBtn').disabled = false;
        }

        function stopTimer() {
            if (timerInterval) {
                clearInterval(timerInterval);
                timerInterval = null;
            }
            
            document.getElementById('startTimerBtn').disabled = false;
            document.getElementById('stopTimerBtn').disabled = true;
        }

        function resetTimer() {
            stopTimer();
            const minutes = parseInt(document.getElementById('timerMinutes').value) || 45;
            timerSeconds = minutes * 60;
            updateTimerDisplay();
        }

        function updateTimer() {
            resetTimer();
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timerSeconds / 60);
            const seconds = timerSeconds % 60;
            document.getElementById('timerDisplay').textContent = 
                `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        // ХАБАРЛАМАЛАР
        function sendAnnouncement() {
            const text = document.getElementById('announcementText').value.trim();
            
            if (!text) {
                showNotification('Хабарлама мәтінін енгізіңіз!', 'error');
                return;
            }
            
            const newAnnouncement = {
                id: Date.now(),
                text: text,
                time: new Date().toLocaleString('kk-KZ'),
                sent: true
            };
            
            announcements.push(newAnnouncement);
            localStorage.setItem('announcements', JSON.stringify(announcements));
            
            updateAnnouncementsList();
            document.getElementById('announcementText').value = '';
            
            showNotification('Хабарлама жіберілді!', 'success');
        }

        function updateAnnouncementsList() {
            const announcementsList = document.getElementById('announcementsList');
            
            if (announcements.length === 0) {
                announcementsList.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        Хабарлама жоқ
                    </div>
                `;
                return;
            }
            
            // Соңғы 5 хабарламаны көрсету
            const recentAnnouncements = announcements.slice(-5).reverse();
            
            announcementsList.innerHTML = recentAnnouncements.map(ann => `
                <div style="background: #f0f7ff; padding: 15px; border-radius: 12px; margin-bottom: 10px;">
                    <div style="font-weight: bold; color: #1a2980; margin-bottom: 5px;">
                        <i class="fas fa-bullhorn"></i> Хабарлама
                    </div>
                    <div style="margin-bottom: 5px;">${ann.text}</div>
                    <div style="color: #666; font-size: 0.9rem;">${ann.time}</div>
                </div>
            `).join('');
        }

        // САУАЛНАМАЛАР
        function showPollForm() {
            document.getElementById('pollForm').style.display = 'block';
            document.getElementById('createPollBtn').style.display = 'none';
        }

        function hidePollForm() {
            document.getElementById('pollForm').style.display = 'none';
            document.getElementById('createPollBtn').style.display = 'inline-flex';
        }

        function addPollOption() {
            const optionsContainer = document.getElementById('pollOptions');
            const optionCount = optionsContainer.children.length + 1;
            
            const newOption = document.createElement('input');
            newOption.type = 'text';
            newOption.className = 'poll-option-input';
            newOption.placeholder = `${optionCount}-нұсқа`;
            newOption.style = 'width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 10px;';
            
            optionsContainer.appendChild(newOption);
        }

        function savePoll() {
            const question = document.getElementById('pollQuestion').value.trim();
            const options = Array.from(document.querySelectorAll('.poll-option-input'))
                .map(input => input.value.trim())
                .filter(option => option);
            
            if (!question) {
                showNotification('Сұрақты енгізіңіз!', 'error');
                return;
            }
            
            if (options.length < 2) {
                showNotification('Кемінде 2 нұсқа қосыңыз!', 'error');
                return;
            }
            
            const newPoll = {
                id: Date.now(),
                question: question,
                options: options.map(option => ({
                    text: option,
                    votes: 0
                })),
                createdAt: new Date().toLocaleString('kk-KZ'),
                active: true
            };
            
            polls.push(newPoll);
            localStorage.setItem('polls', JSON.stringify(polls));
            
            updatePollsList();
            hidePollForm();
            
            // Өрістерді тазарту
            document.getElementById('pollQuestion').value = '';
            document.querySelectorAll('.poll-option-input').forEach((input, index) => {
                if (index < 2) {
                    input.value = index === 0 ? '1-нұсқа' : '2-нұсқа';
                } else {
                    input.remove();
                }
            });
            
            showNotification('Сауалнама қосылды!', 'success');
        }

        function updatePollsList() {
            const pollsList = document.getElementById('pollsList');
            
            if (polls.length === 0) {
                pollsList.innerHTML = `
                    <div style="text-align: center; padding: 30px; color: #666;">
                        <i class="fas fa-poll" style="font-size: 2rem; margin-bottom: 15px; display: block; color: #ccc;"></i>
                        САУАЛНАМА ЖОҚ
                    </div>
                `;
                return;
            }
            
            // Соңғы 3 сауалнаманы көрсету
            const recentPolls = polls.slice(-3).reverse();
            
            pollsList.innerHTML = recentPolls.map(poll => `
                <div style="background: #f8f9fa; padding: 20px; border-radius: 15px; margin-bottom: 20px;">
                    <div style="font-weight: bold; color: #1a2980; margin-bottom: 15px;">
                        <i class="fas fa-question-circle"></i> ${poll.question}
                    </div>
                    
                    ${poll.options.map((option, index) => `
                        <div class="poll-option" data-poll-id="${poll.id}" data-option-index="${index}">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <span>${option.text}</span>
                                <span style="color: #666; font-size: 0.9rem;">${option.votes} дауыс</span>
                            </div>
                            <div style="height: 5px; background: #e0e0e0; border-radius: 3px; margin-top: 5px; overflow: hidden;">
                                <div style="height: 100%; background: #4CAF50; width: ${option.votes * 10}%;"></div>
                            </div>
                        </div>
                    `).join('')}
                    
                    <div style="color: #666; font-size: 0.9rem; margin-top: 10px; text-align: right;">
                        ${poll.createdAt}
                    </div>
                </div>
            `).join('');
        }

        // ============================================
        // КӨМЕКШІ ФУНКЦИЯЛАР
        // ============================================
        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                padding: 15px 25px;
                background: ${type === 'success' ? '#4CAF50' : type === 'error' ? '#f44336' : '#2196F3'};
                color: white;
                border-radius: 10px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.2);
                z-index: 10000;
                animation: slideIn 0.3s ease;
            `;
            
            notification.innerHTML = `
                <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : 'info-circle'}"></i>
                ${message}
            `;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => notification.remove(), 300);
            }, 3000);
        }

        function formatFileSize(bytes) {
            if (bytes < 1024) return bytes + ' Б';
            if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' КБ';
            return (bytes / 1048576).toFixed(1) + ' МБ';
        }

        function exportToExcel() {
            const attendance = JSON.parse(localStorage.getItem('attendance') || '[]');
            
            if (attendance.length === 0) {
                showNotification('Экспорттау үшін деректер жоқ!', 'error');
                return;
            }
            
            // CSV форматтау
            let csv = 'Оқушы аты,Пән,Күні,Уақыты\n';
            attendance.forEach(record => {
                csv += `${record.name || ''},${record.course || ''},${record.date || ''},${record.time || ''}\n`;
            });
            
            // Файлды жүктеу
            const blob = new Blob([csv], { type: 'text/csv' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `қатысу_есебі_${new Date().toLocaleDateString('kk-KZ')}.csv`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            showNotification('Есеп Excel форматында жүктелді!', 'success');
        }

        function playTimerSound() {
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.value = 600;
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 1);
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 1);
            } catch (e) {
                console.log("Аудио қолдауы жоқ");
            }
        }

        // Кестеге элемент қосу
        function addScheduleItem() {
            const time = prompt('Уақыты (мысалы: 09:00):');
            const subject = prompt('Пән атауы:');
            const room = prompt('Кабинет:');
            
            if (time && subject && room) {
                const scheduleItem = { time, subject, room };
                
                // Кестені жаңарту
                const scheduleContainer = document.getElementById('todaySchedule');
                const newItem = document.createElement('div');
                newItem.className = 'schedule-item';
                newItem.innerHTML = `
                    <div class="schedule-time">${time}</div>
                    <div style="font-weight: bold;">${subject}</div>
                    <div style="color: #666;">${room} кабинет</div>
                `;
                
                scheduleContainer.appendChild(newItem);
                showNotification('Кестеге қосылды!', 'success');
            }
        }

        // Стильдерге анимация қосу
        const style = document.createElement('style');
        style.textContent = `
            @keyframes slideIn {
                from { transform: translateX(100%); opacity: 0; }
                to { transform: translateX(0); opacity: 1; }
            }
            @keyframes slideOut {
                from { transform: translateX(0); opacity: 1; }
                to { transform: translateX(100%); opacity: 0; }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
