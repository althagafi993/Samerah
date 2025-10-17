<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مبادرة التميز لقراءة الأعداد 🏅</title>
    <script src="https://cdn.jsdelivr.net/npm/n2words/n2words.min.js"></script>

    <style>
        /* CSS للتصميم الجذاب والألوان الأنثوية المحسنة */
        :root {
            --primary-color: #ff69b4; /* وردي ساخن (Hot Pink) */
            --secondary-color: #ffb6c1; /* وردي فاتح (Light Pink) */
            --accent-color: #9370db; /* بنفسجي متوسط (Medium Purple) */
            --success-color: #3cb371; /* أخضر نضارة */
            --error-color: #dc143c; /* أحمر كرزي */
            --text-color: #4a4a4a;
            --bg-color: #fff0f5; /* خلفية وردية فاتحة جدًا */
        }

        body {
            font-family: 'Arial', sans-serif; 
            background: linear-gradient(135deg, var(--bg-color) 0%, #faeef8 100%);
            color: var(--text-color);
            text-align: center;
            padding: 20px;
            direction: rtl;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 30px; 
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
            border: 8px solid var(--primary-color);
            position: relative;
            overflow: hidden;
        }
        
        /* تزيين Container بنقاط مبهجة */
        .container::before {
            content: "✨";
            position: absolute;
            top: 10px;
            left: 10px;
            font-size: 2em;
            opacity: 0.5;
        }
        .container::after {
            content: "💖";
            position: absolute;
            bottom: 10px;
            right: 10px;
            font-size: 2em;
            opacity: 0.5;
        }

        h1 {
            color: var(--primary-color);
            font-size: 3em;
            margin-bottom: 5px;
            text-shadow: 2px 2px 5px var(--secondary-color);
        }

        h2 {
            color: var(--accent-color);
            font-size: 2em;
            margin-bottom: 30px;
            border-bottom: 4px solid var(--secondary-color);
            padding-bottom: 10px;
            display: inline-block;
        }

        .input-group {
            margin: 25px 0;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        input[type="text"] {
            padding: 18px;
            font-size: 2em;
            width: 90%;
            max-width: 450px;
            border: 5px solid var(--secondary-color);
            border-radius: 15px;
            text-align: center;
            margin-bottom: 20px;
            color: var(--accent-color);
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
        }

        input[type="text"]:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 15px var(--primary-color);
            outline: none;
        }

        button {
            background-color: var(--accent-color);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-size: 1.2em;
            margin: 8px;
            transition: background-color 0.3s ease, transform 0.1s, box-shadow 0.3s;
            box-shadow: 0 6px var(--primary-color);
        }

        button:hover {
            background-color: #a893e2; 
        }

        button:active {
            transform: translateY(3px);
            box-shadow: 0 3px var(--primary-color);
        }

        .microphone-btn {
            background-color: var(--primary-color);
            box-shadow: 0 6px #ff3399;
            font-size: 1.5em;
            min-width: 300px;
            margin-top: 20px;
        }

        .microphone-btn:hover {
            background-color: #ff3399;
        }

        .result-area {
            min-height: 100px;
            margin-top: 30px;
            padding: 20px;
            border: 4px dashed var(--secondary-color);
            background-color: #fcfcfc;
            border-radius: 20px;
            font-size: 1.5em;
            font-weight: bold;
            color: var(--text-color);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .feedback-icon {
            font-size: 4em;
            margin: 20px;
            display: none;
            font-weight: bold;
            animation: bounce 0.5s ease-in-out;
        }

        .feedback-icon.success {
            color: var(--success-color);
        }

        .feedback-icon.error {
            color: var(--error-color);
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .footer {
            margin-top: 40px;
            padding-top: 15px;
            border-top: 2px dashed var(--secondary-color);
            font-size: 1.1em;
            color: var(--accent-color);
            font-weight: 500;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🏅 مبادرة التميز 🏅</h1>
        <h2>( تحسين قراءة الأعداد في مادة الرياضيات للمرحلة الابتدائية )</h2>
        
        <div class="input-group">
            <label for="numberInput" style="font-size: 1.8em; margin-bottom: 10px; color: var(--accent-color); font-weight: bold;">العدد المطلوب قراءته:</label>
            <input type="text" id="numberInput" placeholder="أدخل رقمًا أو اضغط توليد عشوائي" maxlength="12">
            
            <div class="controls">
                <button onclick="generateRandomNumber()">توليد عدد عشوائي 🎲</button>
                <button onclick="speakNumber()" id="listenBtn">سماع القراءة الصحيحة 🎧 (مساعد جوجل)</button>
            </div>
        </div>

        <div class="interaction-area">
            <button class="microphone-btn" id="recordBtn" onclick="toggleRecording()">
                🎙️ ابدأ التحدث
            </button>
            
            <p id="microphoneStatus" style="margin-top: 15px; font-size: 1.1em; color: var(--primary-color);">اضغطي على الزر لبدء التسجيل</p>
            
            <div class="result-area">
                <span id="speechResult">ستظهر محاولة قراءة الطالبة (نصًا) هنا...</span>
            </div>
            
            <span id="successIcon" class="feedback-icon success">✅ أحسنتِ!</span>
            <span id="errorIcon" class="feedback-icon error">❌ حاولي مجددًا</span>
        </div>

        <div class="footer">
            تصميم أ.سميرة الزهراني
        </div>

    </div>

    <script>
        const numberInput = document.getElementById('numberInput');
        const speechResult = document.getElementById('speechResult');
        const recordBtn = document.getElementById('recordBtn');
        const microphoneStatus = document.getElementById('microphoneStatus');
        const successIcon = document.getElementById('successIcon');
        const errorIcon = document.getElementById('errorIcon');
        
        let recognition = null; 
        let isRecording = false;

        // --- وظائف مساعدة ---
        
        /**
         * تنظيف النص للمقارنة: إزالة الفراغات الزائدة وعلامات الترقيم.
         */
        function normalizeArabicText(text) {
            if (!text) return '';
            // إزالة التشكيل (الحركات) والرموز غير المرغوب فيها
            let normalized = text.replace(/[\u064B-\u0652\u06F0-\u06F9\u200F\u202E\.\,\!\?]/g, ''); 
            // معاملة "و" كفاصل وإزالة الفراغات الزائدة
            normalized = normalized.replace(/و/g, ' '); 
            normalized = normalized.replace(/\s+/g, ' ').trim(); 
            return normalized;
        }

        /**
         * إخفاء جميع أيقونات التقييم
         */
        function hideFeedback() {
            successIcon.style.display = 'none';
            errorIcon.style.display = 'none';
        }

        // --- وظائف توليد الأرقام والقراءة ---
        
        /**
         * توليد رقم عشوائي بين 1 و 999,999,999,999 (12 خانة كحد أقصى)
         */
        function generateRandomNumber() {
            // توليد طول عشوائي بين 1 و 12
            const length = Math.floor(Math.random() * 12) + 1; 
            let randomNumString = '';
            for (let i = 0; i < length; i++) {
                if (i === 0 && length > 1) {
                    randomNumString += Math.floor(Math.random() * 9) + 1; 
                } else {
                    randomNumString += Math.floor(Math.random() * 10); 
                }
            }
            if (length === 1 && randomNumString === '0') randomNumString = '1';
            
            numberInput.value = randomNumString; 
            hideFeedback();
            speechResult.textContent = 'ستظهر محاولة قراءة الطالبة (نصًا) هنا...';
        }
        
        /**
         * تحويل النص إلى كلام (Text-to-Speech) - سماع القراءة الصحيحة.
         */
        function speakNumber() {
            const numberToRead = numberInput.value.trim();
            if (!numberToRead) {
                alert("الرجاء إدخال رقم أولاً.");
                return;
            }
            
            const utterance = new SpeechSynthesisUtterance(numberToRead);
            utterance.lang = 'ar-SA'; 
            
            // محاولة اختيار صوت أنثوي (لتلبية المتطلب التقني)
            const voices = speechSynthesis.getVoices();
            const femaleVoice = voices.find(voice => voice.lang === 'ar-SA' && (voice.name.includes('Female') || voice.name.includes('Google') || voice.name.includes('Arabic')));
            if (femaleVoice) {
                utterance.voice = femaleVoice;
            } 
            
            speechSynthesis.speak(utterance);
            hideFeedback();
        }

        // --- وظائف التعرف على الكلام والتقييم التلقائي ---

        /**
         * تقييم قراءة الطالبة تلقائيًا.
         */
        function automaticEvaluation(studentReading) {
            const numberValue = numberInput.value.trim();
            
            if (!numberValue) {
                errorIcon.style.display = 'inline-block';
                return;
            }

            let correctText = '';
            try {
                // تحويل الرقم إلى نص عربي باستخدام المكتبة
                correctText = n2words(Number(numberValue), { lang: 'ar' });
            } catch (e) {
                correctText = "خطأ في تحويل الرقم إلى نص";
            }

            // تنظيف النصوص للمقارنة الدقيقة
            const normalizedCorrect = normalizeArabicText(correctText);
            const normalizedStudent = normalizeArabicText(studentReading);
            
            // المقارنة: يجب أن تكون القراءة مطابقة تمامًا.
            if (normalizedStudent === normalizedCorrect && normalizedCorrect !== "خطأ في تحويل الرقم إلى نص") {
                successIcon.style.display = 'inline-block';
                errorIcon.style.display = 'none';
            } else {
                errorIcon.style.display = 'inline-block';
                successIcon.style.display = 'none';
            }
        }

        /**
         * بدء/إيقاف التسجيل الصوتي للطالبة
         */
        function toggleRecording() {
            // التحقق من دعم المتصفح لـ Web Speech API 
            if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
                alert('عذرًا، متصفحك لا يدعم وظيفة التعرف على الكلام (مطلوبة للتقييم الآلي). يرجى استخدام متصفح محدث مثل Chrome أو Edge.');
                return;
            }

            if (isRecording) {
                if (recognition) {
                    recognition.stop();
                }
                isRecording = false;
                recordBtn.textContent = '🎙️ ابدأ التحدث';
                microphoneStatus.textContent = 'التسجيل متوقف.';
            } else {
                const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
                recognition = new SpeechRecognition();
                
                recognition.lang = 'ar-SA'; // للتعرف على الكلام باللغة العربية الفصحى
                recognition.interimResults = false; 
                recognition.maxAlternatives = 1;
                
                recognition.onstart = () => {
                    isRecording = true;
                    recordBtn.textContent = '🔴 جاري الاستماع... (اضغطي للإيقاف)';
                    microphoneStatus.textContent = 'المايكروفون مفتوح، يرجى قراءة الرقم...';
                    speechResult.textContent = 'جاري الاستماع...';
                    hideFeedback();
                };

                recognition.onresult = (event) => {
                    const studentReading = event.results[0][0].transcript;
                    speechResult.textContent = `قراءة الطالبة: "${studentReading}"`;
                    automaticEvaluation(studentReading);
                    toggleRecording(); 
                };

                recognition.onerror = (event) => {
                    console.error('Speech recognition error:', event.error);
                    microphoneStatus.textContent = `حدث خطأ: ${event.error}. تأكدي من إعطاء إذن الميكروفون.`;
                    isRecording = false;
                    recordBtn.textContent = '🎙️ ابدأ التحدث';
                };
                
                recognition.onend = () => {
                    if (isRecording) { 
                        isRecording = false;
                        recordBtn.textContent = '🎙️ ابدأ التحدث';
                        microphoneStatus.textContent = 'التسجيل متوقف.';
                    }
                };

                recognition.start();
            }
        }
        
        window.onload = generateRandomNumber;

    </script>
</body>
</html>
