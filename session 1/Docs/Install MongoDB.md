# Cara Mengunduh MongoDB di Linux Mint

Berikut adalah cara bagaimana mengunduh MOngoDB di LInux Mint:

1. Buka terminal
2. Install software yang dibutuhkan yaitu gnupg dan curl
`sudo apt-get install gnupg curl`
3. Impor public GPG Key MongoDB
`curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc | sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg --dearmor`
4. Tambahkan repository MongoDB 
`echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list`
5. Update dan Install MongoDB
`sudo apt update -y`
`sudo apt install mongodb-org -y`
6. Mulai dan aktifkan MongoDB
`sudo systemctl enable --now mongod`
7. Verifikasi instalasi
`sudo systemctl status mongod`
8. Sambungkan ke MongoDB shell
`mongosh`
9. MongoDB selesai terunduh 

![Tampilan selesai](/session%201/img/Mongoselesai.jpeg)
