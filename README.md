# AnomalyDetect
The current version of `AnomalyDetect` detects anomalous heart rate from smartwatch data. `AnomalyDetect` can be used with either RHR (Resting Heart Rate) or HROS (Heart Rate Over Steps) as an input. This method can be applied to any smartwatch data like FitBit, Apple, Garmin and Empatica.


#### Install required packages

```
pip install -r requirements.txt
```

#### Wearable data (Heart rate, steps and sleep) from FitBit users with a COVID-19 diagnosis

```
For a full set (31 users): https://storage.googleapis.com/gbsc-gcp-project-ipop_public/COVID-19/COVID-19-Wearables.zip
```

#### Examples

```
# check results folder for the output

python scripts/rhrad_offline.py --heart_rate data/AHYIJDV_hr.csv --steps data/AHYIJDV_steps.csv
python scripts/hrosad_offline.py --heart_rate data/AHYIJDV_hr.csv --steps data/AHYIJDV_steps.csv
```

## Offline Models 

Offline models use all the data to find anomalies.

#### RHR-AD (Resting Heart Rate) Offline Anomaly Detector

Full command 
```
python rhrad_offline.py \
       --heart_rate hr.csv \
       --steps steps.csv \
       --myphd_id id_offline \
       --figure id_offine.pdf \
       --anomalies id_offline_anomalies.csv \
       --symptom_date 2020-01-30 \
       --diagnosis_date 2020-01-31 \
       --outliers_fraction 0.1 \
       --random_seed 10 
 ```
 

#### HROS-AD (Heart Rate Over Steps) Offline Anomaly Detector

Full command 
```
python hrosad_offline.py \
       --heart_rate hr.csv \
       --steps steps.csv \
       --myphd_id id_offline \
       --figure id_offine.pdf \
       --anomalies id_offline_anomalies.csv \
       --symptom_date 2020-01-30 \
       --diagnosis_date 2020-01-31 \
       --outliers_fraction 0.1 \
       --random_seed 10 
 ```

## Online Models

Online models  split the data into train by taking first 744 hours (1 month) and test by taking the rest of the data, and use a baseline window of length 744 and sliding window of length 1 hour to find anomalies in the test data.

In progress .......

#### Help
```
python rhrad_offline.py -h
python hrosad_offline.py -h
```
