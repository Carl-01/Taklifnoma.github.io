<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To'y Taklifnomasi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;600;700&family=Poppins:wght@300;400;500;600&display=swap');
        
        .dancing-script {
            font-family: 'Dancing Script', cursive;
        }
        
        .poppins {
            font-family: 'Poppins', sans-serif;
        }
        
        .sticker-rain {
            position: fixed;
            top: -50px;
            animation: stickerFall linear infinite;
            pointer-events: none;
            z-index: 1;
        }
        
        @keyframes stickerFall {
            to {
                transform: translateY(100vh) rotate(360deg);
            }
        }
        
        .fade-in {
            opacity: 1;
        }
    </style>
</head>
<body class="bg-white min-h-screen">
    <!-- Sticker Rain Container -->
    <div id="stickerRain" class="fixed inset-0 pointer-events-none overflow-hidden"></div>

    <!-- Welcome Form -->
    <div id="welcomeForm" class="fixed inset-0 bg-blue-600 flex items-center justify-center z-50">
        <div class="bg-white rounded-2xl p-8 max-w-md mx-4 text-center shadow-2xl">
            <div class="text-4xl mb-4">🕊️</div>
            <h2 class="dancing-script text-3xl font-bold text-blue-800 mb-4">Xush kelibsiz!</h2>
            <p class="poppins text-blue-600 mb-6">Iltimos ism va familyangizni kiriting</p>
            
            <div class="space-y-4">
                <input type="text" id="nameInput" placeholder="Ismingiz" class="w-full px-4 py-3 border border-blue-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 poppins">
                <input type="text" id="surnameInput" placeholder="Familyangiz" class="w-full px-4 py-3 border border-blue-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 poppins">
                
                <!-- Gender Selection -->
                <div class="space-y-2">
                    <p class="poppins text-blue-600 text-sm font-medium">Kimsiz?</p>
                    <div class="flex space-x-3">
                        <button type="button" onclick="selectGender('male')" id="maleBtn" class="flex-1 px-4 py-3 border-2 border-blue-200 rounded-lg font-semibold transition-all poppins hover:border-blue-400 text-blue-600">
                            👨 ERKAK
                        </button>
                        <button type="button" onclick="selectGender('female')" id="femaleBtn" class="flex-1 px-4 py-3 border-2 border-blue-200 rounded-lg font-semibold transition-all poppins hover:border-blue-400 text-blue-600">
                            👩 AYOL
                        </button>
                    </div>
                </div>
                
                <button onclick="enterSite()" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors poppins">
                    ✅ Tayyor
                </button>
            </div>
        </div>
    </div>

    <div class="container mx-auto px-4 py-6 relative z-10" id="mainContent" style="display: none;">
        <!-- Language Switcher -->
        <div class="max-w-2xl mx-auto mb-4 text-center">
            <div class="inline-flex bg-white rounded-lg shadow-md border border-blue-200 p-1">
                <button onclick="switchLanguage('latin')" id="latinBtn" class="px-4 py-2 rounded-md text-sm font-medium transition-colors bg-blue-600 text-white">
                    O'zbek (Lotin)
                </button>
                <button onclick="switchLanguage('cyrillic')" id="cyrillicBtn" class="px-4 py-2 rounded-md text-sm font-medium transition-colors text-blue-600 hover:bg-blue-50">
                    Ўзбек (Кирил)
                </button>
            </div>
        </div>
        
        <!-- Main Card -->
        <div class="max-w-2xl mx-auto bg-white rounded-2xl shadow-lg overflow-hidden fade-in border border-blue-200">
            
            <!-- Header -->
            <div class="bg-blue-600 p-6 text-center relative">
                <div class="text-4xl mb-3">🕊️</div>
                <h1 class="dancing-script text-4xl font-bold text-white mb-2">To'y Taklifnomasi</h1>
                <p class="poppins text-blue-100 text-base">Bizning baxtli kunimizga xush kelibsiz!</p>
            </div>

            <!-- Couple Names -->
            <div class="p-6 text-center bg-blue-50">
                <div class="flex justify-center items-center space-x-3 mb-4">
                    <h2 class="dancing-script text-4xl font-bold text-blue-800">
                        Nozimaxon & Jasurbek
                    </h2>
                </div>
                <div class="flex justify-center items-center space-x-3 mb-4">
                    <span class="text-2xl">🕊️</span>
                    <div class="w-16 h-1 bg-blue-400 rounded-full"></div>
                    <span class="text-3xl">💍</span>
                    <div class="w-16 h-1 bg-blue-400 rounded-full"></div>
                    <span class="text-2xl">🕊️</span>
                </div>

            </div>

            <!-- Timer Section -->
            <div class="p-6 bg-blue-100 text-center">
                <h3 class="dancing-script text-2xl font-bold text-blue-800 mb-4">To'ygacha qolgan vaqt</h3>
                <div class="flex justify-center space-x-4 mb-4">
                    <div class="bg-white p-3 rounded-lg shadow-md">
                        <div class="text-2xl font-bold text-blue-600" id="days">00</div>
                        <div class="text-sm text-blue-500">Kun</div>
                    </div>
                    <div class="bg-white p-3 rounded-lg shadow-md">
                        <div class="text-2xl font-bold text-blue-600" id="hours">00</div>
                        <div class="text-sm text-blue-500">Soat</div>
                    </div>
                    <div class="bg-white p-3 rounded-lg shadow-md">
                        <div class="text-2xl font-bold text-blue-600" id="minutes">00</div>
                        <div class="text-sm text-blue-500">Daqiqa</div>
                    </div>
                    <div class="bg-white p-3 rounded-lg shadow-md">
                        <div class="text-2xl font-bold text-blue-600" id="seconds">00</div>
                        <div class="text-sm text-blue-500">Soniya</div>
                    </div>
                </div>
            </div>

            <!-- Event Details -->
            <div class="p-6 bg-white">
                <div class="space-y-4">
                    <!-- Date -->
                    <div class="flex items-center space-x-4 p-4 bg-blue-50 rounded-lg border border-blue-200">
                        <span class="text-3xl">📅</span>
                        <div>
                            <h3 class="poppins font-semibold text-blue-800">Sana va Vaqt</h3>
                            <p class="dancing-script text-xl text-blue-600 font-bold">23 Avgust, 2025 - 12:00</p>
                            <p class="poppins text-sm text-blue-500">Qiz bazmi</p>
                            <p class="poppins text-xs text-blue-400 mt-1">Ayollar va Qizlar uchun</p>
                        </div>
                    </div>

                    <!-- Location -->
                    <div class="flex items-center space-x-4 p-4 bg-blue-50 rounded-lg border border-blue-200">
                        <span class="text-3xl">🏛️</span>
                        <div>
                            <h3 class="poppins font-semibold text-blue-800">Manzil</h3>
                            <p class="dancing-script text-xl text-blue-600 font-bold">"DILOROM" to'yxonasi</p>
                            <p class="poppins text-sm text-blue-500">Toshkent sh., Uchtepa tumani</p>
                        </div>
                    </div>
                </div>

                <!-- Message -->
                <div class="mt-6 p-4 bg-blue-50 rounded-lg border-l-4 border-blue-400">
                    <div class="flex items-start space-x-3">
                        <span class="text-2xl">💌</span>
                        <div>
                            <h4 class="poppins font-semibold text-blue-800 mb-2" id="dearGuestTitle">Aziz mehmon !</h4>
                            <p class="poppins text-blue-700 leading-relaxed" id="invitationMessage">
                                Bizning eng baxtli kunimizni siz va sizning oilangiz bilan nishonlashni xohlaymiz! 
                                Sizning borligingiz to'yimizni yanada chiroyli va esda qolarli qiladi!
                            </p>
                        </div>
                    </div>
                </div>
            </div>



            <!-- RSVP Buttons -->
            <div class="p-6 bg-blue-600 text-center">
                <h3 class="dancing-script text-2xl font-bold text-white mb-4" data-text="rsvp-title">
                    📝 Javobingizni yuboring
                </h3>
                <div class="flex justify-center mb-4">
                    <button onclick="confirmAttendance('ha')" class="poppins bg-white text-blue-600 px-8 py-3 rounded-lg font-semibold hover:bg-blue-50 transition-colors duration-300" data-text="confirm-btn">
                        ✅ Albatta boraman
                    </button>
                </div>
                
                <!-- Map Buttons -->
                <div id="mapButtons" class="hidden space-y-3">
                    <h4 class="text-white font-semibold mb-3" data-text="map-title">To'yxona manzillari:</h4>
                    <div class="flex flex-col sm:flex-row gap-3 justify-center">
                        <a href="https://yandex.uz/maps/?text=Toshkent Uchtepa DILOROM to'yxonasi" target="_blank" class="poppins bg-red-500 text-white px-6 py-3 rounded-lg font-semibold hover:bg-red-600 transition-colors duration-300 flex items-center justify-center space-x-2">
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                            </svg>
                            <span>Yandex Maps</span>
                        </a>
                        <a href="https://www.google.com/maps/search/Toshkent+Uchtepa+DILOROM+to'yxonasi" target="_blank" class="poppins bg-green-500 text-white px-6 py-3 rounded-lg font-semibold hover:bg-green-600 transition-colors duration-300 flex items-center justify-center space-x-2">
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                            </svg>
                            <span>Google Maps</span>
                        </a>
                    </div>
                </div>
            </div>

            <!-- Contact -->
            <div class="p-4 bg-blue-100 text-center">
                <p class="poppins text-blue-700 font-semibold mb-3">
                    Xurmat va ehtirom ila
                </p>
                <p class="dancing-script text-lg text-blue-600 font-bold">
                    Yusufali Xoliyarovlar xonadoni
                </p>
            </div>
        </div>

        <!-- Footer -->
        <div class="text-center mt-4">
            <p class="dancing-script text-xl text-blue-700" id="guestName">
                Xurmatli Mehmon !
            </p>
            <p class="poppins text-blue-600 mt-2" id="invitationText">
                Sizni farzandlarimizning to'y marosimida intiqlik bilan kutamiz
            </p>
        </div>
    </div>

    <!-- Modal -->
    <div id="confirmationModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-6 max-w-sm mx-4 text-center">
            <div class="text-4xl mb-3" id="modalEmoji">🎉</div>
            <h3 class="dancing-script text-2xl font-bold text-gray-800 mb-3" id="modalTitle">Rahmat!</h3>
            <p class="poppins text-gray-600 text-sm mb-4" id="modalMessage">Javobingiz qabul qilindi.</p>
            <button onclick="closeModal()" class="poppins bg-gray-800 text-white px-6 py-2 rounded-lg text-sm hover:bg-gray-700 transition-colors">
                Yopish
            </button>
        </div>
    </div>

    <script>
        let userName = '';
        let userSurname = '';
        let userGender = '';
        let selectedGender = '';

        // Gender detection database
        const genderDatabase = {
            // O'zbek ayollar ismlari
            female: [
                'nozima', 'gulnoza', 'dilnoza', 'feruza', 'malika', 'shahlo', 'sevara', 'nilufar', 'mohira', 'zarina',
                'dilfuza', 'gulshan', 'madina', 'fotima', 'oisha', 'zebo', 'gulnor', 'shahnoza', 'munira', 'kamola',
                'nasiba', 'robiya', 'saida', 'shirin', 'yulduz', 'oysha', 'gulchehra', 'nargiza', 'dildora', 'gulbahor',
                'nozimaxon', 'dilshoda', 'gulrux', 'mohigul', 'shakar', 'gulsanam', 'gulzoda', 'mehriban', 'gulzor',
                'nargis', 'gulnar', 'gulsum', 'gulmira', 'gulhayo', 'gulnara', 'gulzira', 'gulshan', 'gulchin',
                'maryam', 'zulfiya', 'nodira', 'gavhar', 'barno', 'durdona', 'laylo', 'jamila', 'zebiniso', 'sabohat',
                'sitora', 'charos', 'nigora', 'shoira', 'umida', 'nargiza', 'gulchexra', 'dilbar', 'gulbahar',
                // Qoraqalpoq ayollar ismlari
                'aysulu', 'gulsara', 'gulzada', 'aygul', 'gulshat', 'gulnar', 'gulzira', 'aida', 'ainur', 'amina',
                'asem', 'baljan', 'bibigul', 'bibi', 'dana', 'dina', 'farida', 'guljan', 'gulzat', 'jamal',
                'jamilya', 'janna', 'kamila', 'karlygash', 'laura', 'leyla', 'madina', 'mariam', 'nazira', 'roza',
                // Ruscha ayollar ismlari
                'anna', 'mariya', 'elena', 'olga', 'irina', 'svetlana', 'natalya', 'tatyana', 'oksana', 'lyudmila',
                'galina', 'nina', 'valentina', 'larisa', 'marina', 'vera', 'nadezhda', 'lyubov', 'raisa', 'tamara',
                'alla', 'inna', 'zhanna', 'viktoria', 'anastasia', 'ekaterina', 'yulia', 'daria', 'polina', 'kseniya'
            ],
            // O'zbek erkaklar ismlari
            male: [
                'jasurbek', 'aziz', 'bobur', 'davron', 'eldor', 'farrux', 'gulom', 'hamid', 'ikrom', 'javlon',
                'karim', 'laziz', 'mansur', 'nodir', 'otabek', 'pulat', 'qodir', 'rustam', 'sanjar', 'temur',
                'ulugbek', 'vali', 'xamid', 'yorqin', 'zafar', 'abdulla', 'bekzod', 'dilshod', 'erkin', 'farhod',
                'giyos', 'husan', 'islom', 'jahongir', 'komil', 'lochin', 'mirzo', 'nurali', 'oybek', 'parviz',
                'qudrat', 'ravshan', 'sherzod', 'tohir', 'umid', 'vazir', 'xasan', 'yusuf', 'zokirjon', 'akmal',
                'baxtiyor', 'doniyor', 'elbek', 'feruz', 'gayrat', 'habib', 'ilhom', 'jasur', 'kamol', 'latif',
                'muzaffar', 'nusrat', 'orifjon', 'pardabek', 'qasim', 'rahmat', 'sardor', 'timur', 'umar', 'vohid',
                // Qoraqalpoq erkaklar ismlari
                'aibek', 'alisher', 'amangeldi', 'askar', 'bahadur', 'bekzat', 'daulet', 'erlan', 'galym', 'kanat',
                'marat', 'nurlan', 'ruslan', 'serik', 'talgat', 'ulan', 'yerlan', 'zhanibek', 'abat', 'adil',
                'aidyn', 'alikhan', 'amanzhol', 'arman', 'aslan', 'azamat', 'baglan', 'bakhyt', 'berik', 'bolat',
                // Ruscha erkaklar ismlari
                'aleksandr', 'sergey', 'andrey', 'dmitriy', 'vladimir', 'aleksey', 'nikolay', 'ivan', 'mikhail', 'yuriy',
                'pavel', 'oleg', 'viktor', 'anatoliy', 'vasiliy', 'evgeniy', 'roman', 'maksim', 'artem', 'denis',
                'konstantin', 'stanislav', 'leonid', 'gennadiy', 'vadim', 'igor', 'ruslan', 'anton', 'kirill', 'daniil'
            ]
        };

        // Gender selection function
        function selectGender(gender) {
            selectedGender = gender;
            
            const maleBtn = document.getElementById('maleBtn');
            const femaleBtn = document.getElementById('femaleBtn');
            
            // Reset both buttons
            maleBtn.className = 'flex-1 px-4 py-3 border-2 border-blue-200 rounded-lg font-semibold transition-all poppins hover:border-blue-400 text-blue-600';
            femaleBtn.className = 'flex-1 px-4 py-3 border-2 border-blue-200 rounded-lg font-semibold transition-all poppins hover:border-blue-400 text-blue-600';
            
            // Highlight selected button
            if (gender === 'male') {
                maleBtn.className = 'flex-1 px-4 py-3 border-2 border-blue-600 bg-blue-600 text-white rounded-lg font-semibold transition-all poppins';
            } else {
                femaleBtn.className = 'flex-1 px-4 py-3 border-2 border-blue-600 bg-blue-600 text-white rounded-lg font-semibold transition-all poppins';
            }
        }

        // Gender detection function (fallback)
        function detectGender(name) {
            const lowerName = name.toLowerCase().trim();
            
            if (genderDatabase.female.includes(lowerName)) {
                return 'female';
            } else if (genderDatabase.male.includes(lowerName)) {
                return 'male';
            }
            
            // Fallback: check name endings for Uzbek names
            if (lowerName.endsWith('a') || lowerName.endsWith('gul') || lowerName.endsWith('noza') || 
                lowerName.endsWith('xon') || lowerName.endsWith('bibi') || lowerName.endsWith('oy')) {
                return 'female';
            } else if (lowerName.endsWith('bek') || lowerName.endsWith('jon') || lowerName.endsWith('ali') || 
                       lowerName.endsWith('din') || lowerName.endsWith('yor')) {
                return 'male';
            }
            
            return 'unknown';
        }

        // Enter site function
        function enterSite() {
            const nameInput = document.getElementById('nameInput');
            const surnameInput = document.getElementById('surnameInput');
            
            userName = nameInput.value.trim();
            userSurname = surnameInput.value.trim();
            
            if (userName === '' || userSurname === '') {
                alert('Iltimos ism va familyangizni kiriting!');
                return;
            }
            
            if (selectedGender === '') {
                alert('Iltimos jinsingizni tanlang!');
                return;
            }
            
            // Use selected gender, fallback to detection if needed
            userGender = selectedGender || detectGender(userName);
            
            // Hide welcome form and show main content
            document.getElementById('welcomeForm').style.display = 'none';
            document.getElementById('mainContent').style.display = 'block';
            
            // Update content based on gender
            updateContentByGender();
            
            // Update guest name in footer
            updateGuestName();
        }

        // Update content based on gender
        function updateContentByGender() {
            const timeElement = document.querySelector('.dancing-script.text-xl.text-blue-600.font-bold');
            const eventElement = document.querySelector('p.poppins.text-sm.text-blue-500');
            const genderElement = document.querySelector('p.poppins.text-xs.text-blue-400.mt-1');
            
            if (userGender === 'male') {
                // Update time for men (7:00 AM)
                if (currentLanguage === 'latin') {
                    timeElement.textContent = '23 Avgust, 2025 - 07:00';
                    eventElement.textContent = 'Amru Maruf';
                    genderElement.textContent = 'Erkaklar va Bolalar uchun';
                } else {
                    timeElement.textContent = '23 Август, 2025 - 07:00';
                    eventElement.textContent = 'Амру Маруф';
                    genderElement.textContent = 'Эркаклар ва Болалар учун';
                }
            } else {
                // Keep original time for women (12:00 PM)
                if (currentLanguage === 'latin') {
                    timeElement.textContent = '23 Avgust, 2025 - 12:00';
                    eventElement.textContent = 'Qiz bazmi';
                    genderElement.textContent = 'Ayollar va Qizlar uchun';
                } else {
                    timeElement.textContent = '23 Август, 2025 - 12:00';
                    eventElement.textContent = 'Қиз базми';
                    genderElement.textContent = 'Аёллар ва Қизлар учун';
                }
            }
        }

        // Update guest name function
        function updateGuestName() {
            const guestNameElement = document.getElementById('guestName');
            const invitationTextElement = document.getElementById('invitationText');
            const dearGuestTitle = document.getElementById('dearGuestTitle');
            
            if (currentLanguage === 'latin') {
                guestNameElement.textContent = `Xurmatli Mehmon ${userSurname} ${userName} !`;
                dearGuestTitle.textContent = `Aziz mehmon ${userSurname} ${userName} !`;
                invitationTextElement.textContent = 'Sizni farzandlarimizning to\'y marosimida intiqlik bilan kutamiz';
            } else {
                guestNameElement.textContent = `Ҳурматли Меҳмон ${userSurname} ${userName} !`;
                dearGuestTitle.textContent = `Азиз меҳмон ${userSurname} ${userName} !`;
                invitationTextElement.textContent = 'Сизни фарзандларимизнинг тўй маросимида интиқлик билан кутамиз';
            }
        }

        // Timer function
        function updateTimer() {
            let weddingDate;
            
            // Set different times based on gender
            if (userGender === 'male') {
                weddingDate = new Date('2025-08-23T07:00:00'); // 7:00 AM for men
            } else {
                weddingDate = new Date('2025-08-23T12:00:00'); // 12:00 PM for women
            }
            
            const now = new Date();
            const difference = weddingDate - now;
            
            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((difference % (1000 * 60)) / 1000);
                
                document.getElementById('days').textContent = days.toString().padStart(2, '0');
                document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
                document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
                document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
            } else {
                document.getElementById('days').textContent = '00';
                document.getElementById('hours').textContent = '00';
                document.getElementById('minutes').textContent = '00';
                document.getElementById('seconds').textContent = '00';
            }
        }
        
        // Update timer every second
        setInterval(updateTimer, 1000);
        updateTimer();

        // Sticker rain effect
        const stickers = ['✨', '🎊', '🎉', '🕊️', '💍'];
        
        function createStickerRain() {
            const container = document.getElementById('stickerRain');
            const sticker = document.createElement('div');
            sticker.className = 'sticker-rain';
            sticker.textContent = stickers[Math.floor(Math.random() * stickers.length)];
            sticker.style.left = Math.random() * 100 + 'vw';
            sticker.style.fontSize = (Math.random() * 20 + 15) + 'px';
            sticker.style.animationDuration = (Math.random() * 3 + 2) + 's';
            sticker.style.opacity = Math.random() * 0.7 + 0.3;
            
            container.appendChild(sticker);
            
            setTimeout(() => {
                sticker.remove();
            }, 5000);
        }
        
        // Start sticker rain
        setInterval(createStickerRain, 300);
        
        // Language translations
        const translations = {
            latin: {
                'wedding-title': "To'y Taklifnomasi",
                'welcome-text': "Bizning baxtli kunimizga xush kelibsiz!",

                'countdown-title': "To'ygacha qolgan vaqt",
                'day': "Kun",
                'hour': "Soat",
                'minute': "Daqiqa",
                'second': "Soniya",
                'date-time': "Sana va Vaqt",
                'evening': "Qiz bazmi",
                'address': "Manzil",
                'dear-guests': "Aziz mehmon !",
                'invitation-text': "Bizning eng baxtli kunimizni siz va sizning oilangiz bilan nishonlashni xohlaymiz! Sizning borligingiz to'yimizni yanada chiroyli va esda qolarli qiladi!",
                'rsvp-title': "📝 Javobingizni yuboring",
                'confirm-btn': "✅ Albatta boraman",
                'map-title': "To'yxona manzillari:",
                'respect-text': "Xurmat va ehtirom ila",
                'family-name': "Yusufali Xoliyarovlar xonadoni",
                'with-love': "Xurmatli Mehmon",
                'modal-title': "Ajoyib!",
                'modal-message': "Sizni to'y marosimimizda ko'rishimizdan xursandmiz 😊"
            },
            cyrillic: {
                'wedding-title': "Тўй Таклифномаси",
                'welcome-text': "Бизнинг бахтли кунимизга хуш келибсиз!",

                'countdown-title': "Тўйгача қолган вақт",
                'day': "Кун",
                'hour': "Соат",
                'minute': "Дақиқа",
                'second': "Сония",
                'date-time': "Сана ва Вақт",
                'evening': "Қиз базми",
                'address': "Манзил",
                'dear-guests': "Азиз меҳмон !",
                'invitation-text': "Бизнинг энг бахтли кунимизни сиз ва сизнинг оилангиз билан нишонлашни хоҳлаймиз! Сизнинг борлигингиз тўйимизни янада чиройли ва эсда қоларли қилади!",
                'rsvp-title': "📝 Жавобингизни юборинг",
                'confirm-btn': "✅ Албатта бораман",
                'map-title': "Тўйхона манзиллари:",
                'respect-text': "Ҳурмат ва эҳтиром ила",
                'family-name': "Юсуфали Холияровлар хонадони",
                'with-love': "Ҳурматли Меҳмон",
                'modal-title': "Ажойиб!",
                'modal-message': "Сизни тўй маросимимизда кўришимиздан хурсандмиз 😊"
            }
        };

        let currentLanguage = 'latin';

        function switchLanguage(lang) {
            currentLanguage = lang;
            
            // Update button styles
            const latinBtn = document.getElementById('latinBtn');
            const cyrillicBtn = document.getElementById('cyrillicBtn');
            
            if (lang === 'latin') {
                latinBtn.className = 'px-4 py-2 rounded-md text-sm font-medium transition-colors bg-blue-600 text-white';
                cyrillicBtn.className = 'px-4 py-2 rounded-md text-sm font-medium transition-colors text-blue-600 hover:bg-blue-50';
            } else {
                cyrillicBtn.className = 'px-4 py-2 rounded-md text-sm font-medium transition-colors bg-blue-600 text-white';
                latinBtn.className = 'px-4 py-2 rounded-md text-sm font-medium transition-colors text-blue-600 hover:bg-blue-50';
            }
            
            // Update all text elements
            const elements = document.querySelectorAll('[data-text]');
            elements.forEach(element => {
                const key = element.getAttribute('data-text');
                if (translations[lang][key]) {
                    element.textContent = translations[lang][key];
                }
            });
            
            // Update specific elements that don't have data-text attributes
            document.querySelector('h1').textContent = translations[lang]['wedding-title'];
            document.querySelector('.dancing-script + p').textContent = translations[lang]['welcome-text'];
            document.querySelector('p.dancing-script.text-xl.text-blue-600.font-semibold').textContent = translations[lang]['love-story'];
            document.querySelector('h3.dancing-script.text-2xl.font-bold.text-blue-800').textContent = translations[lang]['countdown-title'];
            
            // Update timer labels
            const timerLabels = document.querySelectorAll('.text-sm.text-blue-500');
            timerLabels[0].textContent = translations[lang]['day'];
            timerLabels[1].textContent = translations[lang]['hour'];
            timerLabels[2].textContent = translations[lang]['minute'];
            timerLabels[3].textContent = translations[lang]['second'];
            
            // Update other elements
            document.querySelectorAll('h3.poppins.font-semibold.text-blue-800')[0].textContent = translations[lang]['date-time'];
            document.querySelectorAll('h3.poppins.font-semibold.text-blue-800')[1].textContent = translations[lang]['address'];
            document.querySelector('p.poppins.text-sm.text-blue-500').textContent = translations[lang]['evening'];
            // Update guest name when language changes (this will set the personalized greeting)
            updateGuestName();
            document.getElementById('invitationMessage').textContent = translations[lang]['invitation-text'];
            document.querySelector('p.poppins.text-blue-700.font-semibold').textContent = translations[lang]['respect-text'];
            document.querySelector('p.dancing-script.text-lg.text-blue-600.font-bold').textContent = translations[lang]['family-name'];
            document.querySelector('p.dancing-script.text-xl.text-blue-700').textContent = translations[lang]['with-love'];
            
            // Update content based on gender and language
            updateContentByGender();
            
            // Update guest name when language changes
            updateGuestName();
        }

        function confirmAttendance(response) {
            const modal = document.getElementById('confirmationModal');
            const modalEmoji = document.getElementById('modalEmoji');
            const modalTitle = document.getElementById('modalTitle');
            const modalMessage = document.getElementById('modalMessage');
            const mapButtons = document.getElementById('mapButtons');
            
            modalEmoji.textContent = '🎉';
            modalTitle.textContent = translations[currentLanguage]['modal-title'];
            modalMessage.textContent = translations[currentLanguage]['modal-message'];
            
            // Show map buttons
            mapButtons.classList.remove('hidden');
            
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }
        
        function closeModal() {
            const modal = document.getElementById('confirmationModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }
        
        // Click effect - more stickers
        document.addEventListener('click', function(e) {
            if (e.target.tagName !== 'BUTTON' && e.target.tagName !== 'A') {
                for(let i = 0; i < 3; i++) {
                    setTimeout(() => {
                        const sparkle = document.createElement('div');
                        sparkle.textContent = stickers[Math.floor(Math.random() * stickers.length)];
                        sparkle.style.position = 'fixed';
                        sparkle.style.left = (e.clientX + Math.random() * 40 - 20) + 'px';
                        sparkle.style.top = (e.clientY + Math.random() * 40 - 20) + 'px';
                        sparkle.style.pointerEvents = 'none';
                        sparkle.style.fontSize = '20px';
                        sparkle.style.zIndex = '1000';
                        sparkle.style.animation = 'sparkleUp 1.5s ease-out forwards';
                        
                        document.body.appendChild(sparkle);
                        
                        setTimeout(() => {
                            sparkle.remove();
                        }, 1500);
                    }, i * 100);
                }
            }
        });
        
        // Add sparkle animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes sparkleUp {
                0% { transform: translateY(0) scale(1) rotate(0deg); opacity: 1; }
                100% { transform: translateY(-60px) scale(0.3) rotate(180deg); opacity: 0; }
            }
        `;
        document.head.appendChild(style);
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96c6ce24c78c5fc4',t:'MTc1NDczNzgwOC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

