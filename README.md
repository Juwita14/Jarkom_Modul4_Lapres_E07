# Jarkom_Modul4_Lapres_E07
Praktikum Modul 4 Jarkom 2020<br/>
05111840000051 Juwita Kartika Rani<br/>
05111840000115 Muhammad Rafi Yudhistira<br/>
05111840007004 Siti Munawaroh

## VLSM (Variable Length Subnet Masking) - CPT
<br/>Untuk server MOJOKERTO dan MALANG, tidak perlu diikutkan dalam subnet pembagian IP, karena mereka menggunakan NID DMZ: 10.151.79.64/29, di mana akan dipecah masing-masing mendapatkan NID 10.151.79.64/30 dan 10.151.79.68/30.
<br/>![image](https://user-images.githubusercontent.com/58022238/102002440-13361200-3d2f-11eb-8c64-a7126a76e6e9.png)
<br/>![image](https://user-images.githubusercontent.com/58022238/102008485-80639a80-3d63-11eb-96be-160948024eaa.png)
<br/> Subnet besar yang dibentuk memiliki NID 192.168.0.0 dengan netmask /19. Pembagian IP berdasarkan NID dan netmask dihitung menggunakan pohon pada gambar di bawah:
<br/>![vlsm](https://user-images.githubusercontent.com/58022238/102008592-565ea800-3d64-11eb-9aff-71af88d93f09.png)
<br/>Kemudian jika NID dibagikan pada setiap subnet pada topologi, akan menjadi sebagai berikut:
<br/>![image](https://user-images.githubusercontent.com/58022238/102008720-28c62e80-3d65-11eb-8558-fd9b413c2ba1.png)
<br/>Untuk routing pada CPT, diberikan static route pada semua router yang ada dengan route sebagai berikut untuk setiap router:

![image](https://user-images.githubusercontent.com/58022238/102008952-cbcb7800-3d66-11eb-9aff-b49d16c0d23a.png)

# CIDR (Classless Inter Domain Routing) - UML
Menggabungkan subnet-subnet mulai dari yang paling jauh dalam topologi, penggabungannya:

<br/>![image](https://user-images.githubusercontent.com/58022238/102002475-732cb880-3d2f-11eb-8d44-c08a084a0a73.png)
<br/>![image](https://user-images.githubusercontent.com/58022238/102002480-7de74d80-3d2f-11eb-90b7-8bf10889f982.png)
<br/>![image](https://user-images.githubusercontent.com/58022238/102002487-97889500-3d2f-11eb-883e-6beee14b1395.png)
<br/>![image](https://user-images.githubusercontent.com/58022238/102002491-a2dbc080-3d2f-11eb-832c-3315f5cd05da.png)
<br/>Sehingga di dapatkan berikut pohon pembagian IP berdasarkan penggabungan subnet yang telah dilakukan:

<br/>![image](https://user-images.githubusercontent.com/58022238/102009334-5b722600-3d69-11eb-9db4-9193cf7461b6.png)

<br/>Pertama membuat file ```topologi.sh``` dengan konfigurasi berikut:
```
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.78.33 eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch4 eth4=daemon,,,switch13 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch2 eth1=daemon,,,switch3 eth2=daemon,,,switch19 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch3 eth1=daemon,,,switch15 eth2=daemon,,,switch16 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch4 eth1=daemon,,,switch5 eth2=daemon,,,switch21 eth3=daemon,,,switch22 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch17 eth2=daemon,,,switch18 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

# Klien
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
```
