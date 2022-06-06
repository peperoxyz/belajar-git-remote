# Belajar Git-Remote
Repository yang dibuat untuk latihan menggunakan git-remote sekaligus menyimpannya di GitHub

## Git Server
GitHub merupakan salah satu platform yang menyediakan Git Server.

## SSH
[Secure Shell] : Protokol jaringan untuk komunikasi jaringan yang aman dan terenkripsi. Untuk pengguna windows wajib menggunakan GitBash agar SSH dapat digunakan dengan baik.

### Git SSH
SSH adalah salah satu mekanisme untuk berkomunikasi dengan Git Server. Keuntungan menggunakan SSH untuk berkomunikasi(pengiriman/pengambilan data), kita tidak perlu memasukkan username dan password(seperti saat menggunakan HTTP).

### SSH Key
SSH Key adalah kunci yang digunakan untuk autentikasi ke SSH Server.

A. Membuat SSH Key : Ketikkan command ini di GitBash
``` ssh-keygen ```

Maka secara otomatis akan terdapat 2 key di lokal(2 file): yaitu private key dan public key:
1. File id_rsa -> private key
2. File id_rsa.pub -> public key

B. Setelah buat SSH Key, registrasikan SSH public key ke GitHub. Hal ini dilakukan agar kita tidak perlu melakukan autentikasi lagi saat berkomunikasi.
1. Masuk ke github.com/settings/keys
2. Add new key
3. Tambahkan nama key dan isi key berdasarkan isi file id_rsa.pub (public key)

C. Test SSH ke GitHub : Pastikan apakah kita sudah bisa terkoneksi ke GitHub menggunakan SSH.
```bash
ssh -T git@github.com
response: Hi peperoxyz! You've successfully authenticated, but GitHub does not provide shell access. //success terhubung
```

## Remote Repository
Saat kita membuat Git project di local, Git tidak tahu tentang Remote Repository. Kita perlu memberi tahu ke Git Prokect yang sudah kita buat tentang lokasi git repo kita.

A. Menambahkan remote repository
1. Buat Git Project
2. Ketik command ini(sesuaikan ssh dengan ssh repo):
```bash
git remote add namaRemote ssh-url
```
B. Melihat remote repository yang sudah berhasil gunakan command
``` git remote``` atau ``` git remote get-url namaRemote ``` untuk detailnya.

C. Menghapus remote repository
``` git remote rm namaRemote ```

## Git Push
Git project yang sudah kita simpan di lokal Git, tidak secara otomatis akan tersimpan di Git Server. Oleh karena itu, jika kita ingin mengirim perubahan yang terjadi di Git project pada lokal kita, perlu dilakukan Git Push.

### Push Branch
1. Perubahan branch ke remote dengan nama branch yang sama dengan yang di lokal
``` git push namaRemote namaLocalBranch ```
2. Perubahan branch ke remote dengan nama branch yang berbeda dengan yang di lokal
``` git push namaRemote namaLocalBranch:namaRemoteBranchBaru ```
3. Push semua branch: tanpa bisa mengganti nama
``` git push namaRemote --all ```
4. Menghapus branch yang ada di remote repository (bukan berarti terhapus juga di lokal)
``` git push --delete namaRemote namaBranch ```

Git push bisa dilakukan setiap kali kita selesai melakukan commit di git project lokal, atau sekaligus di akhir setelah seluruh(lebih dari 1 commit) dilakukan di git project lokal.

## Git Clone
Clone digunakan ketika kita ingin mendownload project Git yang ada di server Github, ke lokal/komputer baru, dan secara otomatis akan didownload sebagai Git project (tanpa harus Git init).

1. Masuk ke folder yang ingin diletakkan file clonningan dari Git Server
2. Copy SSH dari repo yang ingin di-clone
3. Ketik command berikut:
``` git clone ssh namaFolderHasilClone ```

Note: Git Clone hanya akan meng-clonning branch utama saja.
