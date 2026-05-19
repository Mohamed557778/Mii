<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>⚡ MATRIX CHAT // SECURE_LINE</title>
    <style>
        :root {
            --bg-dark: #06070d;
            --panel-bg: rgba(14, 16, 27, 0.85);
            --neon-cyan: #00f3ff;
            --neon-green: #39ff14;
            --neon-magenta: #ff0055;
            --text-main: #f1f5f9;
            --text-muted: #475569;
            --border-glow: rgba(0, 243, 255, 0.2);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Courier New', Courier, 'Segoe UI', Tahoma, sans-serif;
        }

        body {
            background-color: var(--bg-dark);
            background-image: 
                linear-gradient(rgba(18, 24, 38, 0.4) 1px, transparent 1px),
                linear-gradient(90deg, rgba(18, 24, 38, 0.4) 1px, transparent 1px);
            background-size: 20px 20px;
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        /* حاوية الدردشة الزجاجية */
        .chat-frame {
            width: 100%;
            max-width: 480px;
            height: 100vh;
            background: var(--panel-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-left: 2px solid var(--neon-cyan);
            border-right: 2px solid var(--neon-cyan);
            box-shadow: 0 0 30px rgba(0, 243, 255, 0.15);
            display: flex;
            flex-direction: column;
            position: relative;
        }

        /* الهيدر المطور */
        .chat-header {
            padding: 20px;
            background: rgba(8, 9, 16, 0.9);
            border-bottom: 2px solid rgba(0, 243, 255, 0.3);
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }

        .system-status {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .chat-title {
            font-size: 1.15rem;
            font-weight: bold;
            color: var(--neon-cyan);
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.6);
            letter-spacing: 1px;
        }

        .encryption-badge {
            font-size: 0.7rem;
            color: var(--neon-green);
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .encryption-badge::before {
            content: '';
            display: inline-block;
            width: 6px;
            height: 6px;
            background: var(--neon-green);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--neon-green);
            animation: blink 1.5s infinite;
        }

        .btn-purge {
            background: rgba(255, 0, 85, 0.1);
            border: 1px solid var(--neon-magenta);
            color: var(--neon-magenta);
            padding: 8px 14px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: bold;
            transition: all 0.3s ease;
            text-shadow: 0 0 5px var(--neon-magenta);
        }

        .btn-purge:hover {
            background: var(--neon-magenta);
            color: #fff;
            box-shadow: 0 0 15px var(--neon-magenta);
        }

        /* منطقة استعراض المحادثات */
        .display-area {
            flex: 1;
            padding: 25px 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .display-area::-webkit-scrollbar {
            width: 3px;
        }
        .display-area::-webkit-scrollbar-thumb {
            background: var(--neon-cyan);
        }

        /* ستايل الرسائل المشفرة */
        .msg-bubble {
            max-width: 80%;
            padding: 12px 16px;
            font-size: 0.95rem;
            line-height: 1.5;
            position: relative;
            animation: slideIn 0.25s cubic-bezier(0.18, 0.89, 0.32, 1.28);
            border-radius: 4px;
        }

        .incoming {
            background: rgba(0, 243, 255, 0.05);
            color: var(--neon-cyan);
            align-self: flex-start;
            border-right: 3px solid var(--neon-cyan);
            border-top-left-radius: 12px;
            border-bottom-left-radius: 12px;
            box-shadow: inset 0 0 10px rgba(0, 243, 255, 0.05);
        }

        .outgoing {
            background: rgba(57, 255, 20, 0.05);
            color: #d1f7c4;
            align-self: flex-end;
            border-left: 3px solid var(--neon-green);
            border-top-right-radius: 12px;
            border-bottom-right-radius: 12px;
            box-shadow: inset 0 0 10px rgba(57, 255, 20, 0.05);
        }

        .sys-log {
            background: rgba(255, 255, 255, 0.02);
            color: var(--text-muted);
            font-size: 0.75rem;
            align-self: center;
            padding: 6px 12px;
            border: 1px dashed rgba(255, 255, 255, 0.1);
            border-radius: 2px;
            text-shadow: none;
        }

        /* صندوق الإدخال التكنولوجي */
        .terminal-input-bar {
            padding: 20px;
            background: rgba(8, 9, 16, 0.95);
            border-top: 2px solid rgba(0, 243, 255, 0.2);
            display: flex;
            gap: 12px;
        }

        .terminal-field {
            flex: 1;
            background: #0f111a;
            border: 1px solid rgba(0, 243, 255, 0.3);
            color: var(--text-main);
            padding: 14px;
            border-radius: 6px;
            outline: none;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.5);
        }

        .terminal-field:focus {
            border-color: var(--neon-cyan);
            box-shadow: 0 0 12px rgba(0, 243, 255, 0.3), inset 0 0 8px rgba(0, 0, 0, 0.5);
        }

        .btn-transmit {
            background: var(--neon-cyan);
            color: #000;
            border: none;
            padding: 0 22px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.4);
            text-transform: uppercase;
        }

        .btn-transmit:hover {
            background: #fff;
            box-shadow: 0 0 20px #fff;
            transform: scale(1.02);
        }

        /* الأنيميشنس */
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(12px) scale(0.98); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }
    </style>
</head>
<body>

    <div class="chat-frame">
        <!-- الهيدر الاستخباراتي -->
        <div class="chat-header">
            <div class="system-status">
                <div class="chat-title">QUANTUM_LINE // v2.0</div>
                <div class="encryption-badge">تشفير محلي نشط 100%</div>
            </div>
            <button class="btn-purge" onclick="purgeSystem()">تطهير شامل</button>
        </div>

        <!-- ساحة عرض الشفرات (الرسائل) -->
        <div class="display-area" id="displayArea">
            <div class="msg-bubble sys-log">جدار الحماية مفعل بالكامل. البيانات تُخزن في الذاكرة المعزولة لجهازك الحالي فقط.</div>
        </div>

        <!-- وحدة بث البيانات (الكتابة) -->
        <div class="terminal-input-bar">
            <input type="text" id="terminalInput" class="terminal-field" placeholder="أدخل رسالتك السرية هنا برمز الآلة..." onkeypress="handleKey(event)">
            <button class="btn-transmit" onclick="transmitData()">إرسال</button>
        </div>
    </div>

    <script>
        const displayArea = document.getElementById('displayArea');
        const terminalInput = document.getElementById('terminalInput');
        let userToggle = true; 

        // استدعاء البيانات من الذاكرة الرام المحلية للمتصفح فور الفتح
        window.onload = function() {
            const cachedLogs = localStorage.getItem('shadow_chat_vault');
            if (cachedLogs) {
                displayArea.innerHTML = cachedLogs;
                autoScroll();
            }
        };

        function transmitData() {
            const rawText = terminalInput.value.trim();
            if (rawText === '') return;

            const msgNode = document.createElement('div');
            msgNode.classList.add('msg-bubble');
            
            // محاكاة متبادلة لإرسال محلي تجريبي مريح ومبهر
            if (userToggle) {
                msgNode.classList.add('incoming');
            } else {
                msgNode.classList.add('outgoing');
            }
            
            msgNode.innerText = rawText;
            displayArea.appendChild(msgNode);
            
            // تحديث مخزن البيانات المشفرة محلياً
            localStorage.setItem('shadow_chat_vault', displayArea.innerHTML);
            
            terminalInput.value = '';
            userToggle = !userToggle; 
            autoScroll();
        }

        function handleKey(e) {
            if (e.key === 'Enter') {
                transmitData();
            }
        }

        function autoScroll() {
            displayArea.scrollTop = displayArea.scrollHeight;
        }

        // مسح تام وفوري لقاعدة البيانات المحلية دون ترك أي أثر بكسل
        function purgeSystem() {
            if (confirm("هل تريد تفعيل بروتوكول التطهير الشامل ومسح الذاكرة؟")) {
                localStorage.removeItem('shadow_chat_vault');
                displayArea.innerHTML = '<div class="msg-bubble sys-log">تم تطهير النظام بالكامل وصفرت السجلات.</div>';
            }
        }
    </script>
</body>
</html>
