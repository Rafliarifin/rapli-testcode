# LANGKAH-LANGKAH MENJALANKAN DOCKER SEDERHANA DI LINUX

# BUAT FOLDER DOCKER:
```bash
$ mkdir docker-test
```
# BERPINDAH KE FOLDER:
```bash
$ cd docker-test
```
# BUAT DOCKERFILE
```bash
$ touch Dockerfile
```
# MENGEDIT ISI DOCKERFILe
```bash
$ nano Dockerfile
```
# ISI DOCKERFILE
```bash
# Gunakan image dasar PHP dengan Apache
FROM php:8.2-apache

# Salin file PHP dari direktori lokal ke dalam container
COPY ./php /var/www/html

# Expose port 80 untuk akses HTTP
EXPOSE 80
```
# BUAT FOLDER TEMPAT HTML
```bash
$ mkdir php
```
# BUAT FILE INDEX DI DALAM FOLDER HTML:
```bash
$ touch php/index.php
```
# MENGEDIT ISI FILE INDEX YANG ADA DI DIDALAM FOLDER HTML:
```bash
$ nano php/index.php
```

# ISI FILE index.php:
```bash
<?php
echo "Hello World";
?>
```

#  BANGUN Docker Image:
```bash
$ docker build -t docker-app .
```

# MENJALANKAN KONTAINER:
```bash
$ docker run -d -p 8080:80 docker-app
```

# AKSES APLIKASI DI BROWSER
http://localhost:8080

# MENAMPILKAN STATUS DOCKER TELAH BERJALAN
![Gambar dari Google Drive](https://drive.google.com/uc?id=12NLMAnNNc2o4ju9ZbKoWTbcAppS3lx0q)


# MENAMPILKAN BUKTI DOCKER BERJALAN
![Gambar dari Google Drive](https://drive.google.com/uc?id=18SoGVEs0fM5MMhYNyZEfev36c0AZVkrh)


# MENGHENTIKAN KONTAINER YANG BERJALAN
```bash
$ docker stop "id-container"
```

# MELAKUKAN PEMBATASAN MEMORI
```bash
$ docker run -d  --memory=300m --cpus=1 --name docker-test -p 8080:80 docker-app
```
# BUKTI STATUS PEMBATASAN MEMORI
![Gambar dari Google Drive](https://drive.google.com/uc?id=15umxrrN7PMx2QR5ffjbma01yx0NoXZhI)

# MELAKUKAN FASE BEDAH CONTAINER
## 1. Command ps aux
Menampilkan semua proses yang sedang berjalan di dalam container. Ini berguna untuk menganalisis aplikasi atau proses yang sedang dijalankan dalam container.
```bash
$ docker exec -it <container_id> ps aux
```
### Bukti Percobaan ps aux
![Gambar dari Google Drive](https://drive.google.com/uc?id=1Od4LyCy3pSf0kxKsvZPDx2O9PBaU_WK7)

## 2. Command inspect
Command ini memberikan informasi rinci tentang container, termasuk konfigurasi jaringan, mounts, environment variables, dan lainnya.
```bash
$ docker inspect <container_id>
```
## Bukti percobaan inspect
![Gambar dari Google Drive](https://drive.google.com/uc?id=1bG1u3Gn-BMfRI82Iatzh06V_ndUP5GD2)

## 3. Command logs
Untuk melihat log yang dihasilkan oleh container. Ini berguna untuk debugging atau melihat output aplikasi yang berjalan di dalam container.
```bash
$ docker logs <container_id>
```
## Bukti percobaan logs
![Gambar dari Google Drive](https://drive.google.com/uc?id=1V1H19zapeWlpew8xY_Sst6rYtvkuVoSG)

## 4.Command masuk ke container
Untuk masuk dan melakukan modifikasi file didalam container
```bash
$ docker exec -it <container_id> /bin/bash
```
## Bukti percobaan masuk ke container
![Gambar dari Google Drive](https://drive.google.com/uc?id=1J-rrirh8qHUhIdPJquC78tvwaGBt5P2w)

## 5. Membatasi CPU
Untuk membatasi jumlah CPU yang dialokasikan ke kontainer saat menjalankan dengan pengaturan tertentu.
```bash
$ docker run -d --name my-container --cpus="2.0" my-image
```
## Bukti percobaan membatasi cpu ke container
![Gambar dari Google Drive](https://drive.google.com/uc?export=view&id=12sPlfAy1cw69Vtsd21bau2daukCbgv-8)
