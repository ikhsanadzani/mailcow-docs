# mailcow-docs

# Apa itu mailcow?
adalah software open-source berbasis docker yang digunakan untuk membangun server email yang lengkap dan mandiri

## Ekosistem container untuk mailcow
- **Postfix** untuk menangani lalu lintas pengiriman email.
    
- **Dovecot** sebagai server tempat email Anda disimpan dan diambil.
    
- **Rspamd** untuk menyaring _spam_ secara otomatis.
    
- **SOGo** untuk menyediakan layanan _webmail_, kalender, dan kontak.

Kemudahan yang diberikan mailcow adalah mailcow ui, yaitu antarmuka berbasis web server

## Apa saja yang di butuhkan?

- podman 
> pengganti langsung untuk docker
- podman compose
> 
- podman-docker

## container apa saja yang dibutuhkan
### If there is a firewall, unblock the following ports for incoming connections:

| Service             | Protocol | Port   | Container       | Variable                         |
| ------------------- | -------- | ------ | --------------- | -------------------------------- |
| Postfix SMTP        | TCP      | 25     | postfix-mailcow | `${SMTP_PORT}`                   |
| Postfix SMTPS       | TCP      | 465    | postfix-mailcow | `${SMTPS_PORT}`                  |
| Postfix Submission  | TCP      | 587    | postfix-mailcow | `${SUBMISSION_PORT}`             |
| Dovecot IMAP        | TCP      | 143    | dovecot-mailcow | `${IMAP_PORT}`                   |
| Dovecot IMAPS       | TCP      | 993    | dovecot-mailcow | `${IMAPS_PORT}`                  |
| Dovecot POP3        | TCP      | 110    | dovecot-mailcow | `${POP_PORT}`                    |
| Dovecot POP3S       | TCP      | 995    | dovecot-mailcow | `${POPS_PORT}`                   |
| Dovecot ManageSieve | TCP      | 4190   | dovecot-mailcow | `${SIEVE_PORT}`                  |
| HTTP(S)             | TCP      | 80/443 | nginx-mailcow   | `${HTTP_PORT}` / `${HTTPS_PORT}` |
