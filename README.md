# Minima-Docker
Update Minima

## Minimal Spesifikasi VPS

4Core vCPU

6/8GB RAM

160GB/200GB SSD/NVME Storage

### Hapus Minima Versi Sebelumnya

```
sudo wget -O minima_remove.sh https://raw.githubusercontent.com/minima-global/Minima/master/scripts/minima_remove.sh && chmod +x minima_remove.sh && sudo ./minima_remove.sh -p 9001 -x && sudo rm -r /home/minima/ && sudo userdel minima
```

### Buat User Minima

```
sudo adduser minima
```

Masukkan Password 

![image](https://user-images.githubusercontent.com/91402307/202046123-8c82f36b-bbf7-4aa0-9274-e63d89c34314.png)

Tidak usah di isi Tekan Enter saja semuanya kemudian Tekan Y

![image](https://user-images.githubusercontent.com/91402307/202046334-773b771a-8825-474c-8229-ecb3afeac838.png)

### Berikan Izin 

```
sudo usermod -aG sudo minima
```

![image](https://user-images.githubusercontent.com/91402307/202046487-34e5bfa9-3aa1-4e81-847f-bb71127002be.png)

### Pindah ke User Minima

```
su - minima
```
Lihat sebelumnya berada di  User Root kemudian pindah ke User Minima 

![image](https://user-images.githubusercontent.com/91402307/202046754-ca15d74d-51f5-42b0-93da-d17922a7875a.png)

### Download Docker

```
sudo curl -fsSL https://get.docker.com/ -o get-docker.sh
```

Masukkan Password saat membuat User Minima

![image](https://user-images.githubusercontent.com/91402307/202047148-7232801c-d56d-4625-92b1-15833fd09a58.png)

### Berikan Izin untuk menjalankan Install Docker tunggu beberapa menit

```
sudo chmod +x ./get-docker.sh && ./get-docker.sh
```



