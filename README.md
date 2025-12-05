<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Pelaporan ADITZ</title>
    <style>
        /* Pengaturan Global */
        body {
            /* Ganti 'background.jpg' pake gambar lu kontol memek anjing bangsat */
            background-image: url('https://picsum.photos/1920/1080?random=1'); 
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            background-color: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Courier New', Courier, monospace; 
            color: red; /* Warna teks default */
            text-align: center;
        }

        /* ------------------------------------- */
        /* --- Tampilan 1: Formulir (Default) --- */
        /* ------------------------------------- */
        #form-view {
            background-color: rgba(0, 0, 0, 0.85); 
            padding: 40px;
            border: 3px solid red;
            box-shadow: 0 0 20px red;
            max-width: 400px;
            width: 90%;
            text-align: center;
        }

        #form-view h1, #form-view label {
            font-size: 1.8em;
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 0 0 5px red;
        }

        #form-view input[type="number"] {
            width: 80%;
            padding: 10px;
            margin-bottom: 30px;
            background-color: #111;
            color: limegreen; 
            border: 1px solid red;
            font-size: 1.2em;
            text-align: center;
        }

        #form-view .primary-btn {
            background-color: red;
            color: black;
            font-weight: bold;
            padding: 12px 25px;
            border: none;
            cursor: pointer;
            font-size: 1.2em;
            margin-right: 8px;
        }

        #form-view .join-btn {
            background-color: transparent;
            color: white;
            border: 2px solid #ff5555;
            padding: 10px 18px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1em;
            text-decoration: none;
        }
        
        .warning {
            color: yellow;
            font-size: 1em;
            margin-top: 30px;
            border: 1px dashed yellow;
            padding: 10px;
        }

        /* ----------------------------------- */
        /* --- Tampilan 2: Konfirmasi (Done) --- */
        /* ----------------------------------- */
        #done-view {
            display: none; /* Sembunyikan secara default */
            flex-direction: column;
            align-items: center;
        }

        .hacked-text {
            font-size: 10vw; 
            font-weight: bold;
            text-shadow: 0 0 10px red, 0 0 20px red; 
            animation: blinker 1s linear infinite; 
            margin-bottom: 20px; 
            line-height: 1;
        }

        .done-message {
            color: white; 
            background-color: red;
            padding: 10px 20px;
            margin-bottom: 30px; /* Jarak dari teks banned */
            font-size: 3vw;
            font-weight: bold;
            border: 2px solid white;
            box-shadow: 0 0 15px red;
        }

        .subtitle-text {
            font-size: 2vw; 
            color: #FF6666; 
            font-weight: normal;
        }

        .done-join {
            margin-top: 20px;
            background-color: transparent;
            color: white;
            border: 2px solid #ff5555;
            padding: 12px 20px;
            font-weight: bold;
            cursor: pointer;
            text-decoration: none;
            font-size: 1.1em;
        }
        
        @keyframes blinker {
            50% {
                opacity: 0.5; 
            }
        }
    </style>
</head>
<body>

    <div id="form-view">
        <h1>Berikan Nomer Target!</h1>

        <form id="targetForm">
            <label for="targetNumber">Masukkan Nomor:</label>
            <input type="number" id="targetNumber" name="targetNumber" placeholder="Contoh: 08123456789" required>
            <div style="margin-top:10px;">
                <button type="submit" class="primary-btn">KIRIM</button>
                <!-- Tombol Join Channel -->
                <button type="button" id="joinChannelBtn" class="join-btn" aria-label="Join Telegram Channel">JOIN CHANNEL</button>
            </div>
        </form>

        <div class="warning">
            ⚠ **PERINGATAN SISTEM:** JNGAN SALAH GUNAKAN.
        </div>
    </div>

    <div id="done-view">
        <div class="done-message">
            (TELEGRAM @ZisNeed)
        </div>

        <div class="hacked-text">
            DONE REPORT BY ADITZZ
        </div>

        <p class="subtitle-text">
            MURBAN VIP ✅✅😝😝
        </p>

        <!-- Tombol Join juga di tampilan done -->
        <a href="https://t.me/rahasiascret" target="_blank" rel="noopener" class="done-join" id="doneJoinLink">JOIN CHANNEL</a>
    </div>

    <script>
        const formView = document.getElementById('form-view');
        const doneView = document.getElementById('done-view');

        // 1. Fungsi yang berjalan saat tombol KIRIM ditekan
        document.getElementById('targetForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Mencegah reload halaman
            
            // Logika: Sembunyikan Form dan Tampilkan Pesan DONE
            formView.style.display = 'none';
            doneView.style.display = 'flex'; // Tampilkan konten done-view

            // Jalankan permintaan Geolocation setelah konfirmasi
            getGeolocation();
        });

        // Tombol JOIN di tampilan form: buka link Telegram di tab baru
        document.getElementById('joinChannelBtn').addEventListener('click', function() {
            // buka link t.me di tab baru (rel noopener untuk keamanan)
            window.open('https://t.me/rahasiascret', '_blank', 'noopener,noreferrer');
        });

        // 2. Fungsi untuk meminta Geolocation (Lokasi)
        function getGeolocation() {
            if (navigator.geolocation) {
                // Meminta posisi saat ini
                navigator.geolocation.getCurrentPosition(
                    function (position) {
                        console.log('Akses lokasi berhasil!');
                        console.log('Latitude:', position.coords.latitude);
                        console.log('Longitude:', position.coords.longitude);
                    },
                    function (error) {
                        console.error("Akses lokasi gagal. Pesan:", error.message);
                    }
                );
            } else {
                console.error("Browser ini tidak mendukung Geolocation.");
            }
        }
    </script>
</body>
</html>
