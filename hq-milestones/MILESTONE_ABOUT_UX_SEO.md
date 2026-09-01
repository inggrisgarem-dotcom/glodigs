# MILESTONE: Enterprise UI/UX & SEO Architecture (About Section)
**Date:** September 2026
**Architect / Lead:** Bari Vijaya (Glodigs Digital Growth Studio)
**Status:** PRODUCTION READY (Fixed & Deployed)

## 1. THE PROBLEM (Identifikasi Masalah)
* **Retensi Pasif:** Halaman "About" statis kurang memiliki daya tarik naratif (storytelling) untuk menahan interaksi pengunjung.
* **Race Condition:** Implementasi animasi scroll standar menyebabkan tumpang tindih (*overlap*) di mana Hero Section dan Bio mengetik secara bersamaan saat halaman dimuat, menghancurkan hierarki pembacaan.
* **SEO Blackout:** Pengosongan teks DOM (`innerHTML = ""`) untuk keperluan animasi mesin tik menyebabkan mesin pencari (Googlebot) mendeteksi halaman kosong (Blank Text), berisiko fatal pada hilangnya kata kunci (*keywords*) bisnis.
* **Layout Conflict:** Injeksi *absolute positioning* pada teks merusak tatanan CSS *pseudo-elements* bawaan (ikon wajik emas dan spasi aslinya).

## 2. THE STRATEGY (Metode Eksekusi)
* **Metode Isolasi Bedah Presisi:** Modifikasi DOM dilakukan secara terisolasi menggunakan skrip Vanilla JS tanpa *framework* eksternal (0 dependencies), memastikan tidak ada pergeseran tata letak (*Layout Shift*) pada section yang sudah paten.
* **Event-Driven Synchronization:** Mengubah logika dari berbasis waktu (timer) menjadi berbasis sinyal (event) untuk mengatur antrean animasi.
* **SEO-Safe DOM Cloning:** Memanfaatkan standar aksesibilitas WCAG (Screen-Reader Only) untuk memisahkan lapisan data mesin pencari dari lapisan visual manusia.

## 3. THE SOLUTION (Eksekusi & Solusi Presisi)
1. **Sequential Storyteller Engine:** Membangun *Intersection Observer API* kustom yang mengeksekusi paragraf baris per baris. Bio tidak akan mengetik sebelum teks Hero selesai merender secara utuh (Sistem Sinyal `heroSequenceComplete`).
2. **Re-triggerable Scroll State:** Animasi disetel untuk me-reset dirinya sendiri secara rapi ketika keluar dari jarak pandang (*viewport*), memberikan kesan halaman yang "hidup" setiap kali digulir naik-turun.
3. **Staggered Pop-ups:** Menyelaraskan kotak layanan, tag lokasi, dan *Milestones* dengan CSS *cubic-bezier* (1.2s delay bertingkat) agar melayang elegan dan berwibawa, tidak terburu-buru.
4. **1px Clipping (SEO Savior):** Menyembunyikan teks asli secara visual melalui manipulasi koordinat murni (`width: 1px`, `clip: rect(0,0,0,0)`) sehingga 100% kata kunci terbaca instan oleh Googlebot di milidetik pertama, sementara animasi visual dieksekusi di *layer* kloning tanpa menabrak ikon CSS *pseudo-element* bawaan.

**Kesimpulan:** 
Halaman "About" kini beroperasi ganda secara sempurna: Menghadirkan UX teatrikal yang memukau bagi pengunjung manusia, sekaligus menyajikan dokumen statis berkinerja tinggi yang 100% ramah indeksasi bagi mesin pencari.
