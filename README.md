![unsw_0](https://user-images.githubusercontent.com/7439960/197022279-cfdf58ea-01ca-4c1e-854e-99776012a0bd.png) 
# IoT CVE Dataset


**Authors**  
  Carlos A. Rivera A.(1), Arash Shaghaghi1(1), Gustavo Batista(1), David D. Nguyen(1), and Salil S. Kanhere(1)  
   1. The University of New South Wales (UNSW) Sydney Australia.  
  
  
**Abstract**  
In our IoT-based research projects, we have developed and implemented three different machine-learning architectures with the sole purpose of helping the ITC administrator of any enterprise to manage (install, grand or deny access, and remove) IoT devices. Our approach utilises the cybersecurity characteristics of the devices as a pinpoint to carry-out different analyses and predictions. The output of this project is two-fold. First, the resolution of whether grant or deny access to the requested device and Second, a set of recommended remediation actions that the ITC administrators must follow if they want to implement the analysed IoT device. When fully enforced, these remediation actions will give the organisation's stockholders the certainty that all the installed IoT devices have been subject to rigorous security analyses.


**Keywords**  
IoT CyberSecurity Prediction | National Vulnerability Database (NVD) | Common Vulnerabilities Enumeration (CVE) | Common Weaknesses Enumeration (CWE) | IoT security | Machine learning


**The Datasets**  
We aim to analyse text and, through ML models, predict the weakness(es) for any IoT device. We define hence the necesity of a dataset with mostly text as its content, and divided into two parts. The first, a text sequence (the input) and the classes to predict (the output). The output would contain a finite list of weaknesses(CWEs). 
Searching for possible sources, we used the dataset from [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7) and added technical information (from Zoomeye) to form our dataset-0 (Table-1). Analysing this dataset, we found two problems; First, the information is organised in features rather than just text; Secondly, the classes predicted are risk labels(Low, Medium, High, Critical). 

We solved these problems by conducting the following activities:
- Utilise the features that provide mainly textual information (the numeric-bsaed features do not provide information when used as part of a larger text) and putting them together. 
- Since the records are matched to the vulnerability codes that the NVD generates, we used a program to query the CVE code and obtained the text of each record's weakness(es). 
- To complement the information of each device, we extracted five technical features through the ZoomEye search engine and pasted added to the corresponding text of each record of the dataset. 
- We searched the NVD for only the CVEs in the IoT devices DB, obtained the corresponding vulnerability description, and used it as a new record. We extracted the weakness(es) of the CVE and added it to the DS. 


**Table 1. Dataset-0 features.**

Description of features of dataset from [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7)(SRC-1), ZoomEye (RC-2) and The NVD (SRC-3)
|Source |Feature Name |Data Type |Unique Values|Details|
| --- | --- | --- | --- | --- |
|SRC-1  |Brand        |Categorical|            129     |Name of the device reported on the CVE.\\
|SRC-1  |Product Type |Categorical|             71     |Phrase describing the product.\\
|SRC-1  |Category     |Categorical|              5     |SmartHome, Medical, Wearable, Telecomm, and Other.\\
|SRC-2  |Model        |Categorical|            Infinite |Product model identifier.\\
|SRC-2  |Operating System|    Categorical|     Infinite |Operating System name identifier.\\
|SRC-2  |Operating System Version|Categorical| Infinite |Operating System version identifier.\\
|SRC-2  |Ports       |Categorical|             65535    |Numeric identifier of the port(s) detected open.\\
|SRC-2  |Services    |Categorical|             [Infinite](https://www.rfc-editor.org/rfc/rfc6335) |Name of service associated to each open port.\\
|SRC-3  |Vulnerability Description|Categorical|Infinite |Text of each vulnerability description.\\
|SRC-3  |Weakness Description|Categorical     |926       |Text of each weakness description.\\
|SRC-3  |Weakness ID   |Categorical           |926       |Identifier code assigned to each weakness. E.g. CWE-001\\ 



The outcome of converting the structured dataset-0 into text-based yielded the Only-IoT dataset, in figure 1 we show an extract of two records from the same device but generated from two different sources. 


**Figure 1. Extract of records from the Only-IoT Dataset. **

![CWE_DS_Combined](https://user-images.githubusercontent.com/7439960/197088114-8f28bc4b-92f3-435a-a7be-819f75d2a1f2.png)


The first record shows an example obtained from the NVD (the CVE description text as the source and the associated CWEs as the target (classes to predict). The second record shows an example of text (from string-based features) extracted from the structured dataset (Table 1).  


The Only-IoT dataset contains information related to IoT devices, hence, we branded this dataset as "Only-IoT Dataset". 
Furthermore, in an effort to have a bigger dataset and since the NVD contains thousand of records with text, we used the text associated to each vulnerability as source and the linked CWEs as target. This dataset contains information about many systems, not just IoT; therefore, we named it "the All-Systems Dataset". In Table 2, we disclose the number of records each DS contains; And, in Table 3, we provide the statistic of each dataset.


**Table 2. Datasets and their respective record counts.**

|Dataset| Records | 
| --- | --- | 
|Only-IoT DS      |4,892        |
|All-Systems DS   |75,559        |


**Table 3. Datasets Statistics. "AS" represents All-Systems DS and "OI" represents Only-IoT DS.**

|Dataset| Median | Min| Max | Classes|
| --- | --- | --- | --- | --- |
|IO DS |21.5    | 2| 19,273 | 46 |
|AS DS |123.5   |19|  1,110 | 43 |



**Notes:**

-	To create the datasets, we used information from the NVD, however, we found numerous records to contain poor or no details related to weaknesses. Thus, the resulting datasets, contain records that we could match with current weaknesses.  
-	The Only-IoT dataset contains records that relate to vulnerabilities reported in most of the known IoT devices' brands. Furthermore, in our analysis of the information we did not consider devices from brands such as Apple or Google. The All-systems has not limitations, hence, it contains these two brands' devices.


  
**Datasets inquiries**
Please submit any inquiry related to the datasets to:
- [Carlos Rivera UNSW email](mailto:c.riveraalvarez@unsw.edu.au)/[Carlos Rivera Personal email](mailto:alberto.az.au@gmail.com)
- [Dr Arash Shaghaghi - UNSW](mailto:a.shaghaghi@unsw.edu.au), 
- [Professor Salil Kanhere - UNSW](mailto:salil.kanhere@unsw.edu.au)
