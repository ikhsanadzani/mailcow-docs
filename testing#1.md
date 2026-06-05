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
