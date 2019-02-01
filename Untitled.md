

```python
"""The following tables are available data in the MIMIC iii database. The documentation page is copied below. 
Please quickly consult with this page if content of some of the tables of variables are not clear to you.
The list of tables is in the left. Click on the table and you will see the list of variables and their decription.
https://mimic.physionet.org/mimictables/inputevents_cv/"""
```


```python
import numpy as np
import pandas as pd
import csv
```


```python
admissions = []
j = 0
with open('./ADMISSIONS.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        admissions += [row]
        j += 1
        if j > 100:
        	break

admissions_ = pd.DataFrame(admissions[1:])
admissions_.columns = admissions[0]

```


```python
print('list of variable in the admissions table')
print(list(admissions_))
```

    list of variable
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ADMITTIME', 'DISCHTIME', 'DEATHTIME', 'ADMISSION_TYPE', 'ADMISSION_LOCATION', 'DISCHARGE_LOCATION', 'INSURANCE', 'LANGUAGE', 'RELIGION', 'MARITAL_STATUS', 'ETHNICITY', 'EDREGTIME', 'EDOUTTIME', 'DIAGNOSIS', 'HOSPITAL_EXPIRE_FLAG', 'HAS_CHARTEVENTS_DATA']



```python
print('First five rows of the admissions table')
print(admissions_.loc[:4, :])
```

    First five rows of the table
      ROW_ID SUBJECT_ID HADM_ID            ADMITTIME            DISCHTIME  \
    0     21         22  165315  2196-04-09 12:26:00  2196-04-10 15:54:00   
    1     22         23  152223  2153-09-03 07:15:00  2153-09-08 19:10:00   
    2     23         23  124321  2157-10-18 19:34:00  2157-10-25 14:00:00   
    3     24         24  161859  2139-06-06 16:14:00  2139-06-09 12:48:00   
    4     25         25  129635  2160-11-02 02:06:00  2160-11-05 14:55:00   
    
      DEATHTIME ADMISSION_TYPE         ADMISSION_LOCATION  \
    0                EMERGENCY       EMERGENCY ROOM ADMIT   
    1                 ELECTIVE  PHYS REFERRAL/NORMAL DELI   
    2                EMERGENCY  TRANSFER FROM HOSP/EXTRAM   
    3                EMERGENCY  TRANSFER FROM HOSP/EXTRAM   
    4                EMERGENCY       EMERGENCY ROOM ADMIT   
    
              DISCHARGE_LOCATION INSURANCE LANGUAGE           RELIGION  \
    0  DISC-TRAN CANCER/CHLDRN H   Private                UNOBTAINABLE   
    1           HOME HEALTH CARE  Medicare                    CATHOLIC   
    2           HOME HEALTH CARE  Medicare     ENGL           CATHOLIC   
    3                       HOME   Private           PROTESTANT QUAKER   
    4                       HOME   Private                UNOBTAINABLE   
    
      MARITAL_STATUS ETHNICITY            EDREGTIME            EDOUTTIME  \
    0        MARRIED     WHITE  2196-04-09 10:06:00  2196-04-09 13:24:00   
    1        MARRIED     WHITE                                             
    2        MARRIED     WHITE                                             
    3         SINGLE     WHITE                                             
    4        MARRIED     WHITE  2160-11-02 01:01:00  2160-11-02 04:27:00   
    
                                               DIAGNOSIS HOSPITAL_EXPIRE_FLAG  \
    0                            BENZODIAZEPINE OVERDOSE                    0   
    1  CORONARY ARTERY DISEASE\CORONARY ARTERY BYPASS...                    0   
    2                                         BRAIN MASS                    0   
    3                     INTERIOR MYOCARDIAL INFARCTION                    0   
    4                            ACUTE CORONARY SYNDROME                    0   
    
      HAS_CHARTEVENTS_DATA  
    0                    1  
    1                    1  
    2                    1  
    3                    1  
    4                    1  



```python
data = []
j = 0
with open('PROCEDURES_ICD.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    line_count = 0
    for row in csv_reader:
        data += [row]
        j += 1
        if j>100:
          break

np_data = np.array(data)
df_data = pd.DataFrame(np_data[1: ,:])
df_data.columns = np_data[0, :]
df_data['values'] = 1
```


```python
print('list of variables in the ICD procedure table')
print(list(df_data))
```

    list of variables in the ICD procedure table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'SEQ_NUM', 'ICD9_CODE', 'values']



```python
print('First five rows of the ICD procedure table')
print(df_data.loc[:4, :])
```

    First five rows of the  in the ICD procedure table
      ROW_ID SUBJECT_ID HADM_ID SEQ_NUM ICD9_CODE  values
    0    944      62641  154460       3      3404       1
    1    945       2592  130856       1      9671       1
    2    946       2592  130856       2      3893       1
    3    947      55357  119355       1      9672       1
    4    948      55357  119355       2      0331       1



```python
data = []
j = 0
with open('DIAGNOSES_ICD.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    line_count = 0
    for row in csv_reader:
        data += [row]
        j += 1
        if j>100:
          break

np_data = np.array(data)
df_data = pd.DataFrame(np_data[1: ,:])
df_data.columns = np_data[0, :]
df_data['values'] = 1
```


```python
print('list of variables in the ICD diagnosis table')
print(list(df_data))
```

    list of variables in the ICD diagnosis table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'SEQ_NUM', 'ICD9_CODE', 'values']



```python
print('First five rows of the ICD diagnosis table')
print(df_data.loc[:4, :])
```

    First five rows of the  in the ICD diagnosis table
      ROW_ID SUBJECT_ID HADM_ID SEQ_NUM ICD9_CODE  values
    0   1297        109  172335       1     40301       1
    1   1298        109  172335       2       486       1
    2   1299        109  172335       3     58281       1
    3   1300        109  172335       4      5855       1
    4   1301        109  172335       5      4254       1



```python
ICUstays = []
j = 0
with open('./ICUSTAYS.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        ICUstays += [row]
        j += 1
        if j > 100:
        	break

ICUstays_ = pd.DataFrame(ICUstays[1:])
ICUstays_.columns = ICUstays[0]
```


```python
print('list of variables in the ICU stays table')
print(list(ICUstays_))
```

    list of variables in the ICU stays table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'DBSOURCE', 'FIRST_CAREUNIT', 'LAST_CAREUNIT', 'FIRST_WARDID', 'LAST_WARDID', 'INTIME', 'OUTTIME', 'LOS']



```python
print('First five rows of the ICU stays table')
print(ICUstays_.loc[:4, :])
```

    First five rows of the  in the ICU stays table
      ROW_ID SUBJECT_ID HADM_ID ICUSTAY_ID DBSOURCE FIRST_CAREUNIT LAST_CAREUNIT  \
    0    365        268  110404     280836  carevue           MICU          MICU   
    1    366        269  106296     206613  carevue           MICU          MICU   
    2    367        270  188028     220345  carevue            CCU           CCU   
    3    368        271  173727     249196  carevue           MICU          SICU   
    4    369        272  164716     210407  carevue            CCU           CCU   
    
      FIRST_WARDID LAST_WARDID               INTIME              OUTTIME     LOS  
    0           52          52  2198-02-14 23:27:38  2198-02-18 05:26:11   3.249  
    1           52          52  2170-11-05 11:05:29  2170-11-08 17:46:57  3.2788  
    2           57          57  2128-06-24 15:05:20  2128-06-27 12:32:29  2.8939  
    3           52          23  2120-08-07 23:12:42  2120-08-10 00:39:04    2.06  
    4           57          57  2186-12-25 21:08:04  2186-12-27 12:01:13  1.6202  



```python
input_events_CareVue = []
j = 0
with open('./INPUTEVENTS_CV.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        input_events_CareVue += [row]
        j += 1
        if j > 100:
        	break

input_events_CareVue_ = pd.DataFrame(input_events_CareVue[1:])
input_events_CareVue_.columns = input_events_CareVue[0]
```


```python
print('list of variables in the input events (CareVue) table')
print(list(input_events_CareVue_))
```

    list of variables in the input events table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'CHARTTIME', 'ITEMID', 'AMOUNT', 'AMOUNTUOM', 'RATE', 'RATEUOM', 'STORETIME', 'CGID', 'ORDERID', 'LINKORDERID', 'STOPPED', 'NEWBOTTLE', 'ORIGINALAMOUNT', 'ORIGINALAMOUNTUOM', 'ORIGINALROUTE', 'ORIGINALRATE', 'ORIGINALRATEUOM', 'ORIGINALSITE']



```python
print('First five rows of the input events (CareVue) table')
print(input_events_CareVue_.loc[:4, :])
```

    First five rows of the  in the input events table
      ROW_ID SUBJECT_ID HADM_ID ICUSTAY_ID            CHARTTIME ITEMID AMOUNT  \
    0    592      24457  184834     205776  2193-09-11 09:00:00  30056    100   
    1    593      24457  184834     205776  2193-09-11 12:00:00  30056    200   
    2    594      24457  184834     205776  2193-09-11 16:00:00  30056    160   
    3    595      24457  184834     205776  2193-09-11 19:00:00  30056    240   
    4    596      24457  184834     205776  2193-09-11 21:00:00  30056     50   
    
      AMOUNTUOM RATE RATEUOM     ...       ORDERID LINKORDERID STOPPED NEWBOTTLE  \
    0        ml                  ...        756654     9359133                     
    1        ml                  ...       3564075     9359133                     
    2        ml                  ...        422646     9359133                     
    3        ml                  ...       5137889     9359133                     
    4        ml                  ...       8343792     9359133                     
    
      ORIGINALAMOUNT ORIGINALAMOUNTUOM ORIGINALROUTE ORIGINALRATE ORIGINALRATEUOM  \
    0                               ml          Oral                                
    1                               ml          Oral                                
    2                               ml          Oral                                
    3                               ml          Oral                                
    4                               ml          Oral                                
    
      ORIGINALSITE  
    0               
    1               
    2               
    3               
    4               
    
    [5 rows x 22 columns]



```python
input_events_Metavision = []
j = 0
with open('./INPUTEVENTS_MV.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        input_events_Metavision += [row]
        j += 1
        if j > 100:
            break

input_events_Metavision_ = pd.DataFrame(input_events_Metavision[1:])
input_events_Metavision_.columns = input_events_Metavision[0]

```


```python
print('list of variables in the input events (Metavision) table')
print(list(input_events_Metavision_))
```

    list of variables in the input events (Metavision) table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'STARTTIME', 'ENDTIME', 'ITEMID', 'AMOUNT', 'AMOUNTUOM', 'RATE', 'RATEUOM', 'STORETIME', 'CGID', 'ORDERID', 'LINKORDERID', 'ORDERCATEGORYNAME', 'SECONDARYORDERCATEGORYNAME', 'ORDERCOMPONENTTYPEDESCRIPTION', 'ORDERCATEGORYDESCRIPTION', 'PATIENTWEIGHT', 'TOTALAMOUNT', 'TOTALAMOUNTUOM', 'ISOPENBAG', 'CONTINUEINNEXTDEPT', 'CANCELREASON', 'STATUSDESCRIPTION', 'COMMENTS_EDITEDBY', 'COMMENTS_CANCELEDBY', 'COMMENTS_DATE', 'ORIGINALAMOUNT', 'ORIGINALRATE']



```python
print('First five rows of the input events (Metavision) table')
print(input_events_Metavision_.loc[:4, :])
```

    First five rows of the  in the input events (Metavision) table
      ROW_ID SUBJECT_ID HADM_ID ICUSTAY_ID            STARTTIME  \
    0    241      27063  139787     223259  2133-02-05 06:29:00   
    1    242      27063  139787     223259  2133-02-05 05:34:00   
    2    243      27063  139787     223259  2133-02-05 05:34:00   
    3    244      27063  139787     223259  2133-02-03 12:00:00   
    4    245      27063  139787     223259  2133-02-03 12:00:00   
    
                   ENDTIME  ITEMID       AMOUNT AMOUNTUOM       RATE     ...       \
    0  2133-02-05 08:45:00  225166  6.774531824       mEq                ...        
    1  2133-02-05 06:30:00  225944   28.1329972        ml  30.142497     ...        
    2  2133-02-05 06:30:00  225166  2.813299944       mEq                ...        
    3  2133-02-03 12:01:00  225893            1      dose                ...        
    4  2133-02-03 12:01:00  220949          100        ml                ...        
    
      TOTALAMOUNTUOM ISOPENBAG CONTINUEINNEXTDEPT CANCELREASON STATUSDESCRIPTION  \
    0             ml         0                  0            1         Rewritten   
    1             ml         0                  0            0   FinishedRunning   
    2             ml         0                  0            0   FinishedRunning   
    3             ml         0                  0            2         Rewritten   
    4             ml         0                  0            2         Rewritten   
    
      COMMENTS_EDITEDBY COMMENTS_CANCELEDBY        COMMENTS_DATE ORIGINALAMOUNT  \
    0                                    RN  2133-02-05 12:52:00             10   
    1                                                                 28.132998   
    2                                                                 2.8132997   
    3                RN                      2133-02-03 17:06:00              1   
    4                RN                      2133-02-03 17:06:00            100   
    
      ORIGINALRATE  
    0   .050000001  
    1    30.255817  
    2   .050426364  
    3            1  
    4            0  
    
    [5 rows x 31 columns]



```python
output_events = []
j = 0
with open('./OUTPUTEVENTS.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        output_events += [row]
        j += 1
        if j > 100:
        	break


output_events_ = pd.DataFrame(output_events[1:])
output_events_.columns = output_events[0]

```


```python
print('list of variables in the output events table')
print(list(output_events_))
```

    list of variables in the output events table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'CHARTTIME', 'ITEMID', 'VALUE', 'VALUEUOM', 'STORETIME', 'CGID', 'STOPPED', 'NEWBOTTLE', 'ISERROR']



```python
print('First five rows of the output events table')
print(output_events_.loc[:4, :])
```

    First five rows of the  in the output events table
      ROW_ID SUBJECT_ID HADM_ID ICUSTAY_ID            CHARTTIME ITEMID VALUE  \
    0    344      21219  177991     225765  2142-09-08 10:00:00  40055   200   
    1    345      21219  177991     225765  2142-09-08 12:00:00  40055   200   
    2    346      21219  177991     225765  2142-09-08 13:00:00  40055   120   
    3    347      21219  177991     225765  2142-09-08 14:00:00  40055   100   
    4    348      21219  177991     225765  2142-09-08 16:00:00  40055   200   
    
      VALUEUOM            STORETIME   CGID STOPPED NEWBOTTLE ISERROR  
    0       ml  2142-09-08 12:08:00  17269                            
    1       ml  2142-09-08 12:08:00  17269                            
    2       ml  2142-09-08 13:39:00  17269                            
    3       ml  2142-09-08 16:17:00  17269                            
    4       ml  2142-09-08 16:17:00  17269                            



```python
service = []
j = 0
with open('./SERVICES.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        service += [row]
        j += 1
        if j > 100:
        	break


service_ = pd.DataFrame(service[1:])
service_.columns = service[0]

```


```python
print('list of variables in the service table')
print(list(service_))
```

    list of variables in the service table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'TRANSFERTIME', 'PREV_SERVICE', 'CURR_SERVICE']



```python
print('First five rows of the service table')
print(service_.loc[:4, :])
```

    First five rows of the  in the service table
      ROW_ID SUBJECT_ID HADM_ID         TRANSFERTIME PREV_SERVICE CURR_SERVICE
    0    758        471  135879  2122-07-22 14:07:27        TSURG          MED
    1    759        471  135879  2122-07-26 18:31:49          MED        TSURG
    2    760        472  173064  2172-09-28 19:22:15                      CMED
    3    761        473  129194  2201-01-09 20:16:45                        NB
    4    762        474  194246  2181-03-23 08:24:41                        NB



```python
prescription = []
j = 0
with open('./PRESCRIPTIONS.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        prescription += [row]
        j += 1
        if j > 100:
        	break


prescription_ = pd.DataFrame(prescription[1:])
prescription_.columns = prescription[0]

```


```python
print('list of variables in the prescription table')
print(list(prescription_))
```

    list of variables in the prescription table
    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'STARTDATE', 'ENDDATE', 'DRUG_TYPE', 'DRUG', 'DRUG_NAME_POE', 'DRUG_NAME_GENERIC', 'FORMULARY_DRUG_CD', 'GSN', 'NDC', 'PROD_STRENGTH', 'DOSE_VAL_RX', 'DOSE_UNIT_RX', 'FORM_VAL_DISP', 'FORM_UNIT_DISP', 'ROUTE']



```python
print('First five rows of the prescription table')
print(prescription_.loc[:4, :])
```

    First five rows of the prescription table
        ROW_ID SUBJECT_ID HADM_ID ICUSTAY_ID            STARTDATE  \
    0  2214776          6  107064             2175-06-11 00:00:00   
    1  2214775          6  107064             2175-06-11 00:00:00   
    2  2215524          6  107064             2175-06-11 00:00:00   
    3  2216265          6  107064             2175-06-11 00:00:00   
    4  2214773          6  107064             2175-06-11 00:00:00   
    
                   ENDDATE DRUG_TYPE            DRUG DRUG_NAME_POE  \
    0  2175-06-12 00:00:00      MAIN      Tacrolimus    Tacrolimus   
    1  2175-06-12 00:00:00      MAIN        Warfarin      Warfarin   
    2  2175-06-12 00:00:00      MAIN  Heparin Sodium                 
    3  2175-06-12 00:00:00      BASE             D5W                 
    4  2175-06-12 00:00:00      MAIN      Furosemide    Furosemide   
    
      DRUG_NAME_GENERIC FORMULARY_DRUG_CD     GSN          NDC  \
    0        Tacrolimus             TACR1  021796  00469061711   
    1          Warfarin             WARF5  006562  00056017275   
    2                          HEPAPREMIX  006522  00338055002   
    3                             HEPBASE                    0   
    4        Furosemide            FURO20  008208  00054829725   
    
                PROD_STRENGTH DOSE_VAL_RX DOSE_UNIT_RX FORM_VAL_DISP  \
    0             1mg Capsule           2           mg             2   
    1              5mg Tablet           5           mg             1   
    2  25,000 unit Premix Bag      25,000         UNIT             1   
    3            HEPARIN BASE         250           ml           250   
    4             20mg Tablet          20           mg             1   
    
      FORM_UNIT_DISP ROUTE  
    0            CAP    PO  
    1            TAB    PO  
    2            BAG    IV  
    3             ml    IV  
    4            TAB    PO  



```python
texts = []
j = 0
with open('./cleaned_data/indv_level_NotEvent.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        if j == 0:
            colnames = row
        texts += [row]
        j += 1
        if j > 100:
            break

indv_level_NotEvent = pd.DataFrame(texts)
indv_level_NotEvent.columns = colnames
```


```python
print('list of variables in the physician notes table')
print(list(indv_level_NotEvent))
```

    list of variables in the physician notes table
    ['SUBJECT_ID', 'HADM_ID', 'TEXT']



```python
print('First two rows of the physician notes table')
"""
The texts for each individual (and ICU stay) is in an excel cell which makes it hard to see the whole text.
Here only part of the first row can be seen...
"""
print(indv_level_NotEvent.loc[1:3, :])
```

    First two rows of the physician notes table
      SUBJECT_ID HADM_ID  \
    1      22532  167853   
    2      13702  107527   
    3      13702  167118   
    
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  TEXT  
    1                                                                                                                                                                                                                                                                                                   addendum:  radiologic studies: radiologic studies also included a chest ct  which confirmed cavitary lesions in the left lung apex consistent with infectious process/tuberculosis. this also moderate-sized left pleural effusion.  head ct: head ct showed no intracranial hemorrhage or mass effect  but old infarction consistent with past medical history.  abdominal ct: abdominal ct showed lesions of t10 and sacrum most likely secondary to osteoporosis. these can be followed by repeat imaging as an outpatient.  
    2   micu and then to medicine  history of present illness: this is an 81-year-old female with a history of emphysema not on home o2  who presents with three days of shortness of breath thought by her primary care doctor to be a copd flare. two days prior to admission  she was started on a prednisone taper and one day prior to admission she required oxygen at home in order to maintain oxygen saturation greater than 90%. she has also been on levofloxacin and nebulizers  and was not getting better  and presented to the emergency room.  in the emergency room  her oxygen saturation was 100% on cpap. she was not able to be weaned off of this despite nebulizer treatment and solu-medrol 125 mg iv x2.  review of systems is negative for the following: fevers  chills  nausea  vomiting  night sweats ...  
    3   cardiothoracic  allergies: amlodipine  attending: chief complaint: 81 yosmoker w/ copd  severe tbm  s/p tracheobronchoplasty s/p perc trach major surgical or invasive procedure: bronchoscopy 3/31 4/2 3     s/p trachealplasty percutaneous tracheostomy after failed extubation down size trach on to size 6 cuffless   history of present illness: this 81 year old woman has a history of copd. over the past five  years she has had progressive difficulties with her breathing. in  she was admitted to for respiratory failure due to a copd exacerbation. due to persistent hypoxemia  she required intubation and a eventual bronchoscopy on revealed marked  narrowing of the airways on expiration consistent with tracheomalacia. she subsequently underwent placement of two silicone stents  one in the lef...  

