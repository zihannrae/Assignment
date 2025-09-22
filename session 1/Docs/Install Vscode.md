# Cara Mengunduh Visual Code di Linux Mint

Berikut adalah cara bagaimana mengunduh Visual Code di Linux Mint

1. Buka Firefox browser
2. Buka laman Visual Studio dan pilih opsi Docs
3. Klik Setup dan pilih Linux
4. IKuti tata cara yang sudah disediakan di bagian **Install VS Code on Linux** dan ikuti tata cara di opsi **Debian and Ubuntu based distributions**
5. KLik `.deb.package (64-bit)` untuk mengunduhnya 
6. Buka terminal 
7. Ketik `cd Downloads/` lalu enter
![tahap 1](/session%201/img/vscode%20thp1.jpeg)
8. Ketik `ls` lalu enter
9. Ketik `sudo apt install co` lalu enter
![tahap2](/session%201/img/vscthp2.jpeg)
10. Ketik `sudo apt install wget gpg apt-transport-https` lalu enter
11. Ketik `curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg` lalu enter
12. Ketik `sudo install -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/microsoft-archive-keyring.gpg` lalu enter
13. Ketik `sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'` lalu enter
14. Ketik `sudo apt update` lalu enter
15. Ketik `sudo apt install code` lalu enter
![tahap3](/session%201/img/vscthp3.jpeg)
16. Cek apakah Vscode sudah terinstall dengan cara mencari di search bar Linux Menu.
17. Visual Code sudah bisa digunakan
![selesai](/session%201/img/vscselesai.jpeg)
