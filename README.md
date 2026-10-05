BAI 4: LUU TRU DU LIEU DON GIAN VOI DOCKER VOLUME

1. MUC TIEU
- Tao va quan ly Named Volume trong Docker.
- Kiem chung tinh ben vung cua du lieu duoc luu tru tren Volume giua cac vong doi container khac nhau.
- Thao tac doc va ghi du lieu vao volume thong qua 2 container Alpine doc lap.

2. BOI CANH VA NGUYEN TAC HOAT DONG
- Volume la co che chuan va toi uu de luu tru du lieu ben vung (persistent storage) trong Docker.
- Khi container dung hoac bi xoa (--rm), du lieu trong volume van duoc giu nguyen tren host tai khu vuc quan ly cua Docker (/var/lib/docker/volumes/).
- Cac container khac co the mount cung volume de tiep tuc doc va su dung du lieu.

3. CAC BUOC THUC HIEN

3.1. Tao Named Volume moi
Lenh thuc hien:
```bash
docker volume create easy-volume
```
Ket qua dau ra:
```text
easy-volume
```

3.2. Kiem tra danh sach volume tren may
Lenh thuc hien:
```bash
docker volume ls
```
Ket qua dau ra:
```text
DRIVER    VOLUME NAME
local     easy-volume
```

3.3. Khoi chay Container 1 de ghi du lieu vao Volume
Lenh thuc hien:
```bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
```
Ket qua:
- Container khoi chay, mount volume easy-volume vao duong dan /data.
- Ghi chuoi "Luu tru du lieu Docker" vao /data/test.txt.
- Container tu dong dung va bi xoa do co co --rm.

3.4. Khoi chay Container 2 doc lai du lieu tu Volume de kiem tra
Lenh thuc hien:
```bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
```
Ket qua dau ra:
```text
Luu tru du lieu Docker
```

3.5. Don dep volume sau khi hoan thanh
Lenh thuc hien:
```bash
docker volume rm easy-volume
```
Ket qua dau ra:
```text
easy-volume
```

4. TONG KET CAC LENH
```bash
docker volume create easy-volume
docker volume ls
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
docker volume rm easy-volume
```
