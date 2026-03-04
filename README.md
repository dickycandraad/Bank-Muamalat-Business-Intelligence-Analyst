# Rakamin - Bank Muamalat: Business Intelligence Analyst
## About Company
PT Bank Muamalat Indonesia Tbk adalah bank yang menjalankan usahanya berdasarkan prinsip syariah pertama di Indonesia. Saat ini, Bank Muamalat terus berinovasi dengan mengeluarkan produk-produk syariah seperti asuransi syariah, dana pensiun syariah dan multifinance syariah.
## Case Study Background
### The Business Challenge
PT Sejahtera Bersama memiliki aktivitas penjualan yang cukup aktif, namun informasi yang tersedia belum sepenuhnya dimanfaatkan untuk menghasilkan insight yang komprehensif. Manajemen membutuhkan gambaran yang lebih terstruktur mengenai performa penjualan, tren pertumbuhan, serta kontribusi produk dan wilayah, agar dapat mengambil keputusan yang lebih tepat dan berbasis data.
### My Role as Business Intelligence Analyst
Sebagai Business Intelligence Analyst, peran saya adalah mengubah data menjadi informasi yang bernilai. Melalui proses pengolahan dan analisis data, saya berfokus untuk menyajikan insight yang relevan, terukur, dan mudah dipahami oleh manajemen
### Project Objectives
Proyek ini bertujuan untuk membangun sistem pelaporan yang terintegrasi dan informatif, sehingga perusahaan dapat:
1. Memantau performa penjualan secara menyeluruh
2. Mengidentifikasi pola dan tren penjualan
3. Menemukan peluang untuk mempertahankan maupun meningkatkan penjualan
Dengan pendekatan berbasis data, perusahaan diharapkan dapat mengambil keputusan yang lebih strategis dan terarah.
### Dataset Overview
Disediakan dataset sebagai berikut:
1. Customers.csv
2. Orders.csv
3. Products.csv
4. ProductCategory.csv
## Case Study
1. Tentukan masing-masing primary key pada 4 dataset penjualan
2. Tentukan relationship dari ke-4 tabel tersebut
3. Sebagai Business Intelligence Analyst PT Sejahtera Bersama, kita akan membuat sebuah master table yang berisikan informasi:
   1) CustomerEmail (cust_email)
   2) CustomerCity (cust_city)
   3) OrderDate(order_date)
   4) OrderQty (order_qty)
   5) ProductName (product_name)
   6) ProductCategoryName (category_name)
   7) TotalSales (total_sales)
  Urutkan data tersebut berdasarkan tanggal transaksi yang paling awal sampai yang paling akhir.
5. Dari hasil tabel yang dibuat pada soal nomor 3, simpanlah hasilnya dalam bentuk CSV. Dengan menggunakan Looker Studio, buatlah visualisasi yang menampilkan data penjualan tersebut. Visualisasi tersebut harus berisi minimal:
   1) Total keseluruhan sales
   2) Total keseluruhan sales berdasarkan kategori produk
   3) Total keseluruhan qty berdasarkan kategori produk
   4) Total sales berdasarkan kota
   5) Total qty berdasarkan kota
   6) Top 5 kategori produk yang paling tinggi salesnya
   7) Top 5 kategori produk yang paling tinggi qtynya
6. Sebagai BI analyst PT Sejahtera Bersama, apa yang bisa anda usulkan untuk mempertahankan penjualan ataupun menaikkan penjualan dengan tabel transaksi detail yang sudah ada?

## Langkah-Langkah Pengerjaan Final Task
### 1. Menentukan primary key
Primary key adalah kolom unik yang digunakan untuk mengidentifikasi setiap baris data serta menjadi dasar dalam membangun relasi antar tabel. Penentuan primary key ini menjadi dasar dalam membangun relationship antar tabel pada tahap berikutnya.

Primary key bersifat unik (tidak boleh duplikat), tidak boleh bernilai NULL, mewakili satu baris data secara spesifik, dan digunakan sebagai acuan dalam proses relasi (join).

Berdasarkan karakteristik tersebut, maka primary key dari masing-masing tabel adalah:
1) Customers: CustomerID
2) Orders: OrderID
3) Products: ProdNumber
4) ProductCategory: CategoryID

### 2. Menentukan table relationship
Table relationship adalah hubungan antar tabel yang dibentuk melalui primary key dan foreign key untuk memungkinkan proses penggabungan data (join). Berdasarkan primary key yang telah ditentukan sebelumnya, maka relasi antar tabel adalah sebagaiberikut:
1) Customers.CustomerID = Orders.CustomerID, artinya satu customer dapat memiliki banyak orders.
2) Products.ProdNumber = Orders.ProdNumber, artinya satu produk dapat muncul di banyak transaksi.
3) ProductCategory.CategoryID = Products.Category, artinya satu kategori memiliki banyak produk.

Struktur relationship yang terbentuk adalah One-to Many (1:N), yang memungkinkan proses integrasi data antar tabel untuk analisis

### 3. Membuat master table
Tahap pertama adalah mengimpor dataset berikut ke BigQuery:
1) Customers.csv
2) Orders.csv
3) ProductCategory.csv
4) Products.csv
<img width="570" height="338" alt="image" src="https://github.com/user-attachments/assets/72f02453-1cc5-41c3-b763-964a9f0a2ed1" />

Query berikut digunakan untuk membuat MasterTable dengan menggabungkan tabel Orders, Customers, Products, dan ProductCategory.

<img width="635" height="490" alt="image" src="https://github.com/user-attachments/assets/0babdc5a-03ab-438b-9556-849bc653d377" />
<img width="683" height="203" alt="image" src="https://github.com/user-attachments/assets/82feb5b3-d6f7-4baa-bb62-6594a6cc323b" />

MasterTable telah berhasil dibuat dengan struktur kolom yang sesuai, tipe data yang tepat, serta perhitungan total_sales yang tervalidasi dengan benar.

Seluruh data transaksi telah terintegrasi melalui proses join antar tabel sehingga membentuk satu dataset yang terstruktur dan siap digunakan sebagai sumber utama dalam proses visualisasi dashboard dan analisis penjualan.

### 4. Visualisasi dashboard
<img width="2500" height="1876" alt="Bank Muamalat Business Intelligence Analyst" src="https://github.com/user-attachments/assets/3ea0b163-bb75-4e31-b269-4fc8ff814c04" />

Fitur utama dashboard meliputi:
1) KPI summary cards, yang menampilkan total sales, total orders, total quantity, dan total customers.
2) Filter interaktif, yang terdiri dari date, city, product name dan product category.
3) Bar chart, yang memvisualisasikan total sales dan total quantity by product category.
4) Line chart, yang menampilkan tren antar waktu total sales dan total quantity.
5) Geo map by city, yang memvisualisasikan total sales dan total quantity by city.
6) Donut chart, yang memvisualisasikan top 5 product category by sales dan quantity.

### 5. Insight Bisnis
1) Fokus pada Kategori Penyumbang Total Sales Terbesar
   - Robots menyumbang 42% ($743k) dan Drones menyumbang 27% ($477k) dari total sales.
   - Kategori ini memiliki dampak paling besar terhadap total sales.
   - Peningkatan performa pada dua kategori ini akan memberikan pengaruh signifikan terhadap total penjualan.
2) Maksimalkan Product dengan Total Quantity Order Tinggi
   - eBooks menyumbang 26,8% (3.123 unit) dan Training Videos 17,9% (2.081 unit)
   - mendominasi total quantity order.
   - Produk digital memiliki permintaan tinggi meskipun nilai per unit lebih rendah.
   - Kombinasi produk digital dengan produk fisik dapat membantu meningkatkan nilai transaksi secara keseluruhan.
3) Manfaatkan Pola Tren Penjualan
   - Puncak penjualan terjadi pada Juni 2021 dengan 582 unit terjual ($95k)
   - Penurunan terlihat pada Oktober 2021 dengan 368 unit terjual ($52k)
   - Pergerakan total sales sejalan dengan perubahan total quantity
   - Strategy yang mendorong peningkatan jumlah unit terjual akan berdampak langsung pada kenaikan total sales
4) Perkuat Wilayah dengan Performa Tinggi
   - Washington menjadi kota dengan kontribusi penjualan tertinggi selama periode analisis.
   - Tercatat 308 unit terjual dengan total sales sekitar $55k.
   - Hal ini menunjukkan adanya konsentrasi permintaan pada wilayah tertentu yang dapat menjadi fokus penguatan pasar.
5) Ringkasan Strategis
   - Total sales terkonsentrasi pada produk premium.
   - Volume penjualan didominasi produk digital.
   - Perubahan total sales dipengaruhi oleh perubahan jumlah unit terjual.
   - Terdapat konsentrasi penjualan pada wilayah tertentu.
   - Pendekatan berbasis data ini dapat membantu menjaga stabilitas penjualan sekaligus mendorong pertumbuhan secara terarah.
