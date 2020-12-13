# Jarkom_Modul4_Lapres_E07
Praktikum Modul 4 Jarkom 2020<br/>
05111840000051 Juwita Kartika Rani<br/>
05111840000115 Muhammad Rafi Yudhistira<br/>
05111840007004 Siti Munawaroh

## VLSM

<br/>![image](https://user-images.githubusercontent.com/58022238/102002440-13361200-3d2f-11eb-8c64-a7126a76e6e9.png)

<br/>![image](https://user-images.githubusercontent.com/58022238/102008485-80639a80-3d63-11eb-96be-160948024eaa.png)
<br/> Subnet besar yang dibentuk memiliki NID 192.168.0.0 dengan netmask /19. Pembagian IP berdasarkan NID dan netmask dihitung menggunakan pohon pada gambar di bawah:
<br/>![vlsm](https://user-images.githubusercontent.com/58022238/102008592-565ea800-3d64-11eb-9aff-71af88d93f09.png)
<br/>Kemudian jika NID dibagikan pada setiap subnet pada topologi, akan menjadi sebagai berikut:
<br/>![image](https://user-images.githubusercontent.com/58022238/102008720-28c62e80-3d65-11eb-8558-fd9b413c2ba1.png)
<br/>Untuk routing pada CPT, diberikan static route pada semua router yang ada dengan route sebagai berikut untuk setiap router:

![image](https://user-images.githubusercontent.com/58022238/102008952-cbcb7800-3d66-11eb-9aff-b49d16c0d23a.png)

# CIDR (Classless Inter Domain Routing) - UML
## Menggabungkan subnet-subnet mulai dari yang paling jauh dalam topologi, penggabungannya:

# ![image](https://user-images.githubusercontent.com/58022238/102002475-732cb880-3d2f-11eb-8d44-c08a084a0a73.png)
# ![image](https://user-images.githubusercontent.com/58022238/102002480-7de74d80-3d2f-11eb-90b7-8bf10889f982.png)
# ![image](https://user-images.githubusercontent.com/58022238/102002487-97889500-3d2f-11eb-883e-6beee14b1395.png)
# ![image](https://user-images.githubusercontent.com/58022238/102002491-a2dbc080-3d2f-11eb-832c-3315f5cd05da.png)
## Sehingga di dapatkan berikut pohon pembagian IP berdasarkan penggabungan subnet yang telah dilakukan:
# 
![image](https://user-images.githubusercontent.com/58022238/102009334-5b722600-3d69-11eb-9db4-9193cf7461b6.png)
