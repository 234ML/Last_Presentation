# Seoul_Bike_Sharing_Demand_Prediction
## Topic: Predicting demand for rented bicycles around Ewha, Seodaemun-gu and Mapo-gu

### Environment Setting
- Google Colab
- model name	: AMD EPYC 7B12
- number of CPU cores : 2

### Specification of memory(RAM)
- MemTotal :       13297228 kB
- MemFree :         7424924 kB
- MemAvailable :   11290352 kB

### Dataset
- Original Dataset: 
    - “공공자전거 대여소 정보(22.06월 기준).csv” from 서울 열린데이터 광장(Seoul Open Data Plaza)(https://data.seoul.go.kr/)
    - “서울특별시 공공자전거 이용정보(시간대별)_21.01.csv”~“서울특별시 공공자전거 이용정보(시간대별)_21.12.csv” from 서울 열린데이터 광장(Seoul Open Data Plaza)(https://data.seoul.go.kr/)
    - “SURFACE_ASOS_108_HR_2021_2021_2022.csv”(서울특별시 2021년도 종관기상관측자료) from 기상자료개방 포털(KMA) (https://data.kma.go.kr/data/grnd/selectAsosRltmList.do?pgmNo=36)

- Original Dataset is too big, so we preprocessed data and reduced the size of dataset
    - we dropped correlated features of weather data. and merge it to bike sharing data.
    you can see that process in
    - Our Dataset: seodaemunAndmapo.csv (72,463KB) (Total number of this dataset: 972799)
    ![image](https://user-images.githubusercontent.com/76611903/208368643-81ae2c38-07aa-4228-bb05-ca7c1adb7868.png)
    
### Models
- RandomForest and Gradient Boosting (In this project, the result of gradient boosting was better than random forest)
- Hyperparameter Search: GridSearch
- After Hyperparameter tuning, R2 Score of Gradient Boosting was 0.9380330070944691

### To Run this project
1. Download notebook file. (seoul_bike_sharing_damand_prediction.ipynb)
2. Download dataset file(seodaemunAndmapo.zip), unzip this file, and get seodaemunAndmapo.csv file.
3. Open notebook file in Colab and upload csv file to Colab or your Google Drive.
4. Run cells
- The features of our datset is korean. so, you need to install fonts following the instruction at the top of the notebooke file.
```python
# For Hangeul Font Issue
!sudo apt-get install -y fonts-nanum
!sudo fc-cache -fv
!rm ~/.cache/matplotlib -rf
```
<img width="273" alt="image" src="https://user-images.githubusercontent.com/86579242/208375428-19de666c-d326-40f7-a083-f8bf328947ff.png">
run this cell and restart runtime

- If you downloaded project files on your drive, then Mount your Google Drive.
```
# Mounting Google Drive 
from google.colab import drive
drive.mount('/content/drive')
```

- set the data path(location of seodaemunAndmapo.csv) to DATA_PATH

*. the path should be absolute path

```
# set data path
import os
DATA_PATH = '/content/drive/MyDrive/seodaemunAndmapo.csv'
```

- run cells to load dataset, data preprocessing, train model, evaluation, interpretation



### References
- kaggle ([https://www.kaggle.com/code/kwonyoung234/for-beginner/notebook](https://www.kaggle.com/code/kwonyoung234/for-beginner/notebook))
- scikit-learn (https://scikit-learn.org/)
- matplotlib (https://matplotlib.org/)
- heumsi's github ([https://github.com/heumsi/Seoul-Public-bicycles-EDA](https://github.com/heumsi/Seoul-Public-bicycles-EDA))
