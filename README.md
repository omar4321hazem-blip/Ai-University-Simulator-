<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AUS
      AI University Simulator</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary: #1a1a2e;
            --secondary: #16213e;
            --accent: #0f3460;
            --gold: #e94560;
            --light: #f1f1f1;
            --success: #00c853;
            --danger: #ff1744;
            --warning: #ffd600;
            --info: #00b0ff;
        }
        
        body {
            font-family: 'Cairo', sans-serif;
            background: var(--primary);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
        }
        
        .bg-animation::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 50%, rgba(233, 69, 96, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 20%, rgba(0, 176, 255, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 50% 80%, rgba(0, 200, 83, 0.1) 0%, transparent 50%);
            animation: bgPulse 10s ease-in-out infinite;
        }
        
        @keyframes bgPulse {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }
        
        /* Header */
        .header {
            background: rgba(22, 33, 62, 0.95);
            backdrop-filter: blur(20px);
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid rgba(233, 69, 96, 0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--gold), #ff6b6b);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            animation: logoFloat 3s ease-in-out infinite;
        }
        
        @keyframes logoFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        
        .logo-text h1 {
            font-size: 1.3em;
            font-weight: 800;
            background: linear-gradient(135deg, #fff, #e94560);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .logo-text span {
            font-size: 0.75em;
            color: #888;
        }
        
        .stats-bar {
            display: flex;
            gap: 20px;
            align-items: center;
        }
        
        .stat-item {
            display: flex;
            align-items: center;
            gap: 8px;
            background: rgba(255,255,255,0.05);
            padding: 8px 16px;
            border-radius: 25px;
            border: 1px solid rgba(255,255,255,0.1);
        }
        
        .stat-item .icon {
            font-size: 1.2em;
        }
        
        .stat-item .value {
            font-weight: 700;
            color: var(--warning);
        }
        
        /* Navigation Breadcrumb */
        .breadcrumb {
            padding: 15px 30px;
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(0,0,0,0.2);
            flex-wrap: wrap;
        }
        
        .breadcrumb-item {
            color: #888;
            cursor: pointer;
            transition: 0.3s;
            font-size: 0.9em;
        }
        
        .breadcrumb-item:hover {
            color: var(--gold);
        }
        
        .breadcrumb-item.active {
            color: var(--gold);
            font-weight: 700;
        }
        
        .breadcrumb-sep {
            color: #444;
        }
        
        /* Main Container */
        .main-container {
            padding: 30px;
            max-width: 1400px;
            margin: 0 auto;
        }
        
        /* Section Title */
        .section-title {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .section-title h2 {
            font-size: 2em;
            font-weight: 900;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #fff, var(--gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .section-title p {
            color: #888;
            font-size: 1em;
        }
        
        /* College Grid */
        .college-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            padding: 20px 0;
        }
        
        .college-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.08), rgba(255,255,255,0.02));
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 30px;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        
        .college-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: var(--card-accent, var(--gold));
        }
        
        .college-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: var(--card-accent, var(--gold));
            box-shadow: 0 20px 60px rgba(0,0,0,0.3), 0 0 30px rgba(233, 69, 96, 0.1);
        }
        
        .college-icon {
            width: 70px;
            height: 70px;
            border-radius: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            margin-bottom: 20px;
            background: linear-gradient(135deg, rgba(233, 69, 96, 0.2), rgba(233, 69, 96, 0.05));
        }
        
        .college-card h3 {
            font-size: 1.15em;
            font-weight: 700;
            margin-bottom: 8px;
        }
        
        .college-card .dept-count {
            color: #888;
            font-size: 0.85em;
        }
        
        /* Specialization Grid */
        .spec-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .spec-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.06), rgba(255,255,255,0.01));
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 16px;
            padding: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }
        
        .spec-card:hover {
            transform: translateY(-5px);
            border-color: var(--gold);
            background: linear-gradient(145deg, rgba(233, 69, 96, 0.1), rgba(233, 69, 96, 0.02));
        }
        
        .spec-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            margin: 0 auto 15px;
            background: linear-gradient(135deg, rgba(233, 69, 96, 0.15), transparent);
        }
        
        .spec-card h4 {
            font-size: 0.95em;
            font-weight: 600;
            line-height: 1.5;
        }
        
        /* System Menu */
        .system-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
        }
        
        .system-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.06), rgba(255,255,255,0.01));
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 16px;
            padding: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .system-card:hover {
            transform: translateY(-5px);
            border-color: var(--card-accent, var(--info));
        }
        
        .system-card .sys-icon {
            width: 60px;
            height: 60px;
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            margin: 0 auto 15px;
        }
        
        .system-card h4 {
            font-weight: 700;
            margin-bottom: 8px;
        }
        
        .system-card p {
            color: #888;
            font-size: 0.8em;
        }
        
        /* Quiz Interface */
        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .quiz-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .hearts {
            display: flex;
            gap: 8px;
        }
        
        .heart {
            font-size: 1.5em;
            transition: 0.3s;
        }
        
        .heart.lost {
            filter: grayscale(1);
            opacity: 0.3;
        }
        
        .progress-bar {
            width: 100%;
            height: 8px;
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            margin-bottom: 30px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--gold), #ff6b6b);
            border-radius: 10px;
            transition: width 0.5s ease;
        }
        
        .question-card {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 35px;
            margin-bottom: 25px;
        }
        
        .question-number {
            color: var(--gold);
            font-size: 0.85em;
            font-weight: 600;
            margin-bottom: 15px;
        }
        
        .question-text {
            font-size: 1.15em;
            font-weight: 600;
            line-height: 1.8;
            margin-bottom: 25px;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .option {
            background: rgba(255,255,255,0.05);
            border: 2px solid rgba(255,255,255,0.1);
            border-radius: 12px;
            padding: 15px 20px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .option:hover {
            border-color: var(--info);
            background: rgba(0, 176, 255, 0.1);
        }
        
        .option.correct {
            border-color: var(--success);
            background: rgba(0, 200, 83, 0.15);
            animation: correctPulse 0.5s ease;
        }
        
        .option.wrong {
            border-color: var(--danger);
            background: rgba(255, 23, 68, 0.15);
            animation: wrongShake 0.5s ease;
        }
        
        .option.disabled {
            pointer-events: none;
            opacity: 0.6;
        }
        
        @keyframes correctPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }
        
        @keyframes wrongShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }
        
        .option-letter {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            background: rgba(255,255,255,0.1);
            flex-shrink: 0;
        }
        
        .feedback-box {
            padding: 20px;
            border-radius: 12px;
            margin-top: 15px;
            display: none;
            animation: fadeIn 0.3s ease;
        }
        
        .feedback-box.show {
            display: block;
        }
        
        .feedback-box.correct {
            background: rgba(0, 200, 83, 0.1);
            border: 1px solid rgba(0, 200, 83, 0.3);
        }
        
        .feedback-box.wrong {
            background: rgba(255, 23, 68, 0.1);
            border: 1px solid rgba(255, 23, 68, 0.3);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Tool Learning */
        .tool-card {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 35px;
            margin-bottom: 25px;
        }
        
        .tool-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .tool-number {
            width: 40px;
            height: 40px;
            background: var(--gold);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.1em;
        }
        
        .tool-content {
            line-height: 2;
            color: #ccc;
            margin-bottom: 25px;
        }
        
        /* Button Styles */
        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 12px;
            font-family: 'Cairo', sans-serif;
            font-weight: 700;
            font-size: 1em;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--gold), #ff6b6b);
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(233, 69, 96, 0.3);
        }
        
        .btn-secondary {
            background: rgba(255,255,255,0.1);
            color: white;
            border: 1px solid rgba(255,255,255,0.2);
        }
        
        .btn-secondary:hover {
            background: rgba(255,255,255,0.15);
        }
        
        .btn-success {
            background: linear-gradient(135deg, var(--success), #69f0ae);
            color: #1a1a2e;
        }
        
        /* Result Screen */
        .result-container {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .result-circle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            margin: 30px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3em;
            font-weight: 900;
            position: relative;
        }
        
        .result-circle::before {
            content: '';
            position: absolute;
            inset: -5px;
            border-radius: 50%;
            padding: 5px;
            background: conic-gradient(var(--success), var(--gold), var(--danger));
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            animation: spin 3s linear infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .personality-result {
            background: linear-gradient(145deg, rgba(233, 69, 96, 0.1), rgba(233, 69, 96, 0.02));
            border: 1px solid rgba(233, 69, 96, 0.3);
            border-radius: 20px;
            padding: 30px;
            margin: 25px 0;
        }
        
        .personality-result h3 {
            color: var(--gold);
            margin-bottom: 15px;
            font-size: 1.3em;
        }
        
        /* AI Chat */
        .ai-chat-container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .ai-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 36px;
            background: linear-gradient(135deg, var(--gold), #ff6b6b);
            animation: avatarPulse 2s ease-in-out infinite;
        }
        
        @keyframes avatarPulse {
            0%, 100% { box-shadow: 0 0 0 0 rgba(233, 69, 96, 0.4); }
            50% { box-shadow: 0 0 0 20px rgba(233, 69, 96, 0); }
        }
        
        .chat-messages {
            max-height: 400px;
            overflow-y: auto;
            margin-bottom: 20px;
            padding: 20px;
            background: rgba(0,0,0,0.2);
            border-radius: 16px;
        }
        
        .chat-message {
            margin-bottom: 15px;
            display: flex;
            gap: 10px;
            animation: fadeIn 0.3s ease;
        }
        
        .chat-message.ai .msg-content {
            background: rgba(233, 69, 96, 0.1);
            border: 1px solid rgba(233, 69, 96, 0.2);
        }
        
        .chat-message.user .msg-content {
            background: rgba(0, 176, 255, 0.1);
            border: 1px solid rgba(0, 176, 255, 0.2);
        }
        
        .msg-content {
            padding: 15px;
            border-radius: 12px;
            max-width: 80%;
            line-height: 1.8;
        }
        
        .chat-input {
            display: flex;
            gap: 10px;
        }
        
        .chat-input input {
            flex: 1;
            padding: 15px 20px;
            border: 2px solid rgba(255,255,255,0.1);
            border-radius: 12px;
            background: rgba(255,255,255,0.05);
            color: white;
            font-family: 'Cairo', sans-serif;
            font-size: 1em;
        }
        
        .chat-input input:focus {
            outline: none;
            border-color: var(--gold);
        }
        
        /* Tool List */
        .tool-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        .tool-item {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 12px;
            padding: 20px;
            cursor: pointer;
            transition: 0.3s;
            text-align: center;
        }
        
        .tool-item:hover {
            border-color: var(--gold);
            transform: translateY(-3px);
        }
        
        .tool-item.completed {
            border-color: var(--success);
            background: rgba(0, 200, 83, 0.05);
        }
        
        .tool-item .tool-emoji {
            font-size: 2em;
            margin-bottom: 10px;
        }
        
        /* Scenario Card */
        .scenario-card {
            background: linear-gradient(145deg, rgba(0, 176, 255, 0.05), transparent);
            border: 1px solid rgba(0, 176, 255, 0.2);
            border-radius: 20px;
            padding: 35px;
            margin-bottom: 25px;
        }
        
        .scenario-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .scenario-badge {
            background: var(--info);
            color: var(--primary);
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 700;
            font-size: 0.85em;
        }
        
        .scenario-text {
            font-size: 1.1em;
            line-height: 2;
            margin-bottom: 25px;
            color: #ddd;
        }
        
        /* Certificate */
        .certificate {
            background: linear-gradient(145deg, rgba(255, 214, 0, 0.05), transparent);
            border: 2px solid rgba(255, 214, 0, 0.3);
            border-radius: 20px;
            padding: 50px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .certificate::before {
            content: '🏆';
            position: absolute;
            top: -20px;
            right: -20px;
            font-size: 100px;
            opacity: 0.1;
        }
        
        .certificate h2 {
            color: var(--warning);
            font-size: 2em;
            margin-bottom: 20px;
        }
        
        .cert-details {
            margin: 20px 0;
            line-height: 2.5;
        }
        
        /* Back Button */
        .back-btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            color: #888;
            cursor: pointer;
            margin-bottom: 20px;
            font-size: 0.9em;
            transition: 0.3s;
        }
        
        .back-btn:hover {
            color: var(--gold);
        }
        
        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(0,0,0,0.2);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--gold);
            border-radius: 3px;
        }
        
        /* Mobile Responsive */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 15px;
                padding: 15px;
            }
            
            .stats-bar {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .main-container {
                padding: 15px;
            }
            
            .college-grid {
                grid-template-columns: 1fr;
            }
            
            .section-title h2 {
                font-size: 1.5em;
            }
            
            .question-card {
                padding: 20px;
            }
        }
        
        /* Loading */
        .loading {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 50px;
        }
        
        .loading .spinner {
            width: 50px;
            height: 50px;
            border: 4px solid rgba(255,255,255,0.1);
            border-top-color: var(--gold);
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }
        
        .hidden {
            display: none !important;
        }
        
        /* Notification */
        .notification {
            position: fixed;
            top: 80px;
            left: 50%;
            transform: translateX(-50%) translateY(-100px);
            padding: 15px 30px;
            border-radius: 12px;
            font-weight: 600;
            z-index: 1000;
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        
        .notification.show {
            transform: translateX(-50%) translateY(0);
        }
        
        .notification.success {
            background: var(--success);
            color: var(--primary);
        }
        
        .notification.error {
            background: var(--danger);
            color: white;
        }
        
        .notification.info {
            background: var(--info);
            color: var(--primary);
        }
        
        /* XP Animation */
        .xp-popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3em;
            font-weight: 900;
            color: var(--warning);
            pointer-events: none;
            z-index: 1000;
            animation: xpFloat 1.5s ease-out forwards;
        }
        
        @keyframes xpFloat {
            0% { opacity: 1; transform: translate(-50%, -50%) scale(0.5); }
            50% { opacity: 1; transform: translate(-50%, -80%) scale(1.2); }
            100% { opacity: 0; transform: translate(-50%, -120%) scale(0.8); }
        }
        
        /* Certificate button glow */
        .cert-btn-glow {
            animation: glowPulse 2s ease-in-out infinite;
        }
        
        @keyframes glowPulse {
            0%, 100% { box-shadow: 0 0 5px rgba(255, 214, 0, 0.3); }
            50% { box-shadow: 0 0 25px rgba(255, 214, 0, 0.6); }
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>
    
    <!-- Notification -->
    <div id="notification" class="notification"></div>
    
    <!-- Header -->
    <div class="header">
        <div class="logo">
            <div class="logo-icon">🎓</div>
            <div class="logo-text">
                <h1>AI University Simulator</h1>
                <span>محاكي الجامعة الذكية</span>
            </div>
        </div>
        <div class="stats-bar">
            <div class="stat-item">
                <span class="icon">⚡</span>
                <span>XP:</span>
                <span class="value" id="totalXP">0</span>
            </div>
            <div class="stat-item">
                <span class="icon">❤️</span>
                <span>الأرواح:</span>
                <span class="value" id="totalHearts">3</span>
            </div>
            <div class="stat-item">
                <span class="icon">🏅</span>
                <span>الشهادات:</span>
                <span class="value" id="totalCerts">0</span>
            </div>
        </div>
    </div>
    
    <!-- Breadcrumb -->
    <div class="breadcrumb" id="breadcrumb">
        <span class="breadcrumb-item active" onclick="showColleges()">🏠 الرئيسية</span>
    </div>
    
    <!-- Main Content -->
    <div class="main-container" id="mainContent">
        <!-- Dynamic content loads here -->
    </div>

    <script>
        // ==================== DATA ====================
        const gameState = {
            xp: 0,
            hearts: 3,
            maxHearts: 3,
            certs: 0,
            currentCollege: null,
            currentSpec: null,
            currentSystem: null,
            currentTool: null,
            currentQuestion: 0,
            toolQuestions: [],
            examQuestions: [],
            examAnswers: [],
            challengeIndex: 0,
            personalityScores: {}
        };

        const colleges = [
            {
                id: 'business',
                name: 'كلية الأعمال',
                icon: '💼',
                color: '#e94560',
                aiName: 'CEO AI',
                aiEmoji: '👔',
                specs: [
                    { id: 'ba', name: 'إدارة الأعمال', icon: '📊' },
                    { id: 'acc', name: 'المحاسبة', icon: '🧮' },
                    { id: 'hr', name: 'إدارة الموارد البشرية', icon: '👥' },
                    { id: 'dm', name: 'التسويق الالكتروني', icon: '📱' },
                    { id: 'fin', name: 'التمويل والتكنولوجيا المالية', icon: '💰' },
                    { id: 'mis', name: 'نظم المعلومات الإدارية', icon: '🖥️' },
                    { id: 'log', name: 'العلوم اللوجستية وإدارة سلاسل التزويد', icon: '🚛' }
                ],
                personalities: [
                    { name: 'القائد الأوتوقراطي', desc: 'هو الحازم الذي يتخذ القرارات وحده لضمان السرعة والانضباط.' },
                    { name: 'القائد الديمقراطي', desc: 'هو المشارك الذي يستشير فريقه ليصنع قراراً جماعياً بروح الفريق.' },
                    { name: 'القائد التحويلي', desc: 'هو الملهم الذي يطور قدرات موظفيه ويحفزهم لتحقيق رؤية مستقبلية طموحة.' },
                    { name: 'القائد التفويضي', desc: 'هو الواثق الذي يمنح فريقه حرية التصرف كاملةً لاعتماده على خبرتهم.' }
                ]
            },
            {
                id: 'it',
                name: 'كلية تكنولوجيا المعلومات',
                icon: '💻',
                color: '#00b0ff',
                aiName: 'مهندس AI',
                aiEmoji: '🤖',
                specs: [
                    { id: 'ds', name: 'علم البيانات والذكاء الاصطناعي', icon: '🧠' },
                    { id: 'se', name: 'هندسة البرمجيات', icon: '⚙️' },
                    { id: 'cs', name: 'الأمن السيبراني', icon: '🔒' },
                    { id: 'csc', name: 'علم الحاسوب', icon: '🖥️' }
                ],
                personalities: [
                    { name: 'المُنفذ التقني (The Coder)', desc: 'يتميز بالدقة العالية في تحويل المتطلبات إلى كود برمجي فعال، ويركز على إنجاز المهام التقنية اليومية بكفاءة ونظام.' },
                    { name: 'حلّال المشكلات (The Troubleshooter)', desc: 'يمتلك مهارات تحليلية فائقة تظهر عند حدوث الأزمات أو الثغرات، وقدرته تتركز في تتبع الأخطاء المعقدة وإيجاد حلول سريعة لها.' },
                    { name: 'المعمارِي الرقمي (The Solution Architect)', desc: 'لا ينظر للكود فقط، بل لهيكل النظام ككل؛ يخطط لكيفية ترابط الأنظمة وضمان قابليتها للتوسع والأمان على المدى البعيد.' },
                    { name: 'المبتكر الاستراتيجي (The Tech Visionary)', desc: 'يربط التقنية بالأهداف الذكية للمؤسسات، ويبحث دائماً عن كيفية توظيف الذكاء الاصطناعي والتقنيات الحديثة لابتكار منتجات جديدة.' }
                ]
            },
            {
                id: 'eng',
                name: 'كلية الهندسة',
                icon: '🏗️',
                color: '#ff9100',
                aiName: 'مهندس AI',
                aiEmoji: '👷',
                specs: [
                    { id: 'arch', name: 'هندسة العمارة', icon: '🏛️' },
                    { id: 'civil', name: 'الهندسة المدنية', icon: '🌉' },
                    { id: 'renew', name: 'هندسة الطاقة المتجددة', icon: '⚡' }
                ],
                personalities: [
                    { name: 'الفني المعياري', desc: 'يركز على متانة البناء ودقة الحسابات الإنشائية، ويعتبر السلامة والمواصفات الفنية خطاً أحمر لا يمكن تجاوزه.' },
                    { name: 'المخطط الوظيفي', desc: 'يركز على تجربة المستخدم داخل الفراغ، ويهمه أن يكون التصميم عملياً ومريحاً ويخدم الهدف منه بأقل جهد.' },
                    { name: 'المصمم البيئي (المستدام)', desc: 'يركز على بُعد المستقبل؛ يستخدم مواد صديقة للبيئة ويصمم أنظمة تستهلك أقل قدر من الطاقة والموارد.' },
                    { name: 'المدير الريادي', desc: 'يجمع بين الجمالية الهندسية والجدوى الاقتصادية؛ يبرع في إدارة المشاريع الكبرى وموازنة التكاليف مع الجودة والابتكار.' }
                ]
            },
            {
                id: 'aviation',
                name: 'كلية علوم الطيران',
                icon: '✈️',
                color: '#7c4dff',
                aiName: 'AI Captain',
                aiEmoji: '👨‍✈️',
                specs: [
                    { id: 'maint', name: 'صيانة الطائرات', icon: '🔧' },
                    { id: 'avionics', name: 'علوم إلكترونيات الطيران', icon: '📡' },
                    { id: 'mgmt', name: 'إدارة الطيران', icon: '🗺️' }
                ],
                personalities: [
                    { name: 'المدقق النظامي', desc: 'يقدس بروتوكولات السلامة وقوائم الفحص، ويؤمن بأن الالتزام التام بالنظام هو الضمان الوحيد لمنع الحوادث.' },
                    { name: 'الخبير الاستنتاجي', desc: 'يبرع في فهم لغة الطائرة المعقدة؛ يربط بين الإشارات الإلكترونية والأعطال الميكانيكية بدقة متناهية وسرعة بديهة.' },
                    { name: 'المنسق اللوجستي', desc: 'تتركز قوته في إدارة سلاسل العمليات؛ يضمن تداخل المهام بين الصيانة والإدارة والرحلات دون أي تأخير تشغيلي.' },
                    { name: 'قائد العمليات (Crisis Manager)', desc: 'يظهر معدنه تحت الضغط؛ يمتلك القدرة على اتخاذ قرارات حاسمة في أجزاء من الثانية تضمن سلامة الأرواح والمعدات.' }
                ]
            },
            {
                id: 'pharmacy',
                name: 'كلية الصيدلة',
                icon: '💊',
                color: '#00c853',
                aiName: 'طبيب AI',
                aiEmoji: '👨‍⚕️',
                specs: [
                    { id: 'pharm', name: 'صيدلة', icon: '💊' }
                ],
                personalities: [
                    { name: 'الدقيق المخبري', desc: 'يركز على صفرية الخطأ؛ بارع في استخدام الأجهزة المعقدة وضمان دقة النتائج المخبرية أو الجرعات الدوائية.' },
                    { name: 'المحلل الإكلينيكي', desc: 'يربط بين النتائج الطبية وبين الحالة السريرية للمريض، ويستطيع قراءة ما بين السطور في التقارير الطبية المعقدة.' },
                    { name: 'المستشار الدوائي', desc: 'يمتلك مهارات تواصل عالية، ويبرع في تقديم المشورة للطبيب أو المريض بناءً على فهمه العميق للتداخلات الحيوية.' },
                    { name: 'الباحث التطويري', desc: 'يميل دائماً للتساؤل عن لماذا؛ يتابع أحدث الأبحاث العالمية ويحاول تطبيق تقنيات حيوية جديدة لتحسين جودة العلاج.' }
                ]
            },
            {
                id: 'sharia',
                name: 'كلية الشريعة',
                icon: '📖',
                color: '#ffd600',
                aiName: 'دكتور AI',
                aiEmoji: '👨‍🏫',
                specs: [
                    { id: 'fiqh', name: 'الفقه وأصوله', icon: '📜' }
                ],
                personalities: [
                    { name: 'النصّي (الحامي)', desc: 'يركز على قدسية النصوص الشرعية والالتزام الحرفي بها لضمان الانضباط وعدم الانحراف عن الثوابت.' },
                    { name: 'الإجرائي (المحامي)', desc: 'تتركز مهارته في فهم قواعد اللعبة الإجرائية، وكيفية استخدام الثغرات واللوائح لخدمة القضية.' },
                    { name: 'المقاصدي (الفلسفي)', desc: 'يبحث عن الغاية وروح النص؛ يركز على العدالة والمصلحة العامة، ويبرع في تفسير النصوص بما يحقق المقصد التشريعي.' },
                    { name: 'المجتهد (المطوّر)', desc: 'يمتلك القدرة على تنزيل الحكم على الواقع؛ يربط بين الأصول وبين المتغيرات المعاصرة.' }
                ]
            },
            {
                id: 'medical',
                name: 'كلية العلوم الطبية التطبيقية',
                icon: '🔬',
                color: '#ff4081',
                aiName: 'طبيب AI',
                aiEmoji: '🩺',
                specs: [
                    { id: 'lab', name: 'العلوم الطبية المخبرية', icon: '🧪' },
                    { id: 'bio', name: 'المعالجات الحيوية', icon: '🧬' }
                ],
                personalities: [
                    { name: 'الدقيق المخبري', desc: 'يركز على صفرية الخطأ؛ بارع في استخدام الأجهزة المعقدة وضمان دقة النتائج المخبرية.' },
                    { name: 'المحلل الإكلينيكي', desc: 'يربط بين النتائج الطبية وبين الحالة السريرية للمريض.' },
                    { name: 'المستشار الطبي', desc: 'يمتلك مهارات تواصل عالية ويبرع في تقديم المشورة بناءً على فهمه العميق للتداخلات الحيوية.' },
                    { name: 'الباحث التطويري', desc: 'يميل للتساؤل عن لماذا ويتابع أحدث الأبحاث العالمية لتحسين جودة العلاج.' }
                ]
            },
            {
                id: 'education',
                name: 'كلية العلوم التربوية',
                icon: '📚',
                color: '#64dd17',
                aiName: 'دكتور AI',
                aiEmoji: '👨‍🏫',
                specs: [
                    { id: 'sped', name: 'تربية خاصة', icon: '♿' },
                    { id: 'child', name: 'الطفولة المبكرة', icon: '👶' },
                    { id: 'counsel', name: 'إرشاد نفسي', icon: '🧠' }
                ],
                personalities: [
                    { name: 'المراقب المنهجي', desc: 'يركز على تطبيق الخطط العلاجية والتربوية بدقة وموضوعية، ويؤمن بأهمية القياس والتقييم المبني على المعايير العلمية.' },
                    { name: 'المُشخّص اللماح', desc: 'يمتلك حدساً مهنياً عالياً في ربط السلوكيات الظاهرة بالأسباب النفسية أو العصبية الكامنة.' },
                    { name: 'الموجه الإنساني', desc: 'يضع العلاقة الإنسانية والذكاء العاطفي في المقدمة، ويبرع في خلق بيئة آمنة للمسترشد أو الطفل.' },
                    { name: 'المصمم العلاجي', desc: 'يتميز بالقدرة على ابتكار استراتيجيات تعليمية أو سلوكية غير تقليدية تتناسب مع الحالات المختلفة.' }
                ]
            },
            {
                id: 'arts',
                name: 'كلية العلوم والآداب',
                icon: '🎨',
                color: '#e040fb',
                aiName: 'دكتور AI',
                aiEmoji: '🎓',
                specs: [
                    { id: 'eng_lang', name: 'اللغة الإنجليزية والترجمة', icon: '🌐' },
                    { id: 'design', name: 'الجرافيك ديزاين', icon: '🎨' }
                ],
                personalities: [
                    { name: 'المراقب المنهجي', desc: 'يركز على الدقة والمعايير في العمل الأكاديمي والفني.' },
                    { name: 'المُشخّص اللماح', desc: 'يمتلك حدساً مهنياً عالياً في تحليل النصوص أو التصاميم بعمق.' },
                    { name: 'الموجه الإنساني', desc: 'يضع التواصل الإنساني والتعبير في المقدمة.' },
                    { name: 'المصمم المبدع', desc: 'يتميز بالقدرة على ابتكار حلول إبداعية غير تقليدية.' }
                ]
            },
            {
                id: 'law',
                name: 'كلية الحقوق',
                icon: '⚖️',
                color: '#ff6d00',
                aiName: 'محامي AI',
                aiEmoji: '👨‍⚖️',
                specs: [
                    { id: 'law', name: 'القانون', icon: '⚖️' }
                ],
                personalities: [
                    { name: 'النصّي (الحامي)', desc: 'يركز على قدسية النصوص القانونية والالتزام الحرفي بها لضمان الانضباط.' },
                    { name: 'الإجرائي (المحامي)', desc: 'تتركز مهارته في فهم قواعد اللعبة الإجرائية وكيفية استخدام اللوائح لخدمة القضية.' },
                    { name: 'المقاصدي (الفلسفي)', desc: 'يبحث عن الغاية وروح النص؛ يركز على العدالة والمصلحة العامة.' },
                    { name: 'المجتهد (المطوّر)', desc: 'يمتلك القدرة على تنزيل الحكم على الواقع وربط الأصول بالمتغيرات المعاصرة.' }
                ]
            }
        ];

        // ==================== TOOLS & METHODS DATA ====================
        function getToolsForSpec(collegeId, specId) {
            const toolsDB = {
                'business': {
                    'ba': [
                        { name: 'تحليل SWOT', emoji: '🎯', desc: 'أداة تحليل استراتيجي تُستخدم لتقييم نقاط القوة (Strengths) ونقاط الضعف (Weaknesses) والفرص (Opportunities) والتهديدات (Threats) لمنظمة أو مشروع. طورها ألبرت همفري في ستينيات القرن العشرين. تساعد في اتخاذ قرارات استراتيجية مبنية على فهم شامل للبيئة الداخلية والخارجية.', questions: [
                            { q: 'ما الذي تمثله حرف S في تحليل SWOT؟', options: ['نقاط القوة', 'الاستراتيجية', 'السرعة', 'المبيعات'], correct: 0, explanation: 'حرف S يرمز إلى Strengths أي نقاط القوة الداخلية للمنظمة.' },
                            { q: 'أي من التالي يعتبر تهديداً خارجياً في تحليل SWOT؟', options: ['نقص التدريب', 'دخول منافس جديد', 'ضعف التسويق', 'ارتفاع تكاليف الإنتاج'], correct: 1, explanation: 'دخول منافس جديد هو تهديد خارجي لأنه من البيئة الخارجية للمنظمة.' },
                            { q: 'الفرص في SWOT تمثل عوامل:', options: ['داخلية إيجابية', 'خارجية إيجابية', 'داخلية سلبية', 'خارجية سلبية'], correct: 1, explanation: 'الفرص هي عوامل خارجية إيجابية يمكن للمنظمة استغلالها.' },
                            { q: 'من طور تحليل SWOT؟', options: ['بيتر دراكر', 'ألبرت همفري', 'مايكل بورتر', 'هنري فايول'], correct: 1, explanation: 'ألبرت همفري طور تحليل SWOT في معهد ستانفورد للأبحاث.' },
                            { q: 'نقاط الضعف في SWOT هي:', options: ['عوامل خارجية سلبية', 'عوامل داخلية سلبية', 'عوامل خارجية إيجابية', 'عوامل داخلية إيجابية'], correct: 1, explanation: 'نقاط الضعف هي عوامل داخلية سلبية تحتاج للمعالجة.' },
                            { q: 'ما الهدف الرئيسي من تحليل SWOT؟', options: ['زيادة المبيعات فقط', 'التخطيط الاستراتيجي الشامل', 'تقليل التكاليف', 'توظيف الموظفين'], correct: 1, explanation: 'الهدف هو التخطيط الاستراتيجي من خلال فهم البيئة الداخلية والخارجية.' },
                            { q: 'أي مثال يمثل نقطة قوة؟', options: ['منافسة شديدة', 'علامة تجارية قوية', 'تغير القوانين', 'نمو السوق'], correct: 1, explanation: 'العلامة التجارية القوية هي ميزة داخلية إيجابية.' },
                            { q: 'عند تحويل التهديدات لفرص نستخدم استراتيجية:', options: ['ST', 'WO', 'SO', 'WT'], correct: 0, explanation: 'استراتيجية ST تستخدم نقاط القوة لمواجهة التهديدات.' },
                            { q: 'SWOT يُستخدم في:', options: ['الشركات الكبيرة فقط', 'المشاريع الشخصية فقط', 'جميع أنواع المنظمات والمشاريع', 'القطاع الحكومي فقط'], correct: 2, explanation: 'SWOT أداة عالمية تصلح لجميع أنواع المنظمات والمشاريع.' },
                            { q: 'أي من التالي ليس جزءاً من SWOT؟', options: ['القوة', 'الكفاءة', 'الفرص', 'التهديدات'], correct: 1, explanation: 'الكفاءة ليست أحد العناصر الأربعة لـ SWOT.' }
                        ]},
                        { name: 'نموذج بورتر للقوى الخمس', emoji: '🏭', desc: 'نموذج طوره مايكل بورتر عام 1979 لتحليل الهيكل التنافسي للصناعة. يتكون من 5 قوى: تهديد الداخلين الجدد، القوة التفاوضية للموردين، القوة التفاوضية للمشترين، تهديد البدائل، والتنافس بين الشركات القائمة.', questions: [
                            { q: 'كم عدد القوى في نموذج بورتر؟', options: ['3', '4', '5', '6'], correct: 2, explanation: 'نموذج بورتر يتكون من 5 قوى تنافسية.' },
                            { q: 'من طور نموذج القوى الخمس؟', options: ['بيتر دراكر', 'مايكل بورتر', 'فيليب كوتلر', 'هنري مينتزبرغ'], correct: 1, explanation: 'مايكل بورتر أستاذ في هارفارد هو من طور هذا النموذج.' },
                            { q: 'أي من التالي ليس من القوى الخمس؟', options: ['تهديد البدائل', 'القوة التفاوضية للحكومة', 'التنافس القائم', 'تهديد الداخلين الجدد'], correct: 1, explanation: 'القوة التفاوضية للحكومة ليست من القوى الخمس الأصلية.' },
                            { q: 'عندما تكون تكلفة التحويل عالية فإن:', options: ['قوة المشترين تزداد', 'قوة المشترين تنخفض', 'تهديد البدائل يزداد', 'التنافس يزداد'], correct: 1, explanation: 'تكلفة التحويل العالية تقلل من قدرة المشترين على التبديل.' },
                            { q: 'حواجز الدخول العالية تعني:', options: ['سهولة دخول منافسين جدد', 'صعوبة دخول منافسين جدد', 'زيادة البدائل', 'انخفاض الأسعار'], correct: 1, explanation: 'حواجز الدخول العالية تحمي الشركات القائمة من المنافسين الجدد.' },
                            { q: 'متى طُور نموذج القوى الخمس؟', options: ['1969', '1979', '1989', '1999'], correct: 1, explanation: 'نُشر النموذج لأول مرة في Harvard Business Review عام 1979.' },
                            { q: 'القوة التفاوضية للموردين تزداد عندما:', options: ['يوجد موردون كثر', 'المورد هو المصدر الوحيد', 'المنتج غير فريد', 'تكلفة التحويل منخفضة'], correct: 1, explanation: 'عندما يكون المورد وحيداً تزداد قوته التفاوضية بشكل كبير.' },
                            { q: 'الغرض من النموذج هو:', options: ['تحليل البيئة الداخلية', 'تحليل جاذبية الصناعة', 'تحديد الأهداف', 'تقييم الأداء'], correct: 1, explanation: 'الهدف الرئيسي هو تحليل جاذبية الصناعة وربحيتها.' },
                            { q: 'التنافس الحاد بين الشركات القائمة يؤدي إلى:', options: ['زيادة الأرباح', 'انخفاض الأرباح', 'زيادة حواجز الدخول', 'تقليل البدائل'], correct: 1, explanation: 'التنافس الشديد يضغط على الأسعار والهوامش الربحية.' },
                            { q: 'تهديد البدائل يزداد عندما:', options: ['البدائل أغلى', 'البدائل تقدم قيمة مماثلة بسعر أقل', 'لا توجد بدائل', 'تكلفة التحويل عالية'], correct: 1, explanation: 'البدائل تصبح تهديداً حقيقياً عندما تقدم قيمة مماثلة بتكلفة أقل.' }
                        ]},
                        { name: 'بطاقة الأداء المتوازن BSC', emoji: '📋', desc: 'أداة إدارية طورها كابلان ونورتون عام 1992 لقياس الأداء من أربعة منظورات: المالي، العملاء، العمليات الداخلية، والتعلم والنمو. تساعد في ترجمة الرؤية والاستراتيجية إلى أهداف ومؤشرات قابلة للقياس.', questions: [
                            { q: 'كم منظوراً في بطاقة الأداء المتوازن؟', options: ['2', '3', '4', '5'], correct: 2, explanation: 'BSC تتكون من 4 منظورات: المالي، العملاء، العمليات، التعلم والنمو.' },
                            { q: 'من طور بطاقة الأداء المتوازن؟', options: ['بورتر وكوتلر', 'كابلان ونورتون', 'دراكر وفايول', 'تايلور وويبر'], correct: 1, explanation: 'روبرت كابلان وديفيد نورتون طورا BSC عام 1992.' },
                            { q: 'أي منظور يركز على رضا العملاء؟', options: ['المالي', 'العملاء', 'العمليات الداخلية', 'التعلم والنمو'], correct: 1, explanation: 'منظور العملاء يركز على رضا ووفاء العملاء وحصة السوق.' },
                            { q: 'منظور التعلم والنمو يشمل:', options: ['الأرباح', 'التدريب والابتكار', 'خدمة العملاء', 'سلسلة التوريد'], correct: 1, explanation: 'يركز على قدرة المنظمة على التعلم والابتكار وتطوير موظفيها.' },
                            { q: 'الهدف من BSC هو:', options: ['قياس الأرباح فقط', 'قياس الأداء الشامل', 'تقليل التكاليف', 'زيادة المبيعات'], correct: 1, explanation: 'BSC تقيس الأداء بشكل شامل ومتوازن من جميع الجوانب.' },
                            { q: 'متى طُورت BSC؟', options: ['1982', '1992', '2002', '2012'], correct: 1, explanation: 'نُشرت لأول مرة في Harvard Business Review عام 1992.' },
                            { q: 'KPI هو اختصار لـ:', options: ['Key Performance Indicator', 'Key Process Integration', 'Knowledge Performance Index', 'Key Planning Initiative'], correct: 0, explanation: 'KPI = Key Performance Indicator أي مؤشر الأداء الرئيسي.' },
                            { q: 'أي منظور يركز على الكفاءة التشغيلية؟', options: ['المالي', 'العملاء', 'العمليات الداخلية', 'التعلم'], correct: 2, explanation: 'منظور العمليات الداخلية يركز على كفاءة وجودة العمليات.' },
                            { q: 'BSC تساعد في:', options: ['التخطيط المالي فقط', 'ترجمة الاستراتيجية لأهداف قابلة للقياس', 'التوظيف', 'التسويق'], correct: 1, explanation: 'BSC أداة لترجمة الرؤية والاستراتيجية إلى أهداف ومؤشرات عملية.' },
                            { q: 'المنظور المالي يقيس:', options: ['رضا الموظفين', 'الربحية والعائد على الاستثمار', 'جودة المنتج', 'الابتكار'], correct: 1, explanation: 'المنظور المالي يقيس الأداء المالي مثل الربحية والإيرادات.' }
                        ]},
                        { name: 'مصفوفة BCG', emoji: '📊', desc: 'مصفوفة مجموعة بوسطن الاستشارية لتحليل محفظة المنتجات. تصنف المنتجات إلى 4 فئات: النجوم (حصة عالية/نمو عالي)، الأبقار النقدية (حصة عالية/نمو منخفض)، علامات الاستفهام (حصة منخفضة/نمو عالي)، الكلاب (حصة منخفضة/نمو منخفض).', questions: [
                            { q: 'النجوم في مصفوفة BCG تمثل:', options: ['حصة عالية ونمو عالي', 'حصة منخفضة ونمو عالي', 'حصة عالية ونمو منخفض', 'حصة منخفضة ونمو منخفض'], correct: 0, explanation: 'النجوم لها حصة سوقية عالية في سوق ينمو بسرعة.' },
                            { q: 'الأبقار النقدية تتميز بـ:', options: ['نمو عالي وحصة عالية', 'نمو منخفض وحصة عالية', 'نمو عالي وحصة منخفضة', 'نمو منخفض وحصة منخفضة'], correct: 1, explanation: 'الأبقار النقدية لها حصة سوقية كبيرة في سوق بطيء النمو وتدر أرباحاً.' },
                            { q: 'BCG تعني:', options: ['Business Consulting Group', 'Boston Consulting Group', 'British Corporate Governance', 'Balance Card Growth'], correct: 1, explanation: 'BCG = Boston Consulting Group مجموعة بوسطن الاستشارية.' },
                            { q: 'المحور الأفقي في المصفوفة يمثل:', options: ['معدل النمو', 'الحصة السوقية النسبية', 'الربحية', 'حجم المبيعات'], correct: 1, explanation: 'المحور الأفقي يمثل الحصة السوقية النسبية.' },
                            { q: 'علامات الاستفهام تحتاج:', options: ['استثمار كبير لتصبح نجوماً', 'التخلص منها فوراً', 'تقليل الإنفاق', 'الحفاظ على الوضع'], correct: 0, explanation: 'علامات الاستفهام تحتاج استثمارات كبيرة لتحسين حصتها السوقية.' },
                            { q: 'الكلاب يُنصح بـ:', options: ['الاستثمار فيها', 'التخلص منها أو تقليصها', 'تحويلها لنجوم', 'زيادة التسويق'], correct: 1, explanation: 'الكلاب لها حصة منخفضة ونمو منخفض، وعادة يُنصح بالتخلص منها.' },
                            { q: 'المحور الرأسي يمثل:', options: ['الحصة السوقية', 'معدل نمو السوق', 'هامش الربح', 'عدد المنافسين'], correct: 1, explanation: 'المحور الرأسي يمثل معدل نمو السوق (عالي/منخفض).' },
                            { q: 'أفضل مصدر للتدفق النقدي هو:', options: ['النجوم', 'الأبقار النقدية', 'علامات الاستفهام', 'الكلاب'], correct: 1, explanation: 'الأبقار النقدية هي أفضل مصدر للتدفق النقدي لأنها لا تحتاج استثماراً كبيراً.' },
                            { q: 'مصفوفة BCG تُستخدم لـ:', options: ['تحليل المنافسين', 'تحليل محفظة المنتجات', 'تحليل العملاء', 'تحليل الموردين'], correct: 1, explanation: 'BCG أداة لتحليل محفظة منتجات الشركة وتحديد الاستراتيجية لكل منتج.' },
                            { q: 'النجم يمكن أن يتحول إلى:', options: ['كلب فوراً', 'بقرة نقدية عندما ينخفض النمو', 'علامة استفهام', 'لا يتحول'], correct: 1, explanation: 'عندما ينضج السوق وينخفض النمو، يتحول النجم لبقرة نقدية.' }
                        ]},
                        { name: 'تحليل PESTEL', emoji: '🌍', desc: 'إطار لتحليل البيئة الكلية يشمل: العوامل السياسية (Political)، الاقتصادية (Economic)، الاجتماعية (Social)، التكنولوجية (Technological)، البيئية (Environmental)، القانونية (Legal).', questions: [
                            { q: 'كم عاملاً يحلله PESTEL؟', options: ['4', '5', '6', '7'], correct: 2, explanation: 'PESTEL يحلل 6 عوامل بيئية كلية.' },
                            { q: 'حرف E الأول يمثل:', options: ['البيئة', 'الاقتصاد', 'التعليم', 'الأخلاق'], correct: 1, explanation: 'E الأولى = Economic أي العوامل الاقتصادية.' },
                            { q: 'التضخم يندرج تحت العوامل:', options: ['السياسية', 'الاقتصادية', 'الاجتماعية', 'القانونية'], correct: 1, explanation: 'التضخم عامل اقتصادي يؤثر على القوة الشرائية والتكاليف.' },
                            { q: 'قوانين حماية البيئة تندرج تحت:', options: ['السياسية', 'البيئية', 'القانونية', 'البيئية والقانونية معاً'], correct: 3, explanation: 'قوانين البيئة تندرج تحت العوامل البيئية والقانونية معاً.' },
                            { q: 'التحول الرقمي يندرج تحت:', options: ['السياسية', 'الاجتماعية', 'التكنولوجية', 'القانونية'], correct: 2, explanation: 'التحول الرقمي عامل تكنولوجي يؤثر على الصناعات.' },
                            { q: 'PESTEL يحلل البيئة:', options: ['الداخلية', 'الكلية/الخارجية', 'التنافسية', 'التشغيلية'], correct: 1, explanation: 'PESTEL يحلل البيئة الكلية الخارجية المحيطة بالمنظمة.' },
                            { q: 'التغيرات الديموغرافية تندرج تحت:', options: ['الاقتصادية', 'الاجتماعية', 'السياسية', 'البيئية'], correct: 1, explanation: 'التركيبة السكانية والديموغرافيا من العوامل الاجتماعية.' },
                            { q: 'الاستقرار الحكومي يندرج تحت:', options: ['السياسية', 'الاقتصادية', 'القانونية', 'الاجتماعية'], correct: 0, explanation: 'الاستقرار الحكومي والسياسات العامة عوامل سياسية.' },
                            { q: 'PESTEL يُستخدم قبل:', options: ['التوظيف', 'دخول سوق جديد', 'إعداد الميزانية', 'تصميم المنتج'], correct: 1, explanation: 'PESTEL مهم جداً قبل دخول أسواق جديدة لفهم البيئة الكلية.' },
                            { q: 'حرف L يمثل:', options: ['اللوجستيات', 'القيادة', 'القانونية', 'التعلم'], correct: 2, explanation: 'L = Legal أي العوامل القانونية والتشريعية.' }
                        ]},
                        { name: 'منهجية Lean Management', emoji: '🔄', desc: 'فلسفة إدارية تركز على تقليل الهدر وتعظيم القيمة المقدمة للعميل. نشأت من نظام إنتاج تويوتا (TPS). تحدد 7 أنواع من الهدر: الإنتاج الزائد، الانتظار، النقل، المعالجة الزائدة، المخزون، الحركة، العيوب.', questions: [
                            { q: 'Lean Management نشأت من:', options: ['شركة فورد', 'نظام إنتاج تويوتا', 'شركة جنرال إلكتريك', 'شركة مايكروسوفت'], correct: 1, explanation: 'Lean نشأت من Toyota Production System (TPS).' },
                            { q: 'كم نوعاً من الهدر يحددها Lean؟', options: ['5', '6', '7', '8'], correct: 2, explanation: 'Lean يحدد 7 أنواع من الهدر (MUDA) يجب التخلص منها.' },
                            { q: 'الهدف الرئيسي من Lean:', options: ['زيادة الإنتاج', 'تقليل الهدر وتعظيم القيمة', 'زيادة الموظفين', 'التوسع الجغرافي'], correct: 1, explanation: 'Lean يركز على إزالة كل ما لا يضيف قيمة للعميل.' },
                            { q: 'Kaizen تعني:', options: ['الإنتاج الضخم', 'التحسين المستمر', 'الجودة الشاملة', 'إدارة المخزون'], correct: 1, explanation: 'Kaizen كلمة يابانية تعني التحسين المستمر بخطوات صغيرة.' },
                            { q: 'أي من التالي يعتبر هدراً في Lean؟', options: ['خدمة العملاء', 'الانتظار بين العمليات', 'التدريب', 'البحث والتطوير'], correct: 1, explanation: 'الانتظار من أنواع الهدر السبعة لأنه لا يضيف قيمة.' },
                            { q: 'JIT تعني:', options: ['Just In Training', 'Just In Time', 'Job In Transit', 'Joint Integration Team'], correct: 1, explanation: 'JIT = Just In Time أي الإنتاج في الوقت المناسب بالكمية المناسبة.' },
                            { q: 'خريطة تدفق القيمة (VSM) تُستخدم لـ:', options: ['رسم الهيكل التنظيمي', 'تحديد خطوات العملية والهدر فيها', 'تحليل السوق', 'تقييم الموظفين'], correct: 1, explanation: 'VSM ترسم جميع خطوات العملية لتحديد أين يوجد الهدر.' },
                            { q: '5S تشمل:', options: ['ترتيب مكان العمل', 'خمس استراتيجيات تسويق', 'خمس سياسات مالية', 'خمس طرق توظيف'], correct: 0, explanation: '5S منهجية يابانية لتنظيم مكان العمل: ترتيب، تنظيم، تنظيف، توحيد، استدامة.' },
                            { q: 'الإنتاج الزائد يعتبر:', options: ['ميزة تنافسية', 'أسوأ أنواع الهدر', 'ضروري للاحتياط', 'غير مهم'], correct: 1, explanation: 'الإنتاج الزائد يعتبر أسوأ أنواع الهدر لأنه يسبب أنواع هدر أخرى.' },
                            { q: 'Gemba تعني:', options: ['المكتب', 'موقع العمل الفعلي', 'الاجتماع', 'التقرير'], correct: 1, explanation: 'Gemba كلمة يابانية تعني المكان الفعلي حيث يتم العمل والقيمة.' }
                        ]},
                        { name: 'Six Sigma', emoji: '📐', desc: 'منهجية لتحسين الجودة طورتها موتورولا عام 1986 وتبنتها جنرال إلكتريك. تهدف لتقليل العيوب إلى 3.4 عيب لكل مليون فرصة. تستخدم منهجية DMAIC: تعريف، قياس، تحليل، تحسين، مراقبة.', questions: [
                            { q: 'Six Sigma طورتها شركة:', options: ['تويوتا', 'موتورولا', 'جنرال إلكتريك', 'آبل'], correct: 1, explanation: 'طور بيل سميث Six Sigma في موتورولا عام 1986.' },
                            { q: 'هدف Six Sigma هو تقليل العيوب إلى:', options: ['صفر عيب', '3.4 لكل مليون', '10 لكل ألف', '1 لكل مئة'], correct: 1, explanation: 'المستوى 6 سيجما يعني 3.4 عيب فقط لكل مليون فرصة.' },
                            { q: 'DMAIC تبدأ بـ:', options: ['Design', 'Define', 'Develop', 'Deliver'], correct: 1, explanation: 'D = Define أي تعريف المشكلة وتحديد نطاق المشروع.' },
                            { q: 'الحزام الأسود في Six Sigma يعني:', options: ['مبتدئ', 'خبير يقود مشاريع التحسين', 'مدير عام', 'مستشار خارجي'], correct: 1, explanation: 'Black Belt هو خبير مدرب يقود مشاريع التحسين بتفرغ كامل.' },
                            { q: 'حرف M في DMAIC يعني:', options: ['Manage', 'Measure', 'Monitor', 'Modify'], correct: 1, explanation: 'M = Measure أي قياس الأداء الحالي وجمع البيانات.' },
                            { q: 'حرف A في DMAIC يعني:', options: ['Apply', 'Analyze', 'Arrange', 'Adapt'], correct: 1, explanation: 'A = Analyze أي تحليل البيانات لتحديد الأسباب الجذرية.' },
                            { q: 'حرف C في DMAIC يعني:', options: ['Create', 'Complete', 'Control', 'Change'], correct: 2, explanation: 'C = Control أي مراقبة العملية المحسنة لضمان استدامة التحسين.' },
                            { q: 'من أشهر من تبنى Six Sigma بعد موتورولا:', options: ['تويوتا', 'جنرال إلكتريك', 'سامسونج', 'أمازون'], correct: 1, explanation: 'جاك ويلش جعل Six Sigma محور استراتيجية جنرال إلكتريك في التسعينيات.' },
                            { q: 'سيجما (σ) هي رمز:', options: ['المتوسط', 'الانحراف المعياري', 'النسبة المئوية', 'معامل الارتباط'], correct: 1, explanation: 'σ (سيجما) هي رمز الانحراف المعياري في الإحصاء.' },
                            { q: 'الحزام الأخضر:', options: ['أعلى من الأسود', 'يعمل بدوام جزئي على مشاريع التحسين', 'لا يشارك في مشاريع', 'مسؤول عن التدريب فقط'], correct: 1, explanation: 'Green Belt يعمل على مشاريع التحسين بدوام جزئي مع مهامه الأساسية.' }
                        ]},
                        { name: 'نموذج Canvas لنموذج الأعمال', emoji: '🎯', desc: 'أداة طورها ألكسندر أوستروالدر لتصميم نماذج الأعمال. تتكون من 9 مكونات: شرائح العملاء، القيمة المقترحة، القنوات، العلاقات مع العملاء، مصادر الإيرادات، الموارد الرئيسية، الأنشطة الرئيسية، الشراكات الرئيسية، هيكل التكاليف.', questions: [
                            { q: 'كم مكوناً في Business Model Canvas؟', options: ['5', '7', '9', '11'], correct: 2, explanation: 'Canvas يتكون من 9 مكونات تغطي جميع جوانب نموذج الأعمال.' },
                            { q: 'من طور نموذج Canvas؟', options: ['مايكل بورتر', 'ألكسندر أوستروالدر', 'ستيف بلانك', 'إيريك ريس'], correct: 1, explanation: 'ألكسندر أوستروالدر طوره في كتابه Business Model Generation.' },
                            { q: 'القيمة المقترحة تجيب على سؤال:', options: ['من هم عملاؤك؟', 'لماذا يختارك العميل؟', 'كيف تكسب المال؟', 'من شركاؤك؟'], correct: 1, explanation: 'Value Proposition تحدد ما الذي يميزك ولماذا يختارك العميل.' },
                            { q: 'مصادر الإيرادات تشمل:', options: ['كيف تنفق المال', 'كيف تكسب المال', 'من يعمل لديك', 'أين تعمل'], correct: 1, explanation: 'Revenue Streams تحدد كيف تحقق المنظمة إيراداتها.' },
                            { q: 'شرائح العملاء تحدد:', options: ['المنتجات', 'الفئات المستهدفة', 'الأسعار', 'الموردين'], correct: 1, explanation: 'Customer Segments تحدد الفئات المختلفة التي تخدمها المنظمة.' },
                            { q: 'القنوات في Canvas تعني:', options: ['قنوات التلفزيون', 'طرق الوصول للعملاء', 'قنوات الإنترنت فقط', 'الموردين'], correct: 1, explanation: 'Channels هي الطرق والوسائل للوصول للعملاء وتقديم القيمة لهم.' },
                            { q: 'الموارد الرئيسية تشمل:', options: ['العملاء فقط', 'الأصول الضرورية لعمل النموذج', 'المنافسين', 'الحكومة'], correct: 1, explanation: 'Key Resources هي الأصول المادية والبشرية والمالية الضرورية.' },
                            { q: 'الشراكات الرئيسية تجيب على:', options: ['من هم عملاؤك؟', 'من هم أهم شركائك؟', 'كم تربح؟', 'ما منتجاتك؟'], correct: 1, explanation: 'Key Partners تحدد التحالفات والشراكات الاستراتيجية.' },
                            { q: 'هيكل التكاليف يوضح:', options: ['الإيرادات', 'أهم التكاليف في النموذج', 'عدد الموظفين', 'حجم السوق'], correct: 1, explanation: 'Cost Structure يحدد أهم التكاليف المرتبطة بتشغيل نموذج الأعمال.' },
                            { q: 'Canvas يُستخدم من قبل:', options: ['الشركات الكبيرة فقط', 'الشركات الناشئة فقط', 'أي نوع من المنظمات', 'الحكومات فقط'], correct: 2, explanation: 'Canvas أداة مرنة تصلح لأي نوع من المنظمات والمشاريع.' }
                        ]},
                        { name: 'مصفوفة أنسوف للنمو', emoji: '📈', desc: 'مصفوفة طورها إيغور أنسوف عام 1957 لتحديد استراتيجيات النمو. تتكون من 4 استراتيجيات: اختراق السوق (منتج حالي/سوق حالي)، تطوير المنتج (منتج جديد/سوق حالي)، تطوير السوق (منتج حالي/سوق جديد)، التنويع (منتج جديد/سوق جديد).', questions: [
                            { q: 'كم استراتيجية في مصفوفة أنسوف؟', options: ['2', '3', '4', '5'], correct: 2, explanation: 'مصفوفة أنسوف تتكون من 4 استراتيجيات نمو.' },
                            { q: 'اختراق السوق يعني:', options: ['منتج جديد في سوق جديد', 'منتج حالي في سوق حالي', 'منتج جديد في سوق حالي', 'منتج حالي في سوق جديد'], correct: 1, explanation: 'اختراق السوق = زيادة مبيعات المنتج الحالي في السوق الحالي.' },
                            { q: 'التنويع هو الاستراتيجية الأكثر:', options: ['أماناً', 'مخاطرة', 'شيوعاً', 'بساطة'], correct: 1, explanation: 'التنويع (منتج جديد في سوق جديد) هو الأعلى مخاطرة.' },
                            { q: 'تطوير المنتج يعني:', options: ['بيع نفس المنتج في سوق جديد', 'تقديم منتج جديد في السوق الحالي', 'الخروج من السوق', 'تقليل الأسعار'], correct: 1, explanation: 'Product Development = تطوير منتجات جديدة للعملاء الحاليين.' },
                            { q: 'من طور مصفوفة أنسوف؟', options: ['مايكل بورتر', 'إيغور أنسوف', 'بيتر دراكر', 'فيليب كوتلر'], correct: 1, explanation: 'إيغور أنسوف طورها عام 1957 ويُعرف بأبو الإدارة الاستراتيجية.' },
                            { q: 'أقل الاستراتيجيات مخاطرة:', options: ['التنويع', 'تطوير السوق', 'اختراق السوق', 'تطوير المنتج'], correct: 2, explanation: 'اختراق السوق أقل مخاطرة لأنه يعتمد على ما تعرفه المنظمة.' },
                            { q: 'فتح فرع في بلد جديد بنفس المنتج:', options: ['اختراق السوق', 'تطوير السوق', 'تطوير المنتج', 'التنويع'], correct: 1, explanation: 'بيع المنتج الحالي في سوق جغرافي جديد = تطوير السوق.' },
                            { q: 'محاور المصفوفة هي:', options: ['سعر ومنتج', 'منتج وسوق', 'ربح وتكلفة', 'عرض وطلب'], correct: 1, explanation: 'المحوران هما: المنتج (حالي/جديد) والسوق (حالي/جديد).' },
                            { q: 'إضافة نكهات جديدة لمنتج غذائي:', options: ['اختراق السوق', 'تطوير المنتج', 'تطوير السوق', 'التنويع'], correct: 1, explanation: 'إضافة نكهات جديدة = تطوير المنتج في السوق الحالي.' },
                            { q: 'شركة سيارات تدخل مجال الطيران:', options: ['اختراق السوق', 'تطوير المنتج', 'تطوير السوق', 'التنويع'], correct: 3, explanation: 'الدخول لصناعة مختلفة تماماً = تنويع غير مرتبط.' }
                        ]},
                        { name: 'تحليل سلسلة القيمة', emoji: '🔗', desc: 'نموذج طوره مايكل بورتر لتحليل الأنشطة الداخلية للشركة. يقسم الأنشطة إلى: أنشطة أساسية (اللوجستيات الداخلية، العمليات، اللوجستيات الخارجية، التسويق والمبيعات، الخدمة) وأنشطة داعمة (البنية التحتية، إدارة الموارد البشرية، التطوير التكنولوجي، المشتريات).', questions: [
                            { q: 'سلسلة القيمة طورها:', options: ['أنسوف', 'دراكر', 'بورتر', 'كوتلر'], correct: 2, explanation: 'مايكل بورتر طور تحليل سلسلة القيمة في كتابه Competitive Advantage.' },
                            { q: 'الأنشطة الأساسية عددها:', options: ['3', '4', '5', '6'], correct: 2, explanation: '5 أنشطة أساسية: لوجستيات داخلية، عمليات، لوجستيات خارجية، تسويق، خدمة.' },
                            { q: 'التسويق والمبيعات نشاط:', options: ['داعم', 'أساسي', 'خارجي', 'ثانوي'], correct: 1, explanation: 'التسويق والمبيعات من الأنشطة الأساسية في سلسلة القيمة.' },
                            { q: 'إدارة الموارد البشرية نشاط:', options: ['أساسي', 'داعم', 'خارجي', 'مؤقت'], correct: 1, explanation: 'إدارة الموارد البشرية من الأنشطة الداعمة التي تدعم جميع الأنشطة.' },
                            { q: 'هدف تحليل سلسلة القيمة:', options: ['تحليل المنافسين', 'تحديد مصادر الميزة التنافسية', 'تحليل البيئة الخارجية', 'تحديد الأسعار'], correct: 1, explanation: 'الهدف هو فهم كيف تخلق الشركة قيمة وأين يمكن تحسين الميزة التنافسية.' },
                            { q: 'اللوجستيات الداخلية تشمل:', options: ['التوزيع للعملاء', 'استلام وتخزين المواد الخام', 'التسويق', 'خدمة ما بعد البيع'], correct: 1, explanation: 'Inbound Logistics تشمل استلام وتخزين ومعالجة المدخلات.' },
                            { q: 'الأنشطة الداعمة عددها:', options: ['2', '3', '4', '5'], correct: 2, explanation: '4 أنشطة داعمة: البنية التحتية، HR، التطوير التكنولوجي، المشتريات.' },
                            { q: 'هامش الربح في سلسلة القيمة يمثل:', options: ['التكاليف فقط', 'الفرق بين القيمة الكلية والتكاليف', 'الإيرادات فقط', 'الأنشطة الداعمة'], correct: 1, explanation: 'الهامش = القيمة التي يدفعها العملاء - تكاليف الأنشطة.' },
                            { q: 'العمليات (Operations) تشمل:', options: ['تخزين المواد الخام', 'تحويل المدخلات لمنتجات نهائية', 'توزيع المنتجات', 'خدمة العملاء'], correct: 1, explanation: 'Operations هي عملية تحويل المدخلات إلى المنتج النهائي.' },
                            { q: 'سلسلة القيمة تحلل:', options: ['البيئة الخارجية', 'الأنشطة الداخلية', 'المنافسين', 'العملاء'], correct: 1, explanation: 'سلسلة القيمة أداة لتحليل الأنشطة الداخلية للشركة.' }
                        ]}
                    ],
                    'acc': [
                        { name: 'القيد المزدوج', emoji: '📒', desc: 'مبدأ أساسي في المحاسبة حيث كل معاملة مالية تؤثر على حسابين على الأقل - مدين ودائن. المبلغ المدين يجب أن يساوي المبلغ الدائن دائماً.', questions: Array.from({length:10}, (_, i) => ({q: `سؤال ${i+1} عن القيد المزدوج`, options: ['إجابة أ', 'إجابة ب', 'إجابة ج', 'إجابة د'], correct: 0, explanation: 'شرح الإجابة الصحيحة'})) },
                        { name: 'الميزانية العمومية', emoji: '📊', desc: 'قائمة مالية تعرض الأصول والالتزامات وحقوق الملكية في تاريخ محدد.', questions: Array.from({length:10}, (_, i) => ({q: `سؤال ${i+1} عن الميزانية العمومية`, options: ['إجابة أ', 'إجابة ب', 'إجابة ج', 'إجابة د'], correct: 0, explanation: 'شرح'})) },
                        { name: 'قائمة الدخل', emoji: '💵', desc: 'تعرض الإي 
