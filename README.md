# Data Science 
* Data.csv veri seti kullanılarak geliştirildi.
## Kütüphaneler 
* import numpy as np
* import pandas as pd 
* import matplotlib as mpl
* import seaborn as sns

## Veri Analizi 
* NumPy (Numerical Python) bilimsel hesaplamaları hızlı bir şekilde yapmayı sağlayan bir matematik kütüphanesidir. Numpy’ın temelini numpy dizileri oluşturur. 
* Pandas kütüphanesi ile veri organize edilerek analizler daha kolay ve hızlı şekilde gerçekleştirilir.

## Veri Görselleştirme
* Matplotlib, kaliteli histogramlar, güç spektrumları, çubuk grafikleri, hata çizelgeleri ve vb. şekiller üretmek için 2 boyutlu çizim kütüphanesidir.
* Seaborn, MatPlotLib kütüphanesini temel alır. Veri seti tabanlı çizim fonksiyonları, dataframes (özellikle Pandas) ve arrays (özellikle Numpy arrays) içeren veri setleri üzerinde çalışır. 



- Python kütüphanelerinden yararlanılarak veri ön işleme adımları gerçekleştirildi.
- Veri seti hakkında detaylı bilgi edinebilmek adına veri özelliklerine ve istatiksel değerlere bakıldı. Koveryans ve korelasyon hesapları yapıldıktan sonra veri görselleştirmek adımlarına geçildi. 
- Elimizde bulunan verilerin null sorgulaması yapıldı.
- Eksik veriler tespit edilerek veri tamamlama işlemleri gerçekleştirildi. (median kullanılarak eksik veriler doldurulmuştur.)
- Sütunlardaki tüm NaN değerleri  sıfır(0) ile değiştirildi.
- Aykırı verilerle ilgili işlemler yapıldı. 
```javascript
def outliers(s):
    iqr = (np.quantile(s, 0.75))-(np.quantile(s, 0.25))
    upper_bound = np.quantile(s, 0.75)+(1.5*iqr)
    lower_bound = np.quantile(s, 0.25)-(1.5*iqr)
    f = []
    for i in s:
        if i > upper_bound:
            f.append(i)
        elif i < lower_bound:
            f.append(i)
    sums = len(f)
    pros = len(f)/len(s)*100
    d = {'IQR':iqr,
         'Upper Bound':upper_bound,
        'Lower Bound':lower_bound,
        'Sum outliers': sums,'percentage outliers':pros}
    d = pd.DataFrame(d.items(),columns = ['sub','values'])
    return(d)
    
outliers(df.Elevation)
```
Aykırı veriler temizlenirken; kutu grafiği kullanma, 5 sayı özeti ile uç değer belirleme, standart sapma yöntemleri ile tespit edilir.
- Kutu Grafiği (Box-Plot) Yöntemi ile aykırı değer belirleme işlemi basitçe gerçekleşir. Kutu grafiği medyan ve dörtlükler kullanılarak elde edilmektedir.


