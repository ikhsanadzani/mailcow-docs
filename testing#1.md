## cek apakah waktu sudah sinkron
```
timedatectl status
```
### output:
```
Local time: Sat 2026-06-06 01:03:33 WIB
           Universal time: Fri 2026-06-05 18:03:33 UTC
                 RTC time: Fri 2026-06-05 18:03:33
                Time zone: Asia/Jakarta (WIB, +0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
```
> pastikan NTP service : on
- jika belum jalankan command berikut:

```
sudo timedatectl set-ntp true
```
## pindah ke direktori /opt 
```
cd /opt
```

## unduh repositori resmi
```
sudo git clone https://github.com/mailcow/mailcow-dockerized
```

## Masuk ke folder yang baru saja diunduh
```
cd mailcow-dockerized
```

## Jalankan otomasi skrip bawaan dari mailcow
```
sudo ./generate_config.sh
```
### output dari command diatas:
```
Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
Cannot find Docker with a Version higher or equals 24.0.0
mailcow needs a newer Docker version to work properly...
Please update your Docker installation... exiting
```
> peringatan dari Podman tersebut merusak proses pembacaan variabel oleh skrip

## solving
> disini saya mengkonfigurasi beberapa file agar bisa by pass error tersebut

### bisukan peringatan emulasi Podman
```
sudo touch /etc/containers/nodocker
```

### pangkas pengecekan versi di skrip
```
sudo nvim generate_config.sh
```
#### Lalu commanding bagian ini
```
if [ "$DOCKER_VERSION" -lt 240000 ]; then
    echo "Cannot find Docker with a Version higher or equals 24.0.0"
    echo "mailcow needs a newer Docker version to work properly..."
    echo "Please update your Docker installation... exiting"
    exit 1
fi
```
> semua di commanding

#### lalu generate ulang
```
sudo ./generate_config.sh
```
- output:
```
Detecting if your IP is listed on Spamhaus Bad ASN List...
Check completed! Your IP is clean
Press enter to confirm the detected value '[value]' where applicable or enter a custom value.
Mail server hostname (FQDN) - this is not your mail domain, but your mail servers hostname: 
```
> disini saya hanya menggunakan untuk testing, maka domain yang digunakan adalah dummy domain, berikut cara konfiguarasi nya:

```
sudo nvim /etc/hosts
```

> lalu tambahkan baris baru di file tersebut
- contoh:
```
127.0.0.1  mail.lokal.dev
```

#### Pilihan setelah di generate ulang

Setelah langkah ini, skrip biasanya hanya akan meminta dua hal lagi:

 - Timezone: Ketik Asia/Jakarta (lalu Enter).

 -   Branch: Pilih opsi 1 (master) untuk versi yang lebih stabil.


