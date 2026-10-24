# Live2D Rigging Pack — raw item

![Made by Kevsoft](https://img.shields.io/badge/Made%20by-Kevsoft-blue?style=for-the-badge)
![Live2D Ready](https://img.shields.io/badge/Live2D-Cubism%20Ready-brightgreen?style=for-the-badge)
![Format PSD](https://img.shields.io/badge/Format-PSD%20%7C%20PNG-orange?style=for-the-badge)
![Contact Telegram](https://img.shields.io/badge/Contact-t.me%2Fkevsoft__dev-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)

<p align="center">
  <img src="./preview.png" alt="Character Preview" width="400"/>
</p>

Ini adalah bahan mentah PSD + PNG yang sudah dikelompokkan dan siap digunakan untuk proses *rigging* Live2D. Ukuran canvas standar **768 × 768 px**, terdiri dari total **23 layer** yang telah dibagi rapi ke dalam **12 folder (Part)**.

---

## 🎨 Jasa Rigging & Desain Karakter (Kevsoft Services)

> **Butuh model custom atau mau terima beres tanpa pusing ngerigging?**  
> Kami di **Kevsoft** juga menyediakan layanan profesional untuk:
> - 🖌️ **Desain & Ilustrasi Karakter VTuber / Live2D** (Siap potong layer / *rig-ready*)
> - ⚙️ **Jasa Rigging Live2D** (Physics halus, ekspresi custom, hingga full body rigging)
> 
> 📩 **Hubungi kami via Telegram:** [t.me/kevsoft_dev](https://t.me/kevsoft_dev) untuk konsultasi, pemesanan, atau info *commission* lebih lanjut!

---

## 📦 Isi Paket

| File / Folder | Fungsi |
|---|---|
| `model_live2d.psd` | File PSD utama yang siap di-*import* langsung ke Live2D Cubism. Semua nama layer/folder sudah rapi, blend mode Normal 100%, terdiri dari 12 Part & 23 layer. |
| `layers/NN_Part_xxx/NN_Nama.png` | Kumpulan PNG per layer dengan ukuran *full canvas* (posisi sudah pas, tinggal ditumpuk). Nomor di depan nama file menandakan urutan layer (`01` = paling depan). |
| `layers.json` | Catatan data layer (nama baru, nama asli, folder, urutan, posisi bbox, dan ukuran). |
| `preview.png` | Gambar komposit/gabungan semua layer dengan background transparan. |

---

## 🛠️ Cara Pakai di Cubism Editor

1. Buka Cubism Editor, pilih **`File → Open`** lalu masukkan **`model_live2d.psd`**. Layer akan otomatis menjadi *ArtMesh* dan folder menjadi *Part*.
2. **Atur Clipping Mask** pada mata agar iris tidak keluar dari area mata putih:
   * `Iris_L` → clip ke `EyeWhite_L`
   * `Iris_R` → clip ke `EyeWhite_R`
3. Generate *Auto Mesh*, lalu mulai proses *rigging* per Part. Berikut panduan parameter standar yang bisa digunakan:

| Part / Bagian | Parameter Umum |
|---|---|
| `Part_HairFront`, `Part_Face`, `Part_EarsAccessory`, `Part_Brows` | `ParamAngleX`, `ParamAngleY`, `ParamAngleZ` (mengikuti gerakan kepala) |
| `Part_Brows` | `ParamBrowLY`, `ParamBrowRY` |
| `Part_EyeL`, `Part_EyeR` | `ParamEyeLOpen`, `ParamEyeROpen` (bulu mata & mata putih), `ParamEyeBallX`, `ParamEyeBallY` (iris) |
| `Part_Mouth` | `ParamMouthOpenY`, `ParamMouthForm` |
| `Part_Body`, `Part_Arms`, `Part_Legs` | `ParamBodyAngleX`, `ParamBodyAngleY`, `ParamBodyAngleZ`, `ParamBreath` |
| `Part_HairFront`, `Part_HairBack` | Setup Physics (`ParamHairFront`, `ParamHairSide`, `ParamHairBack`) |

---

## 📑 Urutan Layer (Depan → Belakang)

`Hair_Front` → `Eyebrow_L/R` → `Eyelash` / `Iris` / `EyeWhite` (Kiri, lalu Kanan) → `Mouth` → `Nose` → `Face` → `Headwear`, `Ear_L/R` → `Topwear`, `Bottomwear`, `Neck` → `Shoes`, `Legs` → `Arm_L/R` → `Hair_Back`

> **Note Konvensi Sisi:**  
> Penamaan `_L` merujuk pada **sisi kiri karakter** (terlihat di sebelah **kanan** layar). Sebaliknya, `_R` merujuk pada **sisi kanan karakter** (terlihat di sebelah **kiri** layar). Jika *tracking* mata terbalik saat diuji, cukup tukar parameter `ParamEyeLOpen` ↔ `ParamEyeROpen`.

---

## 🔄 Perubahan dari PSD Asli

* **Penghapusan Layer Mask:** Mask bawaan di file asli dihapus karena menyebabkan efek alpha ganda yang membuat garis tepi tampak pudar.
* **Perbaikan Urutan Layer:** Bulu mata dipindah ke atas iris & mata putih, serta alis dipindah ke atas wajah (tetap di bawah poni) agar sesuai dengan kebutuhan *rigging*.
* **Standardisasi Penamaan:** Nama layer diubah ke format ASCII yang rapi dan unik untuk mencegah *error* saat *import*:
  * `front hair` → `Hair_Front`
  * `irides-l` → `Iris_L`
  * `handwear-l` → `Arm_L`
  * `footwear` → `Shoes`
* **Integritas Piksel:** Piksel tiap layer dijamin 100% sama dengan asset asli tanpa ada pemotongan/perubahan gambar.

---

## ⚠️ Catatan Penting Sebelum Rigging

* **Resolusi Rendah:** Ukuran komponen cukup kecil (Wajah: 68×61 px, Mulut: 8×5 px, Hidung: 8×7 px, Iris: 12×9 px). Masih bisa di-*rig*, namun berisiko buram saat di-zoom. Disarankan melakukan *upscale* 4× (menggunakan Real-ESRGAN / waifu2x) dan menyesuaikan ukuran canvas PSD sebelum *rigging*.
* **Variasi Ekspresi:** Belum tersedia layer cadangan untuk ekspresi mulut terbuka lebar, mata merem, atau variasi bentuk lainnya. Gerakan buka-tutup perlu dibuat melalui *deform/warp* atau menggambar layer tambahan secara manual.
* **Elemen Tertutup Poni:** Alis dan `Headwear` tertutup oleh poni pada ilustrasi asli. Layer tetap ada dan bisa di-*rig*, namun baru terlihat jika poni digerakkan atau dibuat transparan.
* **Verifikasi File:** Struktur PSD telah diverifikasi secara matematis & programatik. Jika menemukan kendala saat dimuat ke Cubism Editor, silakan hubungi tim teknis kami via Telegram.

---

<p align="center">
  <b>Developed & Processed by Kevsoft</b><br>
  <i>Providing Professional Character Design & Live2D Rigging Services</i><br>
  📩 Contact: <a href="https://t.me/kevsoft_dev">t.me/kevsoft_dev</a>
</p>
