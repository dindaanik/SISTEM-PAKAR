# -*- coding: utf-8 -*-
"""
Created on Tue Apr 13 13:43:55 2021

@author: Dinda Anik M
"""

# Nama : Dinda Anik Masruro
# NPM : 1184003
# Kelas D4 TI 3C
# Kode program dibawah ini menggunakan algoritma fuzzy sugeno yang digunakan untuk penerimaan CPNS. 
# Penerimaan CPNS didasarkan pada 3 hal yaitu IPK, SKD, dan TPA. Apabila persyaratan ketiganya memenuhi 
# kriteria penerimaan CPNS maka output dari kode program ini yaitu lulus, menunggu panggilan atau tidak lulus
#%%
# mengimport library numpy,skfuzzy,dan matplotlib.pyplot
import numpy as np
import skfuzzy as fuzz
import matplotlib.pyplot as plt
#%%
# Generate semua variabel
# * IPK dipresentasikan pada rentang subjektif [0, 5]
# * SKD dan TPA memiliki rentang [0, 100,150,200,250,300,350,400,450,500,600,650,700,750] dalam satuan poin persentase
x_ipk = np.arange(0, 5, 1)
x_skd = np.arange(350, 630, 1)
x_tpa  = np.arange(0, 750, 1)
#%%
# Generate fuzzy membership functions
# mempresentasikan IPK rendah dalam bentuk trapesium dengan rentang 0 sampai 2
ipk_rendah = fuzz.trapmf(x_ipk,[0, 0.5, 1, 2])
# mempresentasikan IPK sedang dalam bentuk trapesium dengan rentang 1 sampai 4
ipk_sedang = fuzz.trapmf(x_ipk,[1, 2, 3, 4])
# mempresentasikan IPK tinggi dalam bentuk trapesium dengan rentang 3 sampai 4.5
ipk_tinggi = fuzz.trapmf(x_ipk,[3, 4, 4, 4.5])

# mempresentasikan SKD rendah dalam bentuk trapesium dengan rentang 0 sampai 480
skd_rendah = fuzz.trapmf(x_skd,[0, 350, 400, 480])
# mempresentasikan SKD sedang dalam bentuk segitiga dengan rentang 400 sampai 530
skd_sedang = fuzz.trimf(x_skd,[400, 480, 530])
# mempresentasikan SKD tinggi dalam bentuk trapesium dengan rentang 480 sampai 630
skd_tinggi = fuzz.trapmf(x_skd,[480, 530, 600, 630])

# mempresentasikan TPA rendah dalam bentuk trapesium dengan rentang 0 sampai 450
tpa_rendah = fuzz.trapmf(x_tpa,[0, 0, 300, 450])
# mempresentasikan TPA sedang dalam bentuk trapesium dengan rentang 300 sampai 750
tpa_sedang = fuzz.trapmf(x_tpa,[300, 350, 650, 750])
# mempresentasikan TPA tinggi dalam bentuk trapesium dengan rentang 650 sampai 750
tpa_tinggi = fuzz.trapmf(x_tpa,[650, 680, 700, 750])

R = 20
S = 50
T = 100
#%%
# Visualize these universes and membership functions//membuat visualisasi grafik
fig, (ax0, ax1, ax2, ax3) = plt.subplots(nrows=4, figsize=(8, 10))

#mempresentasikan ipk dalam bentuk grafik dari ipk rendah sampai ke ipk tertinggi
ax0.plot(x_ipk, ipk_rendah, 'b', linewidth=1.5, label='Rendah')
ax0.plot(x_ipk, ipk_sedang, 'g', linewidth=1.5, label='Sedang')
ax0.plot(x_ipk, ipk_tinggi, 'r', linewidth=1.5, label='Tinggi')
ax0.set_title('Index Prestasi Mahasiswa')
ax0.legend()

#mempresentasikan toefl dalam bentuk grafik dari skd rendah sampai ke skd tertinggi
ax1.plot(x_skd, skd_rendah, 'b', linewidth=1.5, label='Rendah')
ax1.plot(x_skd, skd_sedang, 'g', linewidth=1.5, label='Sedang')
ax1.plot(x_skd, skd_tinggi, 'r', linewidth=1.5, label='Tinggi')
ax1.set_title('Seleksi Kompetensi Dasar')
ax1.legend()

#mempresentasikan tpakdalam bentuk grafik dari tpa rendah sampai ke tpa tertinggi
ax2.plot(x_tpa, tpa_rendah, 'b', linewidth=1.5, label='Rendah')
ax2.plot(x_tpa, tpa_sedang, 'g', linewidth=1.5, label='Sedang')
ax2.plot(x_tpa, tpa_tinggi, 'r', linewidth=1.5, label='Tinggi')
ax2.set_title('Index TPA')
ax2.legend()

#mempresentasikan hasil dari algoritma fuzzy sugeno dalam bentuk grafik dari ipk,skd, dan tpa rendah sampai ke ipk, skd, dan tpa  tertinggi
ax3.plot([3, 3],[0, T], 'b', linewidth=1.5, label= 'Tinggi')
ax3.plot([2, 2],[0, S], 'g', linewidth=1.5, label= 'Sedang')
ax3.plot([1, 1],[0, R], 'r', linewidth=1.5, label= 'Rendah')
ax3.set_title('Singleton Sugeno')
ax3.legend()
#%%
##Family
R=20
S=50
T=100
M=[(R,R,R,R,S,T,R,T,T),(R,S,S,S,S,T,T,T,T),(R,T,S,T,S,T,T,T,T)]
#%%
# disini dipresentasikan nilai minimal dari ipk, skd, dan tpa dari pegawai yang akan diterima
in_ipk = 3.3
in_skd = 490
in_tpa = 320
#%%
# setelah itu dilakukanlah fuzzification pada ipk,skd, dan tpa untuk melihat hasil dari penerimaan
in_1 =[]
in_1.append(fuzz.interp_membership(x_ipk, ipk_rendah, in_ipk))
in_1.append(fuzz.interp_membership(x_ipk, ipk_sedang, in_ipk))
in_1.append(fuzz.interp_membership(x_ipk, ipk_tinggi, in_ipk))

in_2 =[]
in_2.append(fuzz.interp_membership(x_skd, skd_rendah, in_skd))
in_2.append(fuzz.interp_membership(x_skd, skd_sedang, in_skd))
in_2.append(fuzz.interp_membership(x_skd, skd_tinggi, in_skd))

in_3 =[]
in_3.append(fuzz.interp_membership(x_tpa, tpa_rendah, in_tpa))
in_3.append(fuzz.interp_membership(x_tpa, tpa_sedang, in_tpa))
in_3.append(fuzz.interp_membership(x_tpa, tpa_tinggi, in_tpa))

# mencetak derajat nilai IPK
print("Derajat Keanggotaan Nilai IPK")  
if in_1[0]>0:  
    print("Rendah : "+ str(in_1[0]))  
if in_1[1]>0:  
    print("Sedang : "+ str(in_1[1]))  
if in_1[2]>0:  
    print("Tinggi : "+ str(in_1[2]))  
    
print("") 
# mencetak derajat nilai SKD
print("Derajat Keanggotaan Nilai SKD")  
if in_2[0]>0:  
    print("Rendah : "+ str(in_2[0]))  
if in_2[1]>0:  
    print("Sedang : "+ str(in_2[1]))  
if in_2[2]>0:  
    print("Tinggi : "+ str(in_2[2]))

print("")  
# mencetak derajat nilai TPA
print("Derajat Keanggotaan Nilai TPA")  
if in_3[0]>0:  
    print("Rendah : "+ str(in_3[0]))  
if in_3[1]>0:  
    print("Sedang : "+ str(in_3[1]))  
if in_3[2]>0:  
    print("Rendah : "+ str(in_3[2]))  
#%%

# mencetak hadil  matriks dari nilai IPK, SKD, TPA
print("Matriks Nilai IPK")  
print(in_1)  
print("")  
print("Matriks Nilai SKD")  
print(in_2)  
print("Matriks Nilai TPA")  
print(in_3)  
#%%
#Inferensi dan Defazzifikasi dengan Metode Sugeno  
#Penyebut dari rule yang dibuat
rul =[]  
for i in range(3) :  
    for j in range (3) :  
        rule = fuzz.relation_min(in_1[i], in_2[j])  
        rul.append(rule)  
penyebut=np.sum(rul)  
  
#Pembilang dari rule yang dibuat
rul =[]  
for i in range(3) :  
    for j in range(3) :  
        rule=fuzz.relation_min(in_1[i], in_2[j])  
        rulxx=rule*M[i][j]  
        rul.append(rulxx)  
pembilang=np.sum(rul)  
hasil = pembilang/penyebut  
  
# Setelah dilakukan dezzafikasi maka kita akan melihat hasil dari penerimaan CPNS dengan melihat IPK, SKD, dan TPA
print ("Index Kelayakan Diterima : "+ str(hasil))  
# Jika hasil dari Dezzafikasi lebih dari 0 atau kurang dari 20 atau sama dengan maka CPNS tersebut tidak lulus kualifikasi.
if hasil >=0 and hasil <=20 :  
    za = (abs(hasil - 0)/(20-0))*100  
    zb = (abs(hasil - 20)/(20-0))*100  
    print("Tidak Lulus : "+ '{:2.2f}'.format(zb)+" %")  
    print("Tidak Lulus : "+ '{:2.2f}'.format(za)+" %")  
# Jika hasil dari Dezzafikasi lebih dari 20 atau kurang dari atau sama dengan 50 maka CPNS tersebut tidak lulus kualifikasi atau menunggu pemanggilan selanjutnya.
if hasil >=20 and hasil <=50 :  
    za = (abs(hasil - 20)/(50-20))*100  
    zb = (abs(hasil - 50)/(50-20))*100  
    print("Tidak Lulus : "+ '{:2.2f}'.format(zb)+" %")  
    print("Waiting List : "+ '{:2.2f}'.format(za)+" %")  
if hasil >=50 and hasil <=100 :  
# Jika hasil dari Dezzafikasi lebih dari 50 atau kurang dari atau sama dengan 100 maka CPNS tersebut menunggu pemanggilan atau lulus kualifikasi.
    za = (abs(hasil - 50)/(100-50))*100  
    zb = (abs(hasil - 100)/(100-50))*100  
    print("Waiting List : "+ '{:2.2f}'.format(zb)+" %")  
    print("Lulus : "+ '{:2.2f}'.format(za)+" %")  
    
## Hasil dari dezzafikasi dengan algoritma fuzzy sugeno yaitu yang layak diterima baik itu menunggu ataupun lulus panggilan sebanyak 60%
## Jika di jabarkan lebih lanjut hasil perekrutan pegawai yang mempresentasikan lulus sebanyak 21.43%
## Sedangkan yang menunggu sebanyak 78.57%
