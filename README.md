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
sudo apt-get update && sudo adduser minima
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

![image](https://user-images.githubusercontent.com/91402307/202047455-bc60138d-544c-4cc9-ade7-88dd7bf2d5e5.png)

### Exit dari User Minima

```
exit
```

![image](https://user-images.githubusercontent.com/91402307/202049650-2ab59185-534f-427d-9073-18a6a5d0b250.png)


### Tambahkan User Minima ke Grup Docker

```
sudo usermod -aG docker $USER && su minima
```

![image](https://user-images.githubusercontent.com/91402307/202049748-169b3300-334e-48e7-b6a5-5b0c7c1b417a.png)

### Jalankan Node Minima
Bagian PASSWORDMINIMA diganti bertujuan untuk akses Web Minima Dapps (jangan sampai lupa)

```
docker run -d -e minima_mdspassword=PASSWORDMINIMA -e minima_server=true -v ~/minimadocker9001:/home/minima/data -p 9001-9004:9001-9004 --restart unless-stopped --name minima9001 minimaglobal/minima:latest
```

![image](https://user-images.githubusercontent.com/91402307/202049085-6b1a2376-efa9-4526-9c99-713743ecfcb4.png)

### Pastikan Docker dimulai secara otomatis saat server dimulai

```
sudo systemctl enable docker.service && sudo systemctl enable containerd.service
```

![image](https://user-images.githubusercontent.com/91402307/202049916-456e7b46-ddd2-479a-a6b1-e712b0493a06.png)

### Otomatis Update 

Setiap 24 jam, Menara Pengawal akan memeriksa apakah ada Minima versi baru dan akan memperbarui jika ada.
```
docker run -d --restart unless-stopped --name watchtower -e WATCHTOWER_CLEANUP=true -e WATCHTOWER_TIMEOUT=60s -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower
```

![image](https://user-images.githubusercontent.com/91402307/202050392-5a615733-48c8-4530-b872-4a40efcb9eb1.png)

### Untuk memeriksa Status Docker

```
docker ps
```

![image](https://user-images.githubusercontent.com/91402307/202050578-afd745b7-3962-45d0-a172-e82b773fff4b.png)

### Memasukkan Incentive ID Minima

```
docker exec -it minima9001 /bin/sh
```

```
sh /bin/minima
```

Masukkan Incentive ID di INCENTIVEID

```
incentivecash uid:INCENTIVEID
```

![image](https://user-images.githubusercontent.com/91402307/202051417-d3bd8752-d84f-4770-803a-617fc7e39ae0.png)

