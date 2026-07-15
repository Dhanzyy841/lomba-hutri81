<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pendaftaran Lomba HUT RI</title>
    <style>
        :root {
            --primary-color: #d90429;
            --primary-hover: #ef233c;
            --secondary-color: #2b2d42;
            --accent-color: #ffb703;
            --glass-bg: rgba(255, 255, 255, 0.95);
            --glass-shadow: 0 0 40px rgba(217, 4, 41, 0.25), 0 15px 35px rgba(0, 0, 0, 0.2);
            --text-color: #2b2d42;
            --border-color: #cbd5e1;
            --success-color: #2ec4b6;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            /* PERUBAHAN UTAMA: Memastikan background gambar menutup penuh layar */
            background-image: url('background pendaftaran.jpeg');
            background-size: cover;          /* Gambar dipaksa memenuhi seluruh area */
            background-position: center;      /* Gambar diposisikan pas di tengah-tengah */
            background-repeat: no-repeat;     /* Mencegah gambar berulang/pecah */
            background-attachment: fixed;     /* Efek parallax di mana background mengunci saat di-scroll */
            color: var(--text-color);
            min-height: 100vh;
            width: 100vw;                     /* Memastikan lebar body penuh */
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 60px 20px;
            position: relative;
            overflow-x: hidden;               /* Menghindari scrollbar horizontal yang mengganggu */
        }

        /* Overlay Gradasi Penuh di Atas Background Agar Kontras & Mencolok */
        body::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.35) 0%, rgba(139, 10, 10, 0.25) 100%);
            z-index: 0;
            pointer-events: none;
        }

        /* Container Formulir */
        .form-container, .admin-container {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            width: 100%;
            max-width: 650px;
            padding: 40px;
            border-radius: 24px;
            box-shadow: var(--glass-shadow);
            border: 1px solid rgba(255, 255, 255, 0.6);
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            z-index: 1;
        }

        .admin-container {
            max-width: 900px;
            display: none;
        }

        /* Dekorasi warna gradasi merah ke putih tebal dengan shadow 3D */
        .form-container::before, .admin-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 14px;
            background: linear-gradient(90deg, #ff002b 0%, #ffffff 100%);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.25), 
                        0 8px 30px rgba(255, 0, 43, 0.4);
            z-index: 5;
        }

        .header {
            text-align: center;
            margin-bottom: 35px;
            position: relative;
        }

        .header .icon-badge {
            background: rgba(255, 0, 43, 0.12);
            color: #ff002b;
            width: 65px;
            height: 65px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px auto;
            font-size: 30px;
            border: 2px solid rgba(255, 0, 43, 0.25);
            box-shadow: 0 4px 10px rgba(255, 0, 43, 0.15);
        }

        .header h1 {
            font-size: 1.9rem;
            color: var(--secondary-color);
            font-weight: 800;
            margin-bottom: 12px;
            letter-spacing: -0.5px;
        }

        .header p {
            font-size: 0.95rem;
            color: #475569;
            line-height: 1.6;
            font-weight: 500;
        }

        .section-title {
            font-size: 1.05rem;
            color: #ff002b;
            text-transform: uppercase;
            font-weight: 700;
            letter-spacing: 1px;
            margin: 35px 0 15px 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .section-title::after {
            content: '';
            flex: 1;
            height: 2px;
            background: linear-gradient(90deg, rgba(255, 0, 43, 0.3), transparent);
        }

        .form-group {
            margin-bottom: 24px;
        }

        label {
            display: block;
            font-weight: 700;
            margin-bottom: 8px;
            font-size: 0.9rem;
            color: var(--secondary-color);
        }

        input[type="text"],
        input[type="number"],
        input[type="password"],
        select {
            width: 100%;
            padding: 14px 16px;
            border: 2px solid var(--border-color);
            border-radius: 12px;
            font-size: 0.95rem;
            color: var(--secondary-color);
            transition: all 0.25s ease;
            background-color: rgba(255, 255, 255, 0.85);
            font-weight: 500;
        }

        input::placeholder {
            color: #94a3b8;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #ff002b;
            background-color: #ffffff;
            box-shadow: 0 0 0 4px rgba(255, 0, 43, 0.15);
        }

        .radio-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .radio-card {
            border: 2px solid var(--border-color);
            border-radius: 12px;
            padding: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            cursor: pointer;
            transition: all 0.25s ease;
            background-color: rgba(255, 255, 255, 0.85);
            font-weight: 600;
            font-size: 0.95rem;
        }

        .radio-card input {
            accent-color: #ff002b;
            width: 18px;
            height: 18px;
            cursor: pointer;
        }

        .radio-card:hover {
            border-color: rgba(255, 0, 43, 0.5);
            background-color: rgba(255, 0, 43, 0.02);
        }

        .radio-card.selected {
            border-color: #ff002b;
            background-color: rgba(255, 0, 43, 0.06);
            color: #ff002b;
            box-shadow: 0 4px 10px rgba(255, 0, 43, 0.1);
        }

        .dynamic-section {
            background-color: rgba(255, 0, 43, 0.03);
            border: 2px dashed rgba(255, 0, 43, 0.3);
            padding: 22px;
            border-radius: 16px;
            margin-top: 25px;
            display: none;
            animation: slideDown 0.35s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .dynamic-section.active {
            display: block;
        }

        .team-member-input {
            margin-bottom: 12px;
        }

        .checkbox-container {
            display: flex;
            align-items: flex-start;
            gap: 12px;
            margin: 30px 0;
            cursor: pointer;
            font-size: 0.9rem;
            line-height: 1.5;
            font-weight: 600;
            color: #334155;
        }

        .checkbox-container input {
            accent-color: #ff002b;
            width: 20px;
            height: 20px;
            margin-top: 2px;
            flex-shrink: 0;
            cursor: pointer;
        }

        .btn-submit {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #ff002b 0%, #c30022 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 25px rgba(255, 0, 43, 0.35);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 30px rgba(255, 0, 43, 0.5);
            filter: brightness(1.1);
        }

        .btn-toggle-mode {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.85);
            color: var(--secondary-color);
            border: 1px solid rgba(0, 0, 0, 0.1);
            padding: 10px 18px;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 700;
            font-size: 0.85rem;
            transition: all 0.25s ease;
            z-index: 10;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .btn-toggle-mode:hover {
            background: var(--secondary-color);
            color: white;
            transform: translateY(-1px);
        }

        .table-responsive {
            overflow-x: auto;
            margin-top: 20px;
            background: #ffffff;
            border-radius: 12px;
            border: 1px solid rgba(0,0,0,0.08);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
            text-align: left;
        }

        th, td {
            padding: 14px 16px;
            border-bottom: 1px solid #f1f5f9;
        }

        th {
            background-color: #f8fafc;
            color: #475569;
            font-weight: 700;
        }

        tr:hover {
            background-color: #f8fafc;
        }

        .admin-actions {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .btn-action {
            padding: 10px 16px;
            border-radius: 8px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.2s ease;
        }

        .btn-danger {
            background-color: #ff002b;
            color: white;
        }

        .btn-danger:hover {
            background-color: #c30022;
        }

        .btn-success {
            background-color: var(--success-color);
            color: white;
        }

        .btn-success:hover {
            filter: brightness(0.95);
        }

        .no-data {
            text-align: center;
            padding: 30px;
            color: #94a3b8;
            font-style: italic;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 600px) {
            body {
                padding: 80px 10px 20px 10px;
            }
            .form-container, .admin-container {
                padding: 30px 20px;
                border-radius: 20px;
            }
            .header h1 {
                font-size: 1.5rem;
            }
            .radio-grid {
                grid-template-columns: 1fr;
                gap: 10px;
            }
            .btn-toggle-mode {
                top: 15px;
                right: 50%;
                transform: translateX(50%);
                width: calc(100% - 20px);
                text-align: center;
            }
        }
    </style>
</head>
<body>

<button class="btn-toggle-mode" id="btnToggle" onclick="toggleMode()">Menu Panitia/Admin 🔒</button>

<div class="form-container" id="userFormSection">
    <div class="header">
        <div class="icon-badge">🇮🇩</div>
        <h1>Formulir Pendaftaran Lomba</h1>
        <p>Silakan isi data diri dengan benar dan pilih kategori serta lomba yang ingin diikuti.</p>
    </div>

    <form id="lombaForm" onsubmit="handleSubmit(event)">
        <div class="section-title">Data Diri Peserta</div>
        
        <div class="form-group">
            <label for="nama">Nama Lengkap</label>
            <input type="text" id="nama" required placeholder="Masukkan nama lengkap pendaftar">
        </div>

        <div class="form-group">
            <label for="umur">Umur (Tahun)</label>
            <input type="number" id="umur" min="1" max="100" required placeholder="Contoh: 9">
        </div>

        <div class="form-group">
            <label>Jenis Kelamin</label>
            <div class="radio-grid">
                <label class="radio-card" id="label-l">
                    <input type="radio" name="jk" value="Laki-laki" required id="radio-l" onclick="selectGender('Laki-laki')"> 
                    Laki-laki
                </label>
                <label class="radio-card" id="label-p">
                    <input type="radio" name="jk" value="Perempuan" id="radio-p" onclick="selectGender('Perempuan')"> 
                    Perempuan
                </label>
            </div>
        </div>

        <div class="section-title">Kategori & Lomba</div>

        <div class="form-group">
            <label for="kategori">Pilih Kategori Usia</label>
            <select id="kategori" required onchange="handleKategoriChange()">
                <option value="" disabled selected>-- Klik untuk memilih kategori --</option>
                <option value="k1">Kategori 1 (Usia 3–4 Tahun)</option>
                <option value="k2">Kategori 2 (Usia 5–7 Tahun)</option>
                <option value="k3">Kategori 3 (Usia 8–10 Tahun)</option>
                <option value="kremaja">Kategori Remaja</option>
                <option value="kibu">Kategori Ibu-Ibu</option>
            </select>
        </div>

        <div class="form-group" id="lombaWrapper" style="display:none;">
            <label for="lomba">Pilih Jenis Lomba</label>
            <select id="lomba" required onchange="handleLombaChange()">
            </select>
        </div>

        <div id="teamSection" class="dynamic-section">
            <div class="section-title" style="margin-top:0; font-size:1rem; color: var(--secondary-color);">Data Kelompok / Tim</div>
            <div class="form-group">
                <label for="namaTim">Nama Tim</label>
                <input type="text" id="namaTim" placeholder="Masukkan nama kelompok/tim">
            </div>
            <div class="form-group">
                <label>Nama Anggota Tim (Selain Pendaftar Utama)</label>
                <div id="anggotaContainer">
                </div>
            </div>
        </div>

        <label class="checkbox-container">
            <input type="checkbox" required>
            <span>Saya menyatakan bahwa data yang saya isi sudah benar dan bersedia mengikuti seluruh peraturan perlombaan HUT RI.</span>
        </label>

        <button type="submit" class="btn-submit">Kirim Pendaftaran 🚀</button>
    </form>
</div>

<div class="admin-container" id="adminSection">
    <div class="header">
        <div class="icon-badge">📊</div>
        <h1>Data Pendaftaran Peserta (Admin)</h1>
        <p>Halaman khusus panitia untuk memonitor, mengunduh, serta menghapus pendaftar.</p>
    </div>

    <div id="adminLoginArea">
        <div class="form-group">
            <label for="adminPassword">Password Admin</label>
            <input type="password" id="adminPassword" placeholder="Masukkan sandi keamanan khusus panitia">
        </div>
        <button class="btn-submit" onclick="loginAdmin()">Masuk ke Panel Admin</button>
    </div>

    <div id="adminPanelArea" style="display: none;">
        <div class="table-responsive">
            <table id="pesertaTable">
                <thead>
                    <tr>
                        <th>No</th>
                        <th>Nama Peserta</th>
                        <th>Umur</th>
                        <th>JK</th>
                        <th>Kategori</th>
                        <th>Lomba</th>
                        <th>Data Kelompok</th>
                        <th>Aksi</th>
                    </tr>
                </thead>
                <tbody id="pesertaTableBody">
                </tbody>
            </table>
        </div>

        <div class="admin-actions">
            <button class="btn-action btn-success" onclick="exportToCSV()">Unduh Data (Format CSV / Excel)</button>
            <button class="btn-action btn-danger" onclick="clearAllData()">Hapus Semua Data</button>
        </div>
    </div>
</div>

<script>
    const dataLomba = {
        k1: [
            { id: "mewarnai", nama: "Mewarnai (17 Agustus)", beregu: false },
            { id: "sepeda_hias", nama: "Sepeda Hias (17 Agustus)", beregu: false },
            { id: "makan_kerupuk_1", nama: "Makan Kerupuk", beregu: false }
        ],
        k2: [
            { id: "tusuk_balon", nama: "Tusuk Balon (15 Agustus)", beregu: false },
            { id: "sedotan_botol", nama: "Masukin Sedotan ke Botol (15 Agustus)", beregu: false },
            { id: "bola_keranjang", nama: "Masukin Bola ke Keranjang (16 Agustus)", beregu: false },
            { id: "makan_kerupuk_2", nama: "Makan Kerupuk (16 Agustus)", beregu: false }
        ],
        k3: [
            { id: "estafet_air_3", nama: "Estafet Air (Lomba Kelompok) – 15 Agustus", beregu: true, anggota: 5 },
            { id: "gurita_3", nama: "Gurita (5 orang per tim) – 16 Agustus", beregu: true, anggota: 5 },
            { id: "ambil_koin", nama: "Ambil Koin di Buah – 16 Agustus", beregu: false },
            { id: "pakai_baju", nama: "Lomba Pakai Baju (Kemeja) – 15 Agustus", beregu: false }
        ],
        kremaja: [
            { id: "gurita_rem", nama: "Gurita (5 orang per tim) – 16 Agustus", beregu: true, anggota: 5 },
            { id: "estafet_air_rem", nama: "Estafet Air (5 orang per tim) – 15 Agustus", beregu: true, anggota: 5 },
            { id: "futsal_rem", nama: "Mini Futsal (5 orang per tim) – 15–17 Agustus", beregu: true, anggota: 5 },
            { id: "balap_karung", nama: "Balap Karung – 16 Agustus", beregu: false }
        ],
        kibu: [
            { id: "gurita_ibu", nama: "Gurita (5 orang per tim) – 17 Agustus", beregu: true, anggota: 5 },
            { id: "voli_jumbo", nama: "Voli Bola Jumbo – 17 Agustus", beregu: true, anggota: 5 },
            { id: "suit_kardus", nama: "Suit Kardus – 17 Agustus", beregu: false }
        ]
    };

    const namaKategori = {
        k1: "Kategori 1 (3-4 Th)",
        k2: "Kategori 2 (5-7 Th)",
        k3: "Kategori 3 (8-10 Th)",
        kremaja: "Kategori Remaja",
        kibu: "Kategori Ibu-Ibu"
    };

    let isUserMode = true;
    let isAdminLoggedIn = false;

    function toggleMode() {
        const userSection = document.getElementById("userFormSection");
        const adminSection = document.getElementById("adminSection");
        const toggleBtn = document.getElementById("btnToggle");

        if (isUserMode) {
            userSection.style.display = "none";
            adminSection.style.display = "block";
            toggleBtn.textContent = "Kembali ke Formulir Pendaftaran 📝";
            isUserMode = false;
            
            if (isAdminLoggedIn) {
                document.getElementById("adminLoginArea").style.display = "none";
                document.getElementById("adminPanelArea").style.display = "block";
                loadAdminData();
            }
        } else {
            userSection.style.display = "block";
            adminSection.style.display = "none";
            toggleBtn.textContent = "Menu Panitia/Admin 🔒";
            isUserMode = true;
        }
    }

    function loginAdmin() {
        const passInput = document.getElementById("adminPassword");
        if (passInput.value === "HUT RI 81") {
            isAdminLoggedIn = true;
            document.getElementById("adminLoginArea").style.display = "none";
            document.getElementById("adminPanelArea").style.display = "block";
            passInput.value = "";
            loadAdminData();
        } else {
            alert("❌ Password salah! Silakan hubungi ketua panitia.");
        }
    }

    function selectGender(gender) {
        const labelL = document.getElementById('label-l');
        const labelP = document.getElementById('label-p');
        if (gender === 'Laki-laki') {
            labelL.classList.add('selected');
            labelP.classList.remove('selected');
        } else {
            labelP.classList.add('selected');
            labelL.classList.remove('selected');
        }
    }

    function handleKategoriChange() {
        const kategoriSelect = document.getElementById("kategori");
        const lombaWrapper = document.getElementById("lombaWrapper");
        const lombaSelect = document.getElementById("lomba");
        const selectedKategori = kategoriSelect.value;

        lombaSelect.innerHTML = '<option value="" disabled selected>-- Pilih Lomba --</option>';
        document.getElementById("teamSection").classList.remove("active");

        if (selectedKategori && dataLomba[selectedKategori]) {
            dataLomba[selectedKategori].forEach(lomba => {
                const option = document.createElement("option");
                option.value = lomba.id;
                option.textContent = lomba.nama;
                option.dataset.beregu = lomba.beregu;
                option.dataset.anggota = lomba.anggota || 0;
                lombaSelect.appendChild(option);
            });
            lombaWrapper.style.display = "block";
        } else {
            lombaWrapper.style.display = "none";
        }
    }

    function handleLombaChange() {
        const lombaSelect = document.getElementById("lomba");
        const selectedOption = lombaSelect.options[lombaSelect.selectedIndex];
        
        const isBeregu = selectedOption.dataset.beregu === "true";
        const jumlahAnggota = parseInt(selectedOption.dataset.anggota);
        
        const teamSection = document.getElementById("teamSection");
        const anggotaContainer = document.getElementById("anggotaContainer");
        const namaTimInput = document.getElementById("namaTim");

        if (isBeregu) {
            teamSection.classList.add("active");
            namaTimInput.required = true;
            anggotaContainer.innerHTML = "";

            for (let i = 1; i < jumlahAnggota; i++) {
                const input = document.createElement("input");
                input.type = "text";
                input.className = "team-member-input";
                input.placeholder = `Nama Anggota ${i + 1}`;
                input.required = true;
                anggotaContainer.appendChild(input);
            }
        } else {
            teamSection.classList.remove("active");
            namaTimInput.required = false;
            anggotaContainer.innerHTML = "";
            namaTimInput.value = "";
        }
    }

    function getStoredData() {
        const data = localStorage.getItem("pendaftarLomba");
        return data ? JSON.parse(data) : [];
    }

    function saveStoredData(data) {
        localStorage.setItem("pendaftarLomba", JSON.stringify(data));
    }

    function handleSubmit(event) {
        event.preventDefault();

        const nama = document.getElementById("nama").value;
        const umur = document.getElementById("umur").value;
        const jk = document.querySelector('input[name="jk"]:checked').value;
        const kategoriVal = document.getElementById("kategori").value;
        const lombaSelect = document.getElementById("lomba");
        const lombaText = lombaSelect.options[lombaSelect.selectedIndex].text;

        const isBeregu = lombaSelect.options[lombaSelect.selectedIndex].dataset.beregu === "true";
        let infoKelompok = "Individu";

        if (isBeregu) {
            const namaTim = document.getElementById("namaTim").value;
            const anggotaInputs = document.querySelectorAll(".team-member-input");
            let anggotaList = [];
            anggotaInputs.forEach(input => {
                if(input.value.trim() !== "") {
                    anggotaList.push(input.value.trim());
                }
            });
            infoKelompok = `Tim: ${namaTim} (Anggota: ${anggotaList.join(", ")})`;
        }

        const pendaftarBaru = {
            id: Date.now(),
            nama: nama,
            umur: umur,
            jk: jk,
            kategori: namaKategori[kategoriVal] || kategoriVal,
            lomba: lombaText,
            kelompok: infoKelompok
        };

        const listPendaftar = getStoredData();
        listPendaftar.push(pendaftarBaru);
        saveStoredData(listPendaftar);

        alert("🎉 Selamat! Pendaftaran Anda berhasil dikirim dan disimpan.");
        
        document.getElementById("lombaForm").reset();
        document.getElementById("lombaWrapper").style.display = "none";
        document.getElementById("teamSection").classList.remove("active");
        document.getElementById('label-l').classList.remove('selected');
        document.getElementById('label-p').classList.remove('selected');
    }

    function loadAdminData() {
        const listPendaftar = getStoredData();
        const tbody = document.getElementById("pesertaTableBody");
        tbody.innerHTML = "";

        if (listPendaftar.length === 0) {
            tbody.innerHTML = `<tr><td colspan="8" class="no-data">Belum ada peserta yang mendaftar.</td></tr>`;
            return;
        }

        listPendaftar.forEach((peserta, index) => {
            const row = document.createElement("tr");
            row.innerHTML = `
                <td>${index + 1}</td>
                <td><strong>${peserta.nama}</strong></td>
                <td>${peserta.umur} Th</td>
                <td>${peserta.jk}</td>
                <td>${peserta.kategori}</td>
                <td>${peserta.lomba}</td>
                <td><small>${peserta.kelompok}</small></td>
                <td>
                    <button class="btn-action btn-danger" style="padding: 5px 10px; font-size: 0.75rem;" onclick="deletePeserta(${peserta.id})">Hapus</button>
                </td>
            `;
            tbody.appendChild(row);
        });
    }

    function deletePeserta(id) {
        if (confirm("Apakah Anda yakin ingin menghapus peserta ini?")) {
            let listPendaftar = getStoredData();
            listPendaftar = listPendaftar.filter(p => p.id !== id);
            saveStoredData(listPendaftar);
            loadAdminData();
        }
    }

    function clearAllData() {
        if (confirm("⚠️ PERINGATAN! Anda akan menghapus seluruh data pendaftaran secara permanen. Lanjutkan?")) {
            localStorage.removeItem("pendaftarLomba");
            loadAdminData();
        }
    }

    function exportToCSV() {
        const listPendaftar = getStoredData();
        if (listPendaftar.length === 0) {
            alert("Tidak ada data untuk diunduh.");
            return;
        }

        let csvContent = "data:text/csv;charset=utf-8,";
        csvContent += "No,Nama Lengkap,Umur,Jenis Kelamin,Kategori Usia,Nama Lomba,Info Kelompok\n";

        listPendaftar.forEach((p, index) => {
            const namaClean = p.nama.replace(/,/g, " ");
            const kelompokClean = p.kelompok.replace(/,/g, " | ");
            const row = `${index + 1},${namaClean},${p.umur},${p.jk},${p.kategori},${p.lomba},${kelompokClean}\n`;
            csvContent += row;
        });

        const encodedUri = encodeURI(csvContent);
        const link = document.createElement("a");
        link.setAttribute("href", encodedUri);
        link.setAttribute("download", "pendaftar_lomba_hut_ri.csv");
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
    }
</script>
</body>
</html>
