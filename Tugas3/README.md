#SISTEM-PAKAR
Nama    :Dinda Anik Masruro
Kelas   :D4 TI 3C
NPM     :1184003

# Pada Persoalan kali ini kita akan menggunakan Algoritma Naive Bayesian yang digunakan untuk mengklasifikasikan peluang terjadinya sesuatu berdasarkan data yang telah dimiliki sebelumnya.
# Persoalan yang akan kita klasifikasikan dengan Algoritma Naive Bayesian yaitu mengenai Iris yang saya dapatkan dari situs (https://raw.githubusercontent.com/mk-gurucharan/Classification/master/IrisDataset.csv)
# Dataset yang digunakan yaitu iris.txt yang didapatkan dari (https://raw.githubusercontent.com/mk-gurucharan/Classification/master/IrisDataset.csv)
# Data set ini memiliki 5 attrbute yaitu sepal_length, sepal_width, petal_length petal_width, dan species
# Label yang digunakan adalah species. label ini akan digunakan untuk memprediksi jenis tanaman yang akan muncul.

import numpy as np
# digunakan untuk mengimport library numpy
import matplotlib.pyplot as plt
# digunakan untuk mengimport library matplotlib.pyplot
import pandas as pd
# digunakan untuk mengimport library pandas
dataset = pd.read_csv('iris.txt')
# digunakan untuk membaca data dari data set iris.txt
X = dataset.iloc[:,:4].values
y = dataset['species'].values
# digunakan untuk mepresentasikan variabel x dan y yaitu jenis species apa.
dataset.head(5)
# menampilkan data dari variabel dari dataset
from sklearn.model_selection import train_test_split
# mengimport library train_test split dari library sklearn,mode_selection
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2)
#  digunakan untuk mempresetasikan variabel training dan testing
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
# digunakan untuk mengubah data sedemikian rupa sehingga distribusinya akan memiliki nilai rata-rata 0 dan deviasi standar 1.
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)
from sklearn.naive_bayes import GaussianNB
# Mengaktifkan/memanggil/membuat fungsi klasifikasi Naive Bayes
classifier = GaussianNB()
# Memasukkan data training pada fungsi klasifikasi Naive Bayes
classifier.fit(X_train, y_train)
# melakukan proses training 
y_pred = classifier.predict(X_test) 
y_pred
# Menentukan hasil prediksi dari x_test
from sklearn.metrics import confusion_matrix
# mengimport library confusion_matrix
cm = confusion_matrix(y_test, y_pred)
# mempresentasikan confussiona_matrix dari t_test dan y_pred
from sklearn.metrics import accuracy_score 
# mengimport library accuracy_score
print ("Accuracy : ", accuracy_score(y_test, y_pred))
# mencetak hasil dari prediksi
cm
df = pd.DataFrame({'Real Values':y_test, 'Predicted Values':y_pred})
df
from sklearn.metrics import classification_report
# mengimport library classification_report dari sklearn_metrics
print(classification_report(y_test, y_pred))
# mencetak hasil dari prediksi