# สรุปความเข้าใจเกี่ยวกับ Docker command

* สำหรับการ check **version Docker** 
 ```
    docker version
 ```

* สำหรับการ ดูข้อมูล **containers** ที่กำลังทำงานอยู่
``` 
    docker ps
```
  ถ้าอยากดู **container** ที่มีทั้งหมด ให้เพิ่ม -a ลงไป
```
    docker ps -a
```
  จะแสดงข้อมูล container ทั้งหมดที่เรามี ทั้งที่กำลังใช้งานอยู่และไม่ได้ใช้

* สำหรับการดู images ที่มีอยู่ในเครื่อง
```
    docker images
```


## Docker กับ Portainer

* ใช้สำหรับการสร้างพื้นที่ไว้เก็บข้อมูลของ **Portainer** (แบบถาวร) เพื่อเก็บข้อมูลการทำงานของ contriner แบบละเอียด
```
    Form: docker imagesdocker volume create <ชื่อ>
    Ex. docker imagesdocker volume create portainer_data

    //portainer_data คือชื่อของ Portainer ที่เราต้องสร้าง
```
* ใช้สำหรับการ Download หรือ Install ของ **Portainer Server**
```
    docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.11.1

    //เป็นการกำหนดกัน run การทำงาน การไหลผ่านของข้อมูลและการกำหนด version การใช้งานของ Portainer 
```
* แสดงรายการเกี่ยวกับ Network
```
    docker network ls
```

* ถ้าต้องการจะลบ container ใน portainer เราจะต้องหยุดการทำงานก่อนถึงจะลบออกได้
```
    Form: docker stop <id-container>      //หยุดการทำงานของ container
    Ex. docker stop 5cs5835bdc2c9

    Form: docker rm <id-container>       //ลบออก
    Ex. docker rm 5cs5835bdc2c9
```