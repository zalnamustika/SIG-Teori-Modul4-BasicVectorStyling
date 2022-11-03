# SIG-Teori-Modul4-BasicVectorStyling

## Data
Anda dapat langsung mengunduh salinan lapisan di atas dari bawah:

[globalpowerplantdatabasev120.zip](https://www.qgistutorials.com/downloads/globalpowerplantdatabasev120.zip)

[ne_10m_land.zip](https://www.qgistutorials.com/downloads/ne_10m_land.zip)

## Prosedur

1. Buka zip kedua kumpulan data ke folder di komputer Anda. Di Panel Browser QGIS, temukan direktori tempat Anda mengekstrak data. Perluas ne_10m_landfolder dan pilih ne_10m_land.shplayer. Seret layer ke kanvas.

2. Anda akan mendapatkan layer baru yang ne_10m_landditambahkan ke panel Layers . Basis data pembangkit listrik global hadir sebagai file CSV, jadi kita perlu mengimpornya. Klik tombol Buka Pengelola Sumber Data pada Bilah Alat Sumber Data . Anda juga dapat menggunakan pintasan keyboard.Ctrl + L

3. Di jendela Pengelola Sumber Data , alihkan ke tab Teks Dibatasi . Klik tombol ... di sebelah Nama file dan telusuri direktori tempat Anda mengekstrak globalpowerplantdatabasev120.zipfile. Pilih global_power_plant_database.csv. QGIS akan otomatis mendeteksi bidang pembatas dan geometri. Biarkan Geometri CRS ke nilai default . Klik Tambah diikuti oleh Tutup .EPSG:4326 - WGS84

4. Sebuah layer baru global_power_plant_databaseakan ditambahkan ke panel Layers dan Anda akan melihat titik-titik yang mewakili pembangkit listrik di kanvas. Sekarang kita siap untuk menata kedua lapisan ini. Klik tombol Open the Layer Styling panel di bagian atas panel Layers

5. Panel Layer Styling akan terbuka di sebelah kanan. Pilih ne_10m_landlapisannya terlebih dahulu. Ini akan menjadi lapisan dasar kami sehingga kami dapat menjaga gaya minimalis agar tidak mengganggu. Klik dan gulir ke bawah. Pilih warna Fill sesuai keinginan Anda. Klik drop-down di sebelah Stroke color dan pilih . Ini akan mengatur garis besar poligon tanah menjadi transparan. Anda akan melihat hasil seleksi Anda diterapkan segera ke lapisan.Simple fillTransparent Stroke

6. Selanjutnya pilih global_power_plant_databaselapisan. Klik dan gulir ke bawah. Pilih penanda segitiga.Simple marker

7. Gulir ke atas dan pilih warna Isi sesuai keinginan Anda. Teknik kartografi yang berguna adalah memilih versi warna isian yang sedikit lebih gelap sebagai warna Stroke . Daripada mencoba memilihnya secara manual, QGIS menyediakan ekspresi untuk mengontrol ini dengan lebih tepat. Klik tombol Penimpaan yang ditentukan data dan pilih Edit .

8. Masukkan ekspresi berikut untuk mengatur warnanya menjadi 30% lebih gelap dari warna isian dan klik OK.

-------------------------

darker(@symbol_color, 130)

-------------------------

Catatan :

-------------------------

Perhatikan bahwa ekspresi ini tidak tergantung pada warna isian yang Anda pilih. Anda akan melihat bahwa ini sangat berguna dalam langkah-langkah berikut di mana secara otomatis mengatur warna batas berdasarkan warna isian yang disediakan.

-------------------------

9. Anda akan melihat bahwa tombol Override yang ditentukan Data di sebelah Warna Stroke telah berubah menjadi kuning - menunjukkan bahwa properti ini dikendalikan oleh override. Render simbol tunggal dari lapisan pembangkit listrik tidak terlalu berguna. Itu tidak menyampaikan banyak informasi kecuali lokasi pembangkit listrik. Mari kita gunakan penyaji yang berbeda untuk membuatnya lebih berguna. Klik drop-down Symbology dan pilih Categorizedrenderer.

10. Lapisan tersebut global_power_plant_databaseberisi atribut yang menunjukkan bahan bakar utama yang digunakan di setiap pembangkit listrik. Kita dapat membuat gaya di mana setiap jenis bahan bakar yang unik ditampilkan dalam warna yang berbeda. Pilih primary_fuelsebagai Kolom . Klik Klasifikasi . Anda akan melihat beberapa kategori dan rendering peta berubah sesuai.

11. Meskipun tampilan Terkategori berguna, lapisan ini berisi terlalu banyak kategori untuk dapat ditafsirkan peta secara bermakna. Pendekatan yang lebih baik adalah mengelompokkan jenis kategori bahan bakar tertentu dan mengurangi jumlah kelas. Mari kita coba buat 3 kategori - Bahan bakar terbarukan , Bahan bakar tidak terbarukan , dan Lainnya . Pilih Rule-basedpenyaji. Pilih semua kecuali satu aturan dengan menahan Ctrltombol dan mengklik setiap baris. Setelah dipilih, klik tombol Hapus aturan yang dipilih untuk menghapusnya.

12. Pilih aturan yang tersisa dan klik Edit aturan saat ini .

13. Masukkan sebagai Label . Klik tombol Ekspresi di sebelah Filter .Renewable fuel

14. Dalam dialog Pembuat String Ekspresi , masukkan ekspresi berikut dan klik OK . Di sini kami mengelompokkan beberapa kategori energi terbarukan ke dalam satu kategori.

-------------------------

"primary_fuel" IN ('Biomass', 'Geothermal', 'Hydro', 'Solar', 'Wind', 'Storage', 'Wave and Tidal')

------------------------

Catatan :

---------------------------

Jenis bahan bakar yang dipilih untuk kategori terbarukan vs. tidak terbarukan didasarkan pada Wikipedia . Ada definisi dan klasifikasi alternatif yang mungkin tidak cocok dengan apa yang dipilih di sini.

---------------------------

15. Gulir ke bawah dan klik Penanda sederhana . Pilih warna Isi yang sesuai . Setelah selesai, klik tombol Kembali.

16. Gulir ke bawah dan klik Penanda sederhana. Pilih warna Isi yang sesuai. Setelah selesai, klik tombol Kembali.

17. Salinan aturan yang ada akan ditambahkan. Pilih baris yang baru ditambahkan dan klik Edit aturan saat ini.

18. Masukkan sebagai Label . Klik tombol Ekspresi di sebelah Filter .Non-renewable fuel

19. Dalam dialog Pembuat String Ekspresi , masukkan ekspresi berikut dan klik OK.

----------------------

"primary_fuel" IN ('Coal', 'Gas', 'Nuclear', 'Oil', 'Petcoke')

----------------------

20. Gulir ke bawah dan klik Penanda sederhana . Pilih warna Isi yang sesuai . Setelah selesai, klik tombol Kembali.

21. Ulangi proses Copy/Paste untuk menambahkan aturan ketiga. Pilih dan klik Edit aturan saat ini

22. Masukkan Othersebagai Label . Pilih Else - Catch all untuk fitur lain daripada Filter . Ini akan memastikan bahwa setiap kategori yang terlewatkan dalam 2 aturan sebelumnya, akan ditata oleh aturan ini. Gulir ke bawah dan klik Penanda sederhana . Pilih warna Isi yang sesuai . Setelah selesai, klik tombol Kembali.

23. Pengkategorian ulang selesai sekarang. Anda akan melihat tampilan yang jauh lebih bersih yang menunjukkan distribusi sumber bahan bakar terbarukan vs. tidak terbarukan yang digunakan oleh pembangkit listrik dan distribusinya di seluruh negara. Namun ini tidak memberikan gambaran yang lengkap. Kita bisa menambahkan variabel lain ke styling. Daripada menampilkan semua penanda dengan ukuran seragam, kami dapat menunjukkan ukuran yang proporsional dengan kapasitas pembangkit listrik masing-masing pembangkit. Teknik kartografi ini disebut pemetaan Multivariat . Klik kanan aturan dan pilih Ubah Ukuran .Renewable fuel

24. Klik tombol Penggantian yang ditentukan data di sebelah Ukuran.Pilih Sunting.

25. Karena kapasitas pembangkit listrik sangat bervariasi di antara kumpulan data kami, cara yang efektif untuk mendapatkan rentang ukuran yang kecil adalah dengan menggunakan log10fungsi. Anda dapat bereksperimen dengan ekspresi yang berbeda untuk sampai pada apa yang terbaik untuk visualisasi pilihan Anda. Masukkan ekspresi berikut dan klik OK.

----------------------

log10("capacity_mw") + 1

----------------------

26. Proses yang sama untuk aturan lainnya.

27. Setelah puas, Anda dapat menutup panel Layer Styling 

28. Melihat visualisasi akhir kami, Anda dapat langsung melihat pola di dataset. Sebagai contoh, di Eropa terdapat lebih banyak pembangkit listrik yang menggunakan sumber energi terbarukan, tetapi kapasitasnya lebih rendah daripada pembangkit yang menggunakan sumber energi tidak terbarukan.
