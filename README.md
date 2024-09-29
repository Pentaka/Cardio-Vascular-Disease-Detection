# Cardio-Vascular-Disease-Detection

Bu veri seti [Kaggle](https://www.kaggle.com/datasets/bhadaneeraj/cardio-vascular-disease-detection)'dan alınmıştır.

## EDA

1.	Age | Objective Feature | age | int (days)
2.	Height | Objective Feature | height | int (cm) |
3.	Weight | Objective Feature | weight | float (kg) |
4.	Gender | Objective Feature | gender | categorical code |
5.	Systolic blood pressure | Examination Feature | ap_hi | int |
6.	Diastolic blood pressure | Examination Feature | ap_lo | int |
7.	Cholesterol | Examination Feature | cholesterol | 1: normal, 2: above normal, 3: well above normal |
8.	Glucose | Examination Feature | gluc | 1: normal, 2: above normal, 3: well above normal |
9.	Smoking | Subjective Feature | smoke | binary |
10.	Alcohol intake | Subjective Feature | alco | binary |
11.	Physical activity | Subjective Feature | active | binary |
12.	Presence or absence of cardiovascular disease | Target Variable | cardio | binary |

## Ağırlık
<img src=https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/Agirlik_grafik.png>

Ağırlık grafiği incelendiğinde veri bütünü ortada gibi görünse de aykırı değerlerin olduğu saptanmıştır.

## Yaş

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/yas_grafik.png>

Yaşlar yıl bazına dönüştürülüp grafik incelendiğinde ağırlıkta olduğu gibi aykırı değerlerin olduğu görülmektedir.

## Boy

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/boy_grafik.png >

Boy grafiğinde de çok miktarda aykırı değer olduğu görülmektedir.

## Cinsiyet

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/cinsiyet_grafik.png >

Verideki cinsiyet dağılımı incelendiğinde neredeyse 1'in, 0'ın iki katı olduğu görülmektedir.

## Glukoz

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/glukoz_grafik.png >

Glukoz dağılımı incelendiğinde yüksek sayıda hastanın değerlerinin normal, azınlıktaki bir grup hastanın da normalin üstünde ve normalin çok üstünde görüldüğü sonucuna varılmaktadır.

## Kolestrol

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/kolesterol_grafik.png >

Kolestrol dağılımı incelendiğinde yine yüksek sayıda normal hasta bulunduğu ve çok daha az miktarda normalin üstünde ve normalin çok üstünde hasta bulunduğu görülmektedir.

## Kardiyo-Vasküler Hastalık

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/kardiyovaskuler_hastalik_grafik.png >

Veri setinde hastalığa sahip olan ve olmayan bireylerin küçük fark ile biribirine eşit olduğu görülmektedir. 

## Veri Ön İşleme

Öncelikle veri setindeki id sütunu, çalışmaya herhangi bir etki etmeyeceği için çıkarılmıştır.
Daha sonra Null değerler kontrol edilerek Null değerin olmadığı saptanmıştır. Sayısal verilerin uç değerlerindeki aykırı noktaların temizlenmesi için Çeyrekler Arası Aralık (IQR) yöntemi kullanılarak
veri seti yeniden şekillendirilmiştir. Aykırı değerler çıkarılınca oluşan grafikler şu şekildedir:

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_agirlik_grafik.png>

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_boy_grafik.png >

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_yas_grafik.png >

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_sonras%C4%B1_diastolic_blood_pressure_da%C4%9Filimi.png >

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_sonras%C4%B1_systolic_blood_pressure_dagilimi.png >



<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerler_grafik.png >

<img src= https://github.com/Pentaka/Cardio-Vascular-Disease-Detection/blob/main/hastalik/aykiri_degerlerin_olmadigi_veriler_grafik.png >


Aykırı değerler çıkarıldıktan sonra veriler train ve test olarak ikiye bölündü. Bölünen verilerdeki sayısal değerler MinMaxScaler ile normalize edilerek modelleme için uygun bir hale getirildi.
Eğitim için gradient boosting algoritmalarının çeşidinden olan ve ağaç tabanlı modeller üreten makine öğrenmesi algoritması olan LightGBM algoritması kullanıldı.

Elde edilen tahminleme sonuçları da şu şekilde:

Doğruluk Oranı:  0.736636409480585
              precision    recall  f1-score   support

           0       0.72      0.81      0.76      8177
           1       0.76      0.66      0.71      7687

    accuracy                           0.74     15864
   macro avg       0.74      0.73      0.73     15864
weighted avg       0.74      0.74      0.74     15864

Kodu çalıştırmak için gereken kütüphaneler:

-pip install pandas
-pip install seaborn
-pip install matplotlib
-pip install tensorflow
-pip install lightgbm
-pip install scikit-learn
