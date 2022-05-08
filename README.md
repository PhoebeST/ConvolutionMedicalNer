# UIUC CS598 DLH: DeepLearning for Healthcare Project
## Citation

*Bardak, B. and Tan, M., 2021. Improving clinical outcome predictions using convolution over medical entities with multimodal learning. Artificial Intelligence in Medicine, 117, p.102112.*

##  The original paper’s repo link

<https://github.com/tanlab/ConvolutionMedicalNer>

## Dependencies

The `requirements.txt` file should list all Python libraries that your notebooks  depend on, and they will be installed using:
```
pip install -r requirements.txt
```
## Data download instruction
1. Clone the code to local.   
```
https://github.com/tanlab/ConvolutionMedicalNer.git
cd ConvolutionMedicalNer
```

2. Run MIMIC-Extract Pipeline as explained in https://github.com/MLforHealth/MIMIC_Extract.   

3. Copy the output file of MIMIC-Extract Pipeline named `all_hourly_data.h5` to `data` folder.

## Usage


1. Run `01-Extract-Timseries-Features.ipnyb` to extract first 24 hours timeseries features from MIMIC-Extract raw data.

2. Copy the `ADMISSIONS.csv`, `NOTEEVENTS.csv`, `ICUSTAYS.csv` files into `data` folder.

3. Run `02-Select-SubClinicalNotes.ipynb` to select subnotes based on criteria from all MIMIC-III Notes.

4. Run `03-Prprocess-Clinical-Notes.ipnyb` to prepocessing notes.

5. Run `04-Apply-med7-on-Clinical-Notes.ipynb` to extract medical entities. 

6. Download pretrained embeddings into `embeddings` folder via link in given References section.

7. Run `05-Represent-Entities-With-Different-Embeddings.ipynb` to convert medical entities into word representations.

8. Run `06-Create-Timeseries-Data.ipynb` to prepare the timeseries data to fed through GRU / LSTM.

9. Run `07-Timeseries-Baseline.ipynb` to run timeseries baseline model to predict 4 different clinical tasks.

10. Run `08-Multimodal-Baseline.ipynb` to run multimodal baseline to predict 4 different clinical tasks.

10. Run `09-Proposed-Model.ipynb` to run proposed model to predict 4 different clinical tasks.

## Results

### Performance of baseline models from reproduced model


| Hospital Mortality ｜ 87.88 ｜ 56.84 ｜ 44.51 ｜
|  ----  | ----  | ----  | ----  | ----  |
｜ICU-Mortality｜88.92｜52.09｜43.58｜
｜LOS > 3 Days｜69.60｜63.90｜55.59｜
｜LOS > 7 Days｜73.47｜21.28｜5.75｜

### Performance of FastText Multimodal from reproduced model


｜Hospital Mortality｜87.91｜58.37｜45.83｜
｜ICU-Mortality ｜89.13｜53.04｜45.31｜
｜LOS > 3 Days ｜70.62｜64.84｜57.12｜
｜LOS > 7 Days｜72.69｜21.95｜2.19｜

###  Performance of Word2Vec Multimodal from reproduced model


｜Hospital Mortality ｜88.0｜58.73｜48.42｜
｜ICU-Mortality ｜89.17｜52.12｜45.00｜
｜LOS $>$ 3 Days ｜69.60｜63.90｜55.59｜
｜LOS $>$ 7 Days｜73.6｜22.80｜3.8｜

## References

Download the MIMIC-III dataset via https://mimic.physionet.org/

MIMIC-Extract implementation: https://github.com/MLforHealth/MIMIC_Extract

med7 implementation: https://github.com/kormilitzin/med7

Download Pre-trained Word2Vec & FastText embeddings: https://github.com/kexinhuang12345/clinicalBERT

Preprocessing Script: https://github.com/kaggarwal/ClinicalNotesICU

