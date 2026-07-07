<p align="center">
    <img src="doc/demo/logo.png" width="80px" />
    <h1 align="center">Cloud Mail</h1>
    <p align="center">Layanan email minimalis dan responsif berbasis Cloudflare Workers, mendukung pengiriman email serta pesan beserta lampiran 🎉</p> 
    <p align="center">
        Bahasa Indonesia | <a href="/README-en.md" style="margin-left: 5px">English</a>
    </p>
    <p align="center">
        <a href="https://github.com/maillab/cloud-mail/tree/main?tab=MIT-1-ov-file" target="_blank" >
            <img src="https://img.shields.io/badge/license-MIT-green" />
        </a>    
        <a href="https://github.com/maillab/cloud-mail/releases" target="_blank" >
            <img src="https://img.shields.io/github/v/release/maillab/cloud-mail" alt="releases" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/issues" >
            <img src="https://img.shields.io/github/issues/maillab/cloud-mail" alt="issues" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/stargazers" target="_blank">
            <img src="https://img.shields.io/github/stars/maillab/cloud-mail" alt="stargazers" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/forks" target="_blank" >
            <img src="https://img.shields.io/github/forks/maillab/cloud-mail" alt="forks" />
        </a>
    </p>
    <p align="center">
        <a href="https://trendshift.io/repositories/20459" target="_blank" >
            <img src="https://trendshift.io/api/badge/repositories/20459" alt="trendshift" >
        </a>
    </p>
</p>


## Deskripsi Proyek

Hanya dengan satu nama domain, Anda dapat membuat berbagai alamat email yang berbeda, layaknya platform penyedia email besar. Proyek ini mendukung deployment ke **Cloudflare Workers**, sehingga dapat menekan biaya server dan memungkinkan Anda membangun layanan email mandiri dengan mudah.

## Tampilan Proyek

- [Demo Online](https://skymail.ink)<br>
- [Panduan Deployment](https://doc.skymail.ink)<br>


| ![](/doc/demo/demo1.png) | ![](/doc/demo/demo2.png) |
|-----------------------|-----------------------|
| ![](/doc/demo/demo3.png) | ![](/doc/demo/demo4.png) |




## Fitur Utama

- **💰 Biaya Rendah**: Dapat dideploy langsung ke Cloudflare Workers sehingga menghemat atau bahkan membebaskan biaya penyewaan server.

- **💻 Desain Responsif**: Tata letak yang responsif secara otomatis beradaptasi dengan layar komputer (PC) maupun sebagian besar browser di ponsel.

- **📧 Pengiriman Email**: Terintegrasi dengan Resend untuk mengirim email, mendukung pengiriman masal (broadcast), menyisipkan gambar dan lampiran, serta memantau status pengiriman.

- **🛡️ Fitur Administrator**: Memungkinkan manajemen pengguna dan email, dilengkapi kontrol akses berbasis peran (RBAC) untuk membatasi fitur serta penggunaan sumber daya.

- **📦 Kirim & Terima Lampiran**: Mendukung penerimaan dan pengiriman lampiran email dengan memanfaatkan penyimpanan objek Cloudflare R2 untuk menyimpan dan mengunduh file.

- **🔔 Notifikasi & Penerusan Pesan**: Email yang masuk dapat diteruskan (forward) secara otomatis ke bot Telegram atau penyedia layanan email lainnya.

- **📡 API Terbuka**: Menyediakan REST API untuk menghasilkan pengguna secara masal dan melakukan pencarian email dengan berbagai parameter.

- **🔢 Pengenalan Kode Verifikasi**: Menggunakan Cloudflare Workers AI untuk mengenali dan mengekstrak kode verifikasi (OTP) secara otomatis dari email yang masuk.

- **📈 Visualisasi Data**: Menggunakan ECharts untuk menampilkan rincian statistik sistem dan grafik pertumbuhan email pengguna secara visual dan interaktif.

- **🎨 Pengaturan Kustomisasi**: Memungkinkan penyesuaian judul situs web, gambar latar belakang halaman login, dan tingkat transparansi antarmuka.

- **🤖 Verifikasi Keamanan**: Terintegrasi dengan Cloudflare Turnstile untuk mencegah pendaftaran akun masal oleh bot/spam.

- **📜 Fitur Lainnya**: Fitur-fitur menarik lainnya sedang dalam tahap pengembangan...



## Tumpukan Teknologi (Tech Stack)

- **Platform**: [Cloudflare Workers](https://developers.cloudflare.com/workers/)

- **Framework Web**: [Hono](https://hono.dev/)

- **ORM**: [Drizzle](https://orm.drizzle.team/)

- **Framework Frontend**: [Vue 3](https://vuejs.org/) 

- **Framework UI**: [Element Plus](https://element-plus.org/) 

- **Layanan Pengiriman Email**: [Resend](https://resend.com/)

- **Penyimpanan Cache**: [Cloudflare KV](https://developers.cloudflare.com/kv/)

- **Database**: [Cloudflare D1](https://developers.cloudflare.com/d1/)

- **Penyimpanan File**: [Cloudflare R2](https://developers.cloudflare.com/r2/)

## Struktur Direktori

```
cloud-mail
├── mail-worker                 # Proyek backend (Cloudflare Worker)
│   ├── src                  
│   │   ├── api                 # Lapisan antarmuka API			
│   │   ├── const               # Konstanta proyek
│   │   ├── dao                 # Lapisan akses data (Data Access Object)
│   │   ├── email               # Pemrosesan dan penerimaan email
│   │   ├── entity              # Entitas database
│   │   ├── error               # Penanganan eksepsi kustom
│   │   ├── hono                # Konfigurasi framework web, interceptor, eksepsi global, dll.
│   │   ├── i18n                # Internasionalisasi bahasa
│   │   ├── init                # Inisialisasi cache database
│   │   ├── model               # Enkapsulasi data respons API
│   │   ├── security            # Otentikasi & otorisasi hak akses
│   │   ├── service             # Lapisan logika bisnis
│   │   ├── template            # Template pesan
│   │   ├── utils               # Kelas utilitas (Tools)
│   │   └── index.js            # File utama/entri
│   ├── package.json            # Dependensi proyek backend
│   └── wrangler.toml           # Konfigurasi Cloudflare Wrangler
│
├── mail-vue                    # Proyek frontend (Vue 3)
│   ├── src
│   │   ├── axios               # Konfigurasi Axios
│   │   ├── components          # Komponen kustom Vue
│   │   ├── echarts             # Konfigurasi dan import ECharts
│   │   ├── i18n                # Internasionalisasi bahasa
│   │   ├── init                # Inisialisasi aplikasi saat dimuat
│   │   ├── layout              # Komponen tata letak utama (Layout)
│   │   ├── perm                # Autentikasi izin pengguna
│   │   ├── request             # Pengelolaan panggilan API
│   │   ├── router              # Konfigurasi rute (Vue Router)
│   │   ├── store               # Manajemen status global (Pinia)
│   │   ├── utils               # Kelas utilitas (Tools)
│   │   ├── views               # Komponen halaman web
│   │   ├── App.vue             # Komponen utama aplikasi
│   │   ├── main.js             # Entri utama JS
│   │   └── style.css           # CSS global
│   ├── package.json            # Dependensi proyek frontend
└── └── env.release             # Konfigurasi lingkungan deployment
```

## Dukungan & Donasi

<a href="https://doc.skymail.ink/support.html" >
<img width="170px" src="./doc/images/support.png" alt="">
</a>

## Lisensi

Proyek ini mendistribusikan di bawah lisensi [MIT](LICENSE).	


## Komunitas & Diskusi

[Telegram](https://t.me/cloud_mail_tg)
