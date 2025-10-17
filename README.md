<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مبادرة التميُّز - تحسين قراءة الأعداد</title>
    <style>
        body {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            margin: 0;
            padding: 20px;
            min-height: 100%;
        }

        html {
            height: 100%;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 25px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .title {
            color: #d63384;
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .subtitle {
            color: #6f42c1;
            font-size: 1.3rem;
            margin-bottom: 20px;
        }

        .card {
            background: linear-gradient(145deg, #fff0f6, #fce4ec);
            border-radius: 20px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 0 8px 25px rgba(214, 51, 132, 0.15);
            border: 2px solid #f8bbd9;
        }

        .input-section {
            display: flex;
            gap: 15px;
            align-items: center;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 20px;
        }

        .number-input {
            font-size: 1.8rem;
            padding: 15px 20px;
            border: 3px solid #f8bbd9;
            border-radius: 15px;
            text-align: center;
            min-width: 300px;
            background: white;
            color: #d63384;
            font-weight: bold;
        }

        .number-input:focus {
            outline: none;
            border-color: #d63384;
            box-shadow: 0 0 15px rgba(214, 51, 132, 0.3);
        }

        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 15px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            color: white;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
        }

        .btn-primary {
            background: linear-gradient(45deg, #d63384, #e91e63);
        }

        .btn-secondary {
            background: linear-gradient(45deg, #6f42c1, #8e44ad);
        }

        .btn-success {
            background: linear-gradient(45deg, #20c997, #28a745);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        .mic-section {
            text-align: center;
            margin: 25px 0;
        }

        .mic-btn {
            background: linear-gradient(45deg, #ff6b9d, #ff8fab);
            border: none;
            border-radius: 50%;
            width: 80px;
            height: 80px;
            font-size: 2rem;
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 20px rgba(255, 107, 157, 0.3);
        }

        .mic-btn:hover {
            transform: scale(1.1);
        }

        .mic-btn.recording {
            background: linear-gradient(45deg, #dc3545, #e74c3c);
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .result-section {
            margin: 25px 0;
            text-align: center;
        }

        .student-answer {
            background: #fff3cd;
            border: 2px solid #f
            feaa7;
            border-radius: 15px;
            padding: 20px;
            margin: 15px 0;
            font-size: 1.3rem;
            color: #856404;
        }

        .feedback {
            padding: 20px;
            border-radius: 15px;
            margin: 15px 0;
            font-size: 1.4rem;
            font-weight: bold;
            text-align: center;
        }

        .feedback.correct {
            background: linear-gradient(145deg, #d4edda, #c3e6cb);
            color: #155724;
            border: 2px solid #b8daff;
        }

        .feedback.incorrect {
            background: linear-gradient(145deg, #f8d7da, #f5c6cb);
            color: #721c24;
            border: 2px solid #f1b0b7;
        }

        .number-display {
            font-size: 3rem;
            font-weight: bold;
            color: #d63384;
            text-align: center;
            padding: 20px;
            background: white;
            border-radius: 15px;
            margin: 20px 0;
            border: 3px solid #f8bbd9;
            letter-spacing: 2px;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            background: linear-gradient(145deg, #fce4ec, #f8bbd9);
            border-radius: 15px;
            color: #d63384;
            font-weight: bold;
            font-size: 1.1rem;
        }

        .status {
            text-align: center;
            margin: 15px 0;
            font-size: 1.1rem;
            color: #6f42c1;
        }

        .hidden {
            display: none;
        }

        .icon {
            margin-left: 8px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1 class="title">🌟 مبادرة التميُّز 🌟</h1>
            <p class="subtitle">تحسين قراءة الأعداد في مادة الرياضيات للمرحلة الابتدائية</p>
        </header>

        <div class="card">
            <div class="input-section">
                <input type="text" id="numberInput" class="number-input" placeholder="أدخلي الرقم هنا (حتى 12 خانة)" maxlength="12">
                <button class="btn btn-primary" onclick="generateRandomNumber()">
                    <span class="icon">🎲</span>
                    توليد رقم عشوائي
                </button>
            </div>

            <div class="number-display" id="numberDisplay">
                أدخلي رقماً لتبدأ التمرين
            </div>
        </div>

        <div class="card">
            <div class="mic-section">
                <p style="color: #d63384; font-size: 1.2rem; margin-bottom: 15px;">
                    <span class="icon">🎤</span>
                    اضغطي على الميكرفون واقرئي الرقم بصوت واضح
                </p>
                <button class="mic-btn" id="micBtn" onclick="toggleRecording()">🎤</button>
                <div class="status" id="status">اضغطي على الميكرفون للبدء</div>
            </div>
        </div>

        <div class="card result-section" id="resultSection" style="display: none;">
            <h3 style="color: #d63384; text-align: center;">📝 إجابتك:</h3>
            <div class="student-answer" id="studentAnswer"></div>
            
            <div class="feedback" id="feedback"></div>
            
            <div style="text-align: center; margin-top: 20px;">
                <button class="btn btn-success" onclick="playCorrectAnswer()">
                    <span class="icon">🔊</span>
                    استمعي للقراءة الصحيحة
                </button>
            </div>
        </div>

        <div class="footer">
            <p>💖 تصميم أ.سميرة الزهراني 💖</p>
        </div>
    </div>

    <script>
        let recognition;
        let isRecording = false;
        let currentNumber = '';

        // تحويل الأرقام إلى كلمات عربية
        const ones = ['', 'واحد', 'اثنان', 'ثلاثة', 'أربعة', 'خمسة', 'ستة', 'سبعة', 'ثمانية', 'تسعة'];
        const tens = ['', '', 'عشرون', 'ثلاثون', 'أربعون', 'خمسون', 'ستون', 'سبعون', 'ثمانون', 'تسعون'];
        const teens = ['عشرة', 'أحد عشر', 'اثنا عشر', 'ثلاثة عشر', 'أربعة عشر', 'خمسة عشر', 'ستة
        عشر', 'سبعة عشر', 'ثمانية عشر', 'تسعة عشر'];

        function numberToArabicWords(num) {
            if (num === '0') return 'صفر';
            
            const numStr = num.toString();
            const length = numStr.length;
            
            if (length <= 3) {
                return convertHundreds(parseInt(num));
            } else if (length <= 6) {
                const thousands = Math.floor(parseInt(num) / 1000);
                const remainder = parseInt(num) % 1000;
                let result = convertHundreds(thousands) + ' ألف';
                if (remainder > 0) {
                    result += ' ' + convertHundreds(remainder);
                }
                return result;
            } else if (length <= 9) {
                const millions = Math.floor(parseInt(num) / 1000000);
                const remainder = parseInt(num) % 1000000;
                let result = convertHundreds(millions) + ' مليون';
                if (remainder > 0) {
                    const thousands = Math.floor(remainder / 1000);
                    const ones = remainder % 1000;
                    if (thousands > 0) {
                        result += ' ' + convertHundreds(thousands) + ' ألف';
                    }
                    if (ones > 0) {
                        result += ' ' + convertHundreds(ones);
                    }
                }
                return result;
            } else {
                const billions = Math.floor(parseInt(num) / 1000000000);
                const remainder = parseInt(num) % 1000000000;
                let result = convertHundreds(billions) + ' مليار';
                if (remainder > 0) {
                    const millions = Math.floor(remainder / 1000000);
                    const thousands = Math.floor((remainder % 1000000) / 1000);
                    const ones = remainder % 1000;
                    if (millions > 0) {
                        result += ' ' + convertHundreds(millions) + ' مليون';
                    }
                    if (thousands > 0) {
                        result += ' ' + convertHundreds(thousands) + ' ألف';
                    }
                    if (ones > 0) {
                        result += ' ' + convertHundreds(ones);
                    }
                }
                return result;
            }
        }

        function convertHundreds(num) {
            if (num === 0) return '';
            
            let result = '';
            const hundreds = Math.floor(num / 100);
            const remainder = num % 100;
            
            if (hundreds > 0) {
                if (hundreds === 1) {
                    result += 'مائة';
                } else if (hundreds === 2) {
                    result += 'مائتان';
                } else {
                    result += ones[hundreds] + ' مائة';
                }
            }
            
            if (remainder > 0) {
                if (result) result += ' ';
                
                if (remainder < 10) {
                    result += ones[remainder];
                } else if (remainder < 20) {
                    result += teens[remainder - 10];
                } else {
                    const tensDigit = Math.floor(remainder / 10);
                    const onesDigit = remainder % 10;
                    result += tens[tensDigit];
                    if (onesDigit > 0) {
                        result += ' ' + ones[onesDigit];
                    }
                }
            }
            
            return result;
        }

        function generateRandomNumber() {
            const digits = Math.floor(Math.random() * 12) + 1;
            let number = '';
            for (let i = 0; i < digits; i++) {
                if (i === 0) {
                    number += Math.floor(Math.random() * 9) + 1;
                } else {
                    number += Math.floor(Math.random() * 10);
                }
            }
            document.getElementById('numberInput').value = number;
            updateNumberDisplay();
        }
        function updateNumb
        erDisplay() {
            const input = document.getElementById('numberInput').value;
            const display = document.getElementById('numberDisplay');
            
            if (input && /^\d+$/.test(input) && input.length <= 12) {
                display.textContent = input;
                currentNumber = input;
                document.getElementById('resultSection').style.display = 'none';
            } else if (input.length > 12) {
                display.textContent = 'الرقم كبير جداً! (أقصى حد 12 خانة)';
                currentNumber = '';
            } else {
                display.textContent = 'أدخلي رقماً صحيحاً';
                currentNumber = '';
            }
        }

        function initSpeechRecognition() {
            if ('webkitSpeechRecognition' in window) {
                recognition = new webkitSpeechRecognition();
            } else if ('SpeechRecognition' in window) {
                recognition = new SpeechRecognition();
            } else {
                document.getElementById('status').textContent = 'المتصفح لا يدعم التعرف على الصوت';
                return;
            }

            recognition.lang = 'ar-SA';
            recognition.continuous = false;
            recognition.interimResults = false;

            recognition.onstart = function() {
                document.getElementById('status').textContent = '🎤 أتحدث الآن...';
            };

            recognition.onresult = function(event) {
                const transcript = event.results[0][0].transcript;
                processAnswer(transcript);
            };

            recognition.onerror = function(event) {
                document.getElementById('status').textContent = 'حدث خطأ، حاولي مرة أخرى';
                stopRecording();
            };

            recognition.onend = function() {
                stopRecording();
            };
        }

        function toggleRecording() {
            if (!currentNumber) {
                alert('يرجى إدخال رقم أولاً!');
                return;
            }

            if (!recognition) {
                initSpeechRecognition();
            }

            if (isRecording) {
                recognition.stop();
            } else {
                recognition.start();
                startRecording();
            }
        }

        function startRecording() {
            isRecording = true;
            const micBtn = document.getElementById('micBtn');
            micBtn.classList.add('recording');
            document.getElementById('status').textContent = '🎤 أتحدث الآن...';
        }

        function stopRecording() {
            isRecording = false;
            const micBtn = document.getElementById('micBtn');
            micBtn.classList.remove('recording');
            document.getElementById('status').textContent = 'اضغطي على الميكرفون للبدء';
        }

        function processAnswer(studentAnswer) {
            const correctAnswer = numberToArabicWords(currentNumber);
            const resultSection = document.getElementById('resultSection');
            const studentAnswerDiv = document.getElementById('studentAnswer');
            const feedbackDiv = document.getElementById('feedback');

            studentAnswerDiv.textContent = studentAnswer;
            resultSection.style.display = 'block';

            // مقارنة بسيطة للإجابات
            const normalizedStudent = studentAnswer.replace(/\s+/g, ' ').trim().toLowerCase();
            const normalizedCorrect = correctAnswer.replace(/\s+/g, ' ').trim().toLowerCase();

            if (normalizedStudent.includes(normalizedCorrect) || normalizedCorrect.includes(normalizedStudent)) {
                feedbackDiv.className = 'feedback correct';
                feedbackDiv.innerHTML = '✅ أحسنت! قرأت الرقم بشكل صحيح 🌟';
            } else {
                feedbackDiv.className = 'feedback incorrect';
                feedbackDiv.innerHTML = '❌ حاولي مرة أخرى 💪<br>القراءة الصحيحة: ' + correctAnswer;
            }
        }

        function playCorrectAnswer() {
            if (!currentNumber) return;
            const correctAnswer = numberToArabicWords(currentNumber);
            
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(correctAnswer);
                utterance.lang = 'ar-SA';
                utterance.rate = 0.8;
                utterance.pitch = 1.2;
                
                // البحث عن صوت أنثوي عربي
                const voices = speechSynthesis.getVoices();
                const arabicFemaleVoice = voices.find(voice => 
                    voice.lang.includes('ar') && voice.name.toLowerCase().includes('female')
                ) || voices.find(voice => voice.lang.includes('ar'));
                
                if (arabicFemaleVoice) {
                    utterance.voice = arabicFemaleVoice;
                }
                
                speechSynthesis.speak(utterance);
            }
        }

        // تحديث العرض عند تغيير المدخل
        document.getElementById('numberInput').addEventListener('input', updateNumberDisplay);

        // تحميل الأصوات عند تحميل الصفحة
        window.addEventListener('load', function() {
            if ('speechSynthesis' in window) {
                speechSynthesis.getVoices();
            }
        });

        // التأكد من تحميل الأصوات
        if ('speechSynthesis' in window) {
            speechSynthesis.addEventListener('voiceschanged', function() {
                // الأصوات محملة الآن
            });
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9900a658a0ecce18',t:'MTc2MDcxMzA2MS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
