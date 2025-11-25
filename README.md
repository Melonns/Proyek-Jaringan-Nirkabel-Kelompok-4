# Proyek Jaringan Nirkabel - Kelompok 4
**Topik:** Open5GS & UERANSIM 5G Core Simulation

## 📊 Registration Status
Berikut adalah hasil log registrasi dari simulasi gNB dan UE.

### gNB Registration
| Metric | Status / Value |
| :--- | :--- |
| **Status** | ✅ SUCCESS |
| **Time Taken** | 15 ms (Trying $\rightarrow$ NG Setup Successful) |
| **AMF Connection** | ESTABLISHED |

### UE Registration
| Metric | Status / Value |
| :--- | :--- |
| **Status** | ✅ SUCCESS |
| **Time Taken** | ~ 1.1 detik (PMLN-SEARCH $\rightarrow$ TUN interface up) |
| **IMSI** | `imsi-001011000000001` |
| **TUN Interface** | `uesimtun0` |
| **IP Address** | `10.45.0.2` |

---

## 📡 Connectivity Tests
Pengujian konektivitas dilakukan dari UE (User Equipment) ke berbagai target.

| Test Target | IP / Endpoint | Result | RTT Average / Note |
| :--- | :--- | :---: | :--- |
| **UPF Gateway** | `10.45.0.2` | **PASS** | 6.441 ms |
| **Internet** | `8.8.8.8` | **PASS** | 62.511 ms |
| **DNS Resolution** | - | **PASS** | - |
| **HTTP/HTTPS** | - | **PASS** | - |

---

## 🛠️ Issues & Troubleshooting
Rangkuman masalah yang ditemukan selama proses simulasi dan solusinya.

| Issue / Error Log | Root Cause | Resolution |
| :--- | :--- | :--- |
| **UE Error:** `PAYLOAD_NOT_FORWARDED`<br>**UPF Error:** `gtp_connect()` ke IP `10.34.4.130` | Konfigurasi `gtpIp` pada file config gNB tidak cocok dengan IP `linkIp` / `ngapIp` yang sebenarnya. | 1. Update `configs/open5gs-gnb-k3s.yaml`: ubah `gtpIp` ke host IP yang benar (`10.0.2.15`).<br>2. Restart `nr-gnb` dan `nr-ue` menggunakan `sudo` (privilege escalation). |

---

## 📷 Lampiran Bukti (Screenshots)
Bukti tangkapan layar dari terminal saat simulasi berjalan.

### 1. Start gNB Simulator
![Log Start gNB](images/gnb-start.png)
*Gambar 1.2: Proses inisialisasi gNB berhasil.*

### 2. Start UE Simulator
![Log Start UE](images/ue-start.png)
*Gambar 1.3: Proses registrasi UE dan pembuatan tunnel.*

### 3. Test Basic Connectivity
![Ping Test Result](images/connectivity-test.png)
*Gambar 1.4: Hasil ping ke Gateway dan Internet.*
