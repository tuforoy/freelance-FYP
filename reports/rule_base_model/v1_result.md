## The result is not good enough ##
1. Adjust rule list



Train accuracy: 0.3880962489460812
Test accuracy: 0.3902675293301601
Test macro F1: 0.3761705192707234

Classification report:
              precision    recall  f1-score   support

         Low       0.11      0.83      0.20      5920
      Medium       0.70      0.37      0.49     45012
        High       0.64      0.33      0.44     32685

    accuracy                           0.39     83617
   macro avg       0.49      0.51      0.38     83617
weighted avg       0.64      0.39      0.45     83617


Confusion matrix:
[[ 4890   952    78]
 [22058 16796  6158]
 [15644  6094 10947]]




HIGH = {
    "chest pain",
    "dyspnea",
    "shortness of breath",
    "syncope",
    "seizure",
    "overdose",
    "bleeding",
    "hematemesis",
    "hematuria",
    "altered mental status",
    "numbness",
    "weakness",
    "stroke",
    "suicidal",
    "respiratory distress",
    "loss of consciousness",
    "anaphylaxis",
    "trauma",
    "mvc",
    "fall",
    "fracture",
}

MED = {
    "abdominal pain",
    "fever",
    "vomiting",
    "nausea",
    "dizziness",
    "headache",
    "palpitations",
    "dysuria",
    "diarrhea",
    "cough",
    "neck pain",
    "back pain",
    "urinary tract infection",
    "burn",
    "rash",
    "wound",
    "pain",
    "pregnancy",
    "pregnant",
    "depression",
    "allergic reaction",
    "altered mental status",
    "lethargy",
    "weakness",
    "unsteady gait",
}

LOW = {
    "suture removal",
    "med refill",
    "wound check",
    "ear pain",
    "eye irritation",
    "constipation",
    "routine",
}