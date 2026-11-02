# Requirement notes

## 01_dataset_sanity_check.ipynb
1. I take **acuity** column from **triage.csv** as ESI mapping.   
    High = ESI 1–2 
    Medium = ESI 3
    Low = ESI 4–5


## 02_preprocess_and_explain.ipynb
1. I did normalization that making the short form in column **chiefcomplaint** to complete form based on the internet info. And also remove unnecessary symbol.

2. Build the first pipeline (nlp):
    a) I created a list of **keywords** to define the symptom based on the information/common knowledge.

3. I **config the negation explicitly** to make sure the negex working
    a) I added negex to nlp pipeline

4. Build second pipeline (nlp_umls), UMLS Linking:
    a) Using **scispacy_linker** to build the UMLS linking
    b) Add the self-config negation inside nlp_umls
    c) Create linker

5. Extract evidence from pipelines
    **"concept": <keyword or matched phrase in lowercase>,**
    **"negated": bool,**
    **"span_text": <surface form>,**
    **"char_start": int,**
    **"char_end": int**
    a) Extract evidence from nlp pipeline
    b) Extract evidence from nlp_umls with linker

6. I create a **preprocess_single** function for testing only

7. I create **preprocess_dataframe** function for the whole processing including:
    *pipeline*
    *Extract evidence*
    *form dataframe*
    *change column name*
    *output*

8. Then I realize the preprocess takes so much time, I created a **preprocess_dataframe_fast** function including **batch** mode and **multiprocess**.

9. I group by the affirmed concepts and negated concepts to review the result for finetuning.

10. I also review the text from chiefcomplaint to see the normalization works.

11. Baseline model (rule-based)
    a) I define the symptom into high, mid, low based on the study on the original source of data file.
    b) Based on the rules I set, I predict the risk again based on the **affirmed_concepts**.

12. I evaluate the result to see the accuracy of the rule-base model. **Only tune the rule based on train set**
    a) The result is disappointed
        Train accuracy: 0.3880962489460812
        Test accuracy: 0.3902675293301601
        Test macro F1: 0.3761705192707234   

        There're two methods I can handle it to increase the accuracy.
        1. I can redefine the list based on the result
            e.g. ETOH	['ethanol']	Medium	Low -> put ethanol into MED list
        2. Build one more model to recover the accuracy.
    b) I also have to clean noisy concepts like
        post
        status
        abnormal
        laboratory test finding
        transfer - product ownership
        surgical transfer - action
