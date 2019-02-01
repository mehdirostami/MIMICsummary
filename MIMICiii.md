
The following tables are available data in the MIMIC iii database. The documentation page is copied below. 
Please quickly consult with this page if content of some of the tables of variables are not clear to you.
The list of tables is in the left. Click on the table and you will see the list of variables and their decription.
https://mimic.physionet.org/mimictables/inputevents_cv/


```python
import numpy as np
import pandas as pd
import csv
```

Here is the table which contains the input events (CareVue).


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

list of variable in the admissions table


```python
print(list(admissions_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ADMITTIME', 'DISCHTIME', 'DEATHTIME', 'ADMISSION_TYPE', 'ADMISSION_LOCATION', 'DISCHARGE_LOCATION', 'INSURANCE', 'LANGUAGE', 'RELIGION', 'MARITAL_STATUS', 'ETHNICITY', 'EDREGTIME', 'EDOUTTIME', 'DIAGNOSIS', 'HOSPITAL_EXPIRE_FLAG', 'HAS_CHARTEVENTS_DATA']


First five rows of the admissions table


```python
print(admissions_.loc[:4, :])
```

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


_____________________________________________________________________________________________

Here is the table which contains the input events (CareVue).


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

list of variables in the ICD procedure table


```python
print(list(df_data))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'SEQ_NUM', 'ICD9_CODE', 'values']


First five rows of the ICD procedure table


```python
print(df_data.loc[:4, :])
```

      ROW_ID SUBJECT_ID HADM_ID SEQ_NUM ICD9_CODE  values
    0    944      62641  154460       3      3404       1
    1    945       2592  130856       1      9671       1
    2    946       2592  130856       2      3893       1
    3    947      55357  119355       1      9672       1
    4    948      55357  119355       2      0331       1


___________________________________________________________________________________

Here is the table which contains the input events (CareVue).


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

list of variables in the ICD diagnosis table


```python
print(list(df_data))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'SEQ_NUM', 'ICD9_CODE', 'values']


First five rows of the ICD diagnosis table


```python
print(df_data.loc[:4, :])
```

      ROW_ID SUBJECT_ID HADM_ID SEQ_NUM ICD9_CODE  values
    0   1297        109  172335       1     40301       1
    1   1298        109  172335       2       486       1
    2   1299        109  172335       3     58281       1
    3   1300        109  172335       4      5855       1
    4   1301        109  172335       5      4254       1


____________________________________________________________________________________________

Here is the table which contains the input events (CareVue).


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

list of variables in the ICU stays table


```python
print(list(ICUstays_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'DBSOURCE', 'FIRST_CAREUNIT', 'LAST_CAREUNIT', 'FIRST_WARDID', 'LAST_WARDID', 'INTIME', 'OUTTIME', 'LOS']


First five rows of the ICU stays table


```python
print(ICUstays_.loc[:4, :])
```

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


______________________________________________________________________________________

Here is the table which contains the input events (CareVue).


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

list of variables in the input events (CareVue) table


```python
print(list(input_events_CareVue_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'CHARTTIME', 'ITEMID', 'AMOUNT', 'AMOUNTUOM', 'RATE', 'RATEUOM', 'STORETIME', 'CGID', 'ORDERID', 'LINKORDERID', 'STOPPED', 'NEWBOTTLE', 'ORIGINALAMOUNT', 'ORIGINALAMOUNTUOM', 'ORIGINALROUTE', 'ORIGINALRATE', 'ORIGINALRATEUOM', 'ORIGINALSITE']


First five rows of the input events (CareVue) table


```python
print(input_events_CareVue_.loc[:4, :])
```

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


___________________________________________________________________________________________________________

Here is the table which contains the input events.


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

list of variables in the input events (Metavision) table


```python
print(list(input_events_Metavision_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'STARTTIME', 'ENDTIME', 'ITEMID', 'AMOUNT', 'AMOUNTUOM', 'RATE', 'RATEUOM', 'STORETIME', 'CGID', 'ORDERID', 'LINKORDERID', 'ORDERCATEGORYNAME', 'SECONDARYORDERCATEGORYNAME', 'ORDERCOMPONENTTYPEDESCRIPTION', 'ORDERCATEGORYDESCRIPTION', 'PATIENTWEIGHT', 'TOTALAMOUNT', 'TOTALAMOUNTUOM', 'ISOPENBAG', 'CONTINUEINNEXTDEPT', 'CANCELREASON', 'STATUSDESCRIPTION', 'COMMENTS_EDITEDBY', 'COMMENTS_CANCELEDBY', 'COMMENTS_DATE', 'ORIGINALAMOUNT', 'ORIGINALRATE']


First five rows of the input events (Metavision) table


```python
print(input_events_Metavision_.loc[:4, :])
```

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


______________________________________________________________________________________________________

Here is the table which contains the transferring information.


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

list of variables in the output events table


```python
print(list(output_events_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'CHARTTIME', 'ITEMID', 'VALUE', 'VALUEUOM', 'STORETIME', 'CGID', 'STOPPED', 'NEWBOTTLE', 'ISERROR']


First five rows of the output events table


```python
print(output_events_.loc[:4, :])
```

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


______________________________________________________________________________________________________

Here is the table which contains the transferring information.


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

list of variables in the service table


```python
print(list(service_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'TRANSFERTIME', 'PREV_SERVICE', 'CURR_SERVICE']


First five rows of the service table


```python
print(service_.loc[:4, :])
```

      ROW_ID SUBJECT_ID HADM_ID         TRANSFERTIME PREV_SERVICE CURR_SERVICE
    0    758        471  135879  2122-07-22 14:07:27        TSURG          MED
    1    759        471  135879  2122-07-26 18:31:49          MED        TSURG
    2    760        472  173064  2172-09-28 19:22:15                      CMED
    3    761        473  129194  2201-01-09 20:16:45                        NB
    4    762        474  194246  2181-03-23 08:24:41                        NB


Here is the table which contains the priscriptions for the patients.


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

list of variables in the prescription table


```python
print(list(prescription_))
```

    ['ROW_ID', 'SUBJECT_ID', 'HADM_ID', 'ICUSTAY_ID', 'STARTDATE', 'ENDDATE', 'DRUG_TYPE', 'DRUG', 'DRUG_NAME_POE', 'DRUG_NAME_GENERIC', 'FORMULARY_DRUG_CD', 'GSN', 'NDC', 'PROD_STRENGTH', 'DOSE_VAL_RX', 'DOSE_UNIT_RX', 'FORM_VAL_DISP', 'FORM_UNIT_DISP', 'ROUTE']


First five rows of the prescription table


```python
print(prescription_.loc[:4, :])
```

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


------------------------------------------------------------------------------------------

Here is the table which contains the physician summary notes on the patients.


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

list of variables in the physician notes table


```python
print(list(indv_level_NotEvent))
```

    ['SUBJECT_ID', 'HADM_ID', 'TEXT']



The texts for each individual (and ICU stay) is in an excel cell which makes it hard to see the whole text.
Here only part of the first row can be seen...


First two rows of the physician notes table


```python
print(indv_level_NotEvent.loc[1:3, :])
```

      SUBJECT_ID HADM_ID                                               TEXT
    1      22532  167853   addendum:  radiologic studies: radiologic stu...
    2      13702  107527   micu and then to medicine  history of present...
    3      13702  167118   cardiothoracic  allergies: amlodipine  attend...


The text for the first patients:


```python
print(indv_level_NotEvent.loc[1, "TEXT"])
```

     addendum:  radiologic studies: radiologic studies also included a chest ct  which confirmed cavitary lesions in the left lung apex consistent with infectious process/tuberculosis. this also moderate-sized left pleural effusion.  head ct: head ct showed no intracranial hemorrhage or mass effect  but old infarction consistent with past medical history.  abdominal ct: abdominal ct showed lesions of t10 and sacrum most likely secondary to osteoporosis. these can be followed by repeat imaging as an outpatient.


The text for the second patients:


```python
print(indv_level_NotEvent.loc[2, "TEXT"])
```

     micu and then to medicine  history of present illness: this is an 81-year-old female with a history of emphysema not on home o2  who presents with three days of shortness of breath thought by her primary care doctor to be a copd flare. two days prior to admission  she was started on a prednisone taper and one day prior to admission she required oxygen at home in order to maintain oxygen saturation greater than 90%. she has also been on levofloxacin and nebulizers  and was not getting better  and presented to the emergency room.  in the emergency room  her oxygen saturation was 100% on cpap. she was not able to be weaned off of this despite nebulizer treatment and solu-medrol 125 mg iv x2.  review of systems is negative for the following: fevers  chills  nausea  vomiting  night sweats  change in weight  gastrointestinal complaints  neurologic changes  rashes  palpitations  orthopnea. is positive for the following: chest pressure occasionally with shortness of breath with exertion  some shortness of breath that is positionally related  but is improved with nebulizer treatment.  past medical history: 1. copd. last pulmonary function tests in demonstrated a fvc of 52% of predicted  a fev1 of 54% of predicted  a mmf of 23% of predicted  and a fev1:fvc ratio of 67% of predicted  that does not improve with bronchodilator treatment. the fvc  however  does significantly improve with bronchodilator treatment consistent with her known reversible air flow obstruction in addition to an underlying restrictive ventilatory defect. the patient has never been on home oxygen prior to this recent episode. she has never been on steroid taper or been intubated in the past. 2. lacunar cva. mri of the head in demonstrates  mild degree of multiple small foci of high t2 signal within the white matter of both cerebral hemispheres as well as the pons  in the latter region predominantly to the right of midline. the abnormalities  while nonspecific in etiology  are most likely secondary to chronic microvascular infarction. there is no mass  lesion  shift of the normal midline strictures or hydrocephalus. the major vascular flow patterns are preserved. there is moderate right maxillary  moderate bilateral ethmoid  mild left maxillary  minimal right sphenoid  and frontal sinus mucosal thickening. these abnormalities could represent an allergic or some other type of inflammatory process. additionally noted is a moderately enlarged subtotally empty sella turcica . 3. angina: most recent stress test was in going for four minutes with a rate pressure product of 10 000  64% of maximum predicted heart rate without evidence of ischemic ekg changes or symptoms. the imaging portion of the study demonstrated no evidence of myocardial ischemia and a calculated ejection fraction of 84%. the patient denies angina at rest and gets angina with walking a few blocks. are alleviated by sublingual nitroglycerin. 4. hypothyroidism on synthroid. 5. depression on lexapro. 6. motor vehicle accident with head injury approximately 10 years ago.  medications on admission: 1. hydrochlorothiazide 25 q.d. 2. prednisone 60 mg  50 mg  40 mg  20 mg. 3. levofloxacin 500 mg q.d. 4. imdur 60 mg q.d. 5. synthroid 75 mcg q.d. 6. pulmicort nebulizer b.i.d. 7. albuterol nebulizer q.4. prn. 8. lexapro 10 mg q.d. 9. protonix 40 mg q.d. 10. aspirin 81 mg q.d.  allergies: norvasc leads to lightheadedness and headache.  family history: noncontributory.  social history: lives with her husband  dr. an eminent pediatric neurologist at . the patient is a prior smoker  but has not smoked in over 10 years. she has no known alcohol use and she is a full code.  physical exam at time of admission: blood pressure 142/76  heart rate 100 and regular  respirations at 17-21  and 97% axillary temperature. she was saturating at 100% on cpap with dry mucous membranes. an elderly female in no apparent distress. pupils are equal  round  and reactive to light and accommodation. extraocular movements are intact. oropharynx difficult to assess due to cpap machine. no evidence of jugular venous pressure  however  the strap from the cpap machine obscures the neck exam. cranial nerves ii through xii are grossly intact. neck is supple without lymphadenopathy. heart exam: tachycardic  regular  obscured by loud bilateral wheezing with increase in the expiratory phase as well as profuse scattered rhonchi throughout the lung fields. positive bowel sounds  soft  nontender  nondistended  obese  no masses. mild edema of the lower extremities without clubbing or cyanosis  no rashes. there is a right hand hematoma. strength is assessed as in the lower extremities  in the upper extremities with a normal mental status and cognition.  laboratory studies: white count 19  hematocrit 41  platelets 300. chem-7: 127  3.6  88  29  17  0.6  143. troponin was negative. cks were negative times three. initial blood gas showed a ph of 7.4  po2 of 66  pco2 of 54.  chest x-ray demonstrates a moderate sized hiatal hernia  segmental atelectasis  left lower lobe infiltrate versus segmental atelectasis.  ekg shows normal sinus rhythm at 113 beats per minute  normal axis  no evidence of st-t wave changes.  brief summary of hospital course: 1. copd/dyspnea/pneumonia: the patient was initially placed on an aggressive steroid taper and admitted to the medical intensive care unit due to her difficulty with oxygenation despite cpap machine. she was also given nebulizer treatments q.4h. as well as chest pt. the nebulizers were increased to q.1h. due to the fact that she continued to have labored breathing.  due to persistent respiratory failure and labored breathing  the patient was intubated on in order to improve oxygenation  ventilation  and ability to suction. a bronchoscopy was performed on   which demonstrated marked narrowing of the airways with expiration consistent with tracheomalacia.  on   two silicone stents were placed  one in the left main stem 12 x 25 and one in the trachea 16 x 40 by dr.  under rigid bronchoscopy with general anesthesia.  on   the patient was extubated to a cool mist shovel mask and her oxygen was titrated down to 2 liters nasal cannula at which time she was transferred to the medical floor. on the medical floor  the steroids were weaned to off on   and the patient was saturating at 97% on 2 liters  92% on room air.  on   the patient was seen again by the interventional pulmonology service  who agreed that she looked much improved and recommended that she go to pulmonary rehabilitation with followup within six weeks' time status post placement of stents in respiratory failure.  2. cardiovascular: the patient was ruled out for a mi. she did have another episode on the medical floor of chest pain  which showed no evidence of ekg changes and negative troponin  negative cks x3. she was continued on aspirin  imdur  and diltiazem for rate control per her outpatient regimen.  3. hypertension: she was maintained on diltiazem and hydrochlorothiazide with adequate blood pressure control and normalization of electrolytes.  4. hematuria: the patient had intermittent hematuria likely secondary to foley placement. the foley catheter was discontinued on . she had serial urinalyses  which were all negative for signs of infection.  5. hyperglycemia: patient was placed on insulin-sliding scale due to hyperglycemia  which was steroid induced. this worked quite well and her glucose came back to normal levels once the steroids were tapered to off.  6. leukocytosis: patient did have a profound leukocytosis of 20 to 22 during much of her hospital course. as the steroids were tapered to off  her white blood cell count on was 15 000. it was felt that the leukocytosis was secondary to both steroids as well as question of a left lower lobe pneumonia.  7. for the left lower lobe pneumonia  the patient had initially received a course of levofloxacin 500 p.o. q.d. from to . this was restarted on for an additional seven day course given the fact that she still had the leukocytosis and still had marked rales at the left lower lobe.  8. hypothyroidism: the patient was continued on outpatient medical regimen.  9. depression: the patient was continued on lexapro per outpatient regimen. it is recommended that she follow up with a therapist as an outpatient due to the fact that she did have a blunted affect throughout much of the hospital course  and did appear clinically to be depressed.  10. prophylaxis: she was maintained on proton-pump inhibitor with subq heparin.  11. sore throat: the patient did have a sore throat for much of the hospital course post extubation. this was treated with cepacol lozenges as well as kbl liquid a solution containing kaopectate  bismuth  and lidocaine at bedtime.  12. communication/code status: the patient was full code throughout her hospital course  and communication was maintained with the patient and her husband.  13. muscle weakness: the patient did have profound muscle weakness and was evaluated by physical therapy  and was found to have impaired functional mobility  impaired musculoskeletal performance  impaired gas exchange  impaired endurance  impaired ventilation  and needed help with supine to sit. however  she was able to tolerate sitting in a chair for approximately one hour.  on motor exam  her flexors and extensors of the lower extremities were at the knee  at the ankle  at the elbows  and hips. it was felt that this weakness was most likely due to a combination of steroid myopathy as well as muscle atrophy secondary to deconditioning after a prolonged hospital course.  14. speech/swallow: the patient had a speech and swallow evaluation showing no evidence of dysphagia  no evidence of vocal cord damage status post tracheal stent placement.  discharge condition: the patient was able to oxygenate on room air at 93% at the time of discharge. she was profoundly weak  but was no longer tachycardic and had a normal blood pressure. her respirations were much improved albeit with transmitted upper airway sounds.  discharge status: the patient will be discharged to for both pulmonary and physical rehabilitation.  discharge medications: 1. levothyroxine 75 mcg p.o. q.d. 2. citalopram 10 mg p.o. q.d. 3. aspirin 81 mg p.o. q.d. 4. fluticasone 110 mcg two puffs inhaled b.i.d. 5. salmeterol diskus one inhalation b.i.d. 6. acetaminophen 325-650 mg p.o. q.4-6h. prn. 7. ipratropium bromide mdi two puffs inhaled q.2h. prn. 8. albuterol 1-2 puffs inhaled q.2h. prn. 9. zolpidem tartrate 5 mg p.o. q.h.s. prn. 10. isosorbide dinitrate 10 mg p.o. t.i.d. 11. diltiazem 60 mg p.o. q.i.d. 12. pantoprazole 40 mg p.o. q.24h. 13. trazodone 25 mg p.o. q.h.s. prn. 14. subq heparin 5000 units subcutaneous b.i.d. until such time that the patient is able to get out of bed twice a day. 15. cepacol lozenges q.2h. prn. 16. levofloxacin 500 mg p.o. q.d. for a seven day course to be completed on . 17. kaopectate/benadryl/lidocaine 5 ml p.o. b.i.d. prn  not to be given around mealtimes for concern of dysphagia induced by lidocaine. 18. lorazepam 0.5-2 mg iv q.6h. prn.  follow-up plans: the patient is recommended to followup with dr.   within two weeks of leaving of the hospital. she is also recommended to followup with the interventional pulmonary service for followup status post stent placement. she is also recommended to followup with a neurologist if her muscle weakness does not improve within one week on physical therapy with concern for steroid-induced myopathy.  final diagnoses: 1. tracheomalacia status post tracheal and left main stem bronchial stent placement. 2. hypertension. 3. hypothyroidism. 4. restrictive lung defect. 5. depression.    dr.  12-207   dictated by: medquist36  d: 11:30 t: 11:33 job#: 

