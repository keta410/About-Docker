# สรุปความเข้าใจเกี่ยวกับ Docker command

* สำหรับการ check **version Docker** 
 ```
    Form: docker version
 ```

* เกี่ยวกับ **containers**
``` 
    Form: docker ps       //ดู container ที่กำลังทำงานอยู่
    Form: docker ps -a    //ดู container ทั้งหมดที่มี
    Form: docker rm <id contrainer>     //ลบ contrainer นั้นๆ
    Form: docker inspect <id contrainer>    //ดูรายละเอียดเกี่ยวกับ contrainer นั้นๆ
```
* เกี่ยวกับ **images**
```
    Form: docker images         //ดู image ที่มีอยู่ในเครื่อง
```
* เกี่ยวกับ **volume**
```
    Form: docker volume ls      //ดู volume ที่มี
```
* เกี่ยวกับ **Network**
```
    Form: docker network create <name>      //สร้าง network
    Ex. docker network create web_network

    Form: docker network ls                 //ดู Network ที่มีทั้งหมด
```
* เกี่ยวกับ **docker-compose** ที่ใช้สำหรับการทำงานกับหลายๆ container
```
    Form: docker-compose ps         //ดู container ทั้งหมดที่กำลังทำงาน
    Form: docker-compose up         //อัพข้อมูลขึ้น
    Form: docker-compose down       //เอาข้อมูลลง
    Form: docker-compose build      //สร้าง container ทั้งหมด ที่ up
    Form: docker-compose build <name>  //สร้าง container
```

## Docker กับ Portainer

* ใช้สำหรับการสร้างพื้นที่ไว้เก็บข้อมูลของ **Portainer** (แบบถาวร) เพื่อเก็บข้อมูลการทำงานของ contriner แบบละเอียด
```
    Form: docker imagesdocker volume create <name>
    Ex. docker imagesdocker volume create portainer_data

    //portainer_data คือชื่อของ Portainer ที่เราต้องสร้าง
```
* ใช้สำหรับการ Download หรือ Install ของ **Portainer Server**
```
    docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.11.1

    //เป็นการกำหนดกัน run การทำงาน การไหลผ่านของข้อมูลและการกำหนด version การใช้งานของ Portainer 
```

* ถ้าต้องการจะลบ container ใน portainer เราจะต้องหยุดการทำงานก่อนถึงจะลบออกได้
```
    Form: docker stop <id-container>      //หยุดการทำงานของ container
    Ex. docker stop 5cs5835bdc2c9

    Form: docker rm <id-container>       //ลบ container
    Ex. docker rm 5cs5835bdc2c9
```
