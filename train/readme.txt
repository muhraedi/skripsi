=> Mengumpulkan dan lakukan labelling dataset
    1.	Menentukan daftar kelas yang akan digunakan untuk training dengan mengubah predefined_classes.txt pada folder data. kelas yang digunakan ada dua yaitu Matang dan Non Matang.
    2.	Menjalankan labelimg.exe dan klik tombol "PascalVOC" yang berada Tepat di bawah tombol "Save" di toolbar untuk beralih ke format YOLO. 
    3.	Membuka folder yang berisi citra hasil ekstraksi untuk memproses banyak citra dan mengganti folder penyimpanan ke folder yang berisi citra itu sendiri.
    4.	Melakukan pelabelan manual pada objek. Pada proses ini tiap objek buah kakao pada gambar akan diberi kotak pembatas (bounding box), kemudian memilih nama kelas yaitu “Matang” atau “Non Matang” dari objek tersebut.
    5.	Setiap gambar yang telah diberi label, secara otomatis menghasilkan sebuah file anotasi dalam format text yang berisi koordinat dan id class dengan format <Class><X><Y><Width> <Height>.

=> Training
- Hubungkan google drive
- Cloning & Building Darknet
- Pindahkan Dataset ke Cloud VM
- Buat file .names dan .data
- Konfigurasi file .cfg
- Buat file .names dan .data
- Generating train.txt dan test.txt
- Download pre-trained weights
- Mulai Training