# Market Basket Analysis: descoperirea tiparelor de cumpărare prin Apriori și FP-Growth

## Prezentare generală

Comportamentul de cumpărare poate fi analizat prin relațiile dintre produsele incluse în aceeași tranzacție. Acest proiect urmărește identificarea acestor relații prin **Apriori** și **FP-Growth**, precum și evaluarea utilității lor pentru decizii comerciale. Analiza coșului de cumpărături este integrată într-un flux mai amplu de Data Mining: explorarea și pregătirea datelor, clasificare, segmentare, detectarea anomaliilor, previziune, analiză textuală, grafuri și interpretabilitate.

Proiectul pornește de la o întrebare economică: **ce informații pot fi extrase din istoricul tranzacțiilor pentru a înțelege mai bine cumpărăturile și a fundamenta recomandări comerciale?** Obiectivul nu este doar obținerea unor scoruri sau reguli, ci interpretarea lor în context economic, cu verificarea limitelor metodologice.


## Motivație și problemă economică

O tranzacție oferă informații despre produse cumpărate împreună, însă relațiile recurente nu sunt întotdeauna vizibile prin statistici descriptive simple. Identificarea lor poate susține recomandări de produse complementare, planificarea ofertelor și analiza cererii. În același timp, frecvența unei asocieri nu demonstrează o relație cauzală sau eficiența unei promoții; interpretările trebuie raportate la prevalența produselor și la calitatea datelor.

**Obiectiv general:** construirea unui flux reproductibil de analiză a tranzacțiilor de retail, centrat pe reguli de asociere și completat cu metode predictive și descriptive.

**Obiective specifice:**

1. Explorarea, curățarea și transformarea datelor tranzacționale într-un format adecvat analizei.
2. Identificarea itemset-urilor frecvente și compararea algoritmilor Apriori și FP-Growth.
3. Evaluarea regulilor prin support, confidence, lift și măsuri complementare.
4. Segmentarea clienților sau tranzacțiilor și identificarea observațiilor atipice.
5. Compararea unor modele de clasificare și explicarea predicțiilor acestora.
6. Analiza evoluției temporale a vânzărilor și formularea de recomandări economice bazate pe rezultate.

## Întrebări de cercetare

- Ce produse apar frecvent în aceeași tranzacție?
- Care asocieri rămân relevante după luarea în calcul a frecvenței individuale a produselor?
- Ce diferențe există între Apriori și FP-Growth în privința rezultatelor și timpului de execuție?
- Pot fi identificate segmente distincte de comportament de cumpărare?
- Ce variabile sunt utile pentru o sarcină de clasificare definită fără scurgere de informație (*data leakage*)?
- Există variații temporale sau observații atipice cu semnificație comercială?
- Cum se traduc rezultatele analitice în recomandări verificabile pentru un comerciant?

## Date utilizate

**Sursă propusă:** [Online Retail — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail), DOI: [10.24432/C5BW33](https://doi.org/10.24432/C5BW33).

Setul conține **541.909 înregistrări de tip linie de factură**, pentru tranzacții desfășurate între **1 decembrie 2010 și 9 decembrie 2011** la un comerciant online din Regatul Unit. Printre câmpuri se află `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID` și `Country`. `InvoiceNo` poate indica și anulări; acestea trebuie tratate explicit în preprocesare. Datele sunt istorice și provin de la un singur comerciant, deci concluziile nu trebuie generalizate automat la întregul sector retail.

Datele brute se păstrează separat de cele procesate. Pentru componentele NLP se poate utiliza un **set auxiliar de texte comerciale, documentat și utilizat legal**, deoarece descrierile scurte de produse nu oferă în mod necesar etichete pentru analiza sentimentului. Alegerea finală a seturilor auxiliare se documentează în raport.

## Metodologie

Proiectul urmărește **KDD** (Selection → Preprocessing → Transformation → Data Mining → Interpretation/Evaluation) și ciclul **CRISP-DM** (Business Understanding → Data Understanding → Data Preparation → Modeling → Evaluation → Deployment). Rezultatele fiecărei etape sunt transmise etapelor următoare, iar deciziile pot fi revizuite dacă evaluarea indică probleme.

| Componentă | Metode / verificări planificate | Rezultat urmărit |
| --- | --- | --- |
| Înțelegerea datelor | statistici descriptive, valori lipsă, duplicate, distribuții, corelații, minimum 5 grafice EDA | profilul datelor și observații economice |
| Preprocesare | strategii pentru valori lipsă, IQR / alte metode pentru outlieri, codificare, scalare, PCA | date documentate și transformate |
| Clasificare | ID3, C4.5, CART sau aproximări justificate; minimum 3 modele suplimentare, optimizare pentru 2 | comparație prin metrici și grafice de evaluare |
| Interpretabilitate | minimum 2 metode XAI, inclusiv interpretare globală și locală | explicația predicțiilor |
| Reguli de asociere | Apriori, FP-Growth; support, confidence, lift; conviction, leverage, Jaccard/cosine | minimum 5 reguli interpretate, dintre care 3 evaluate suplimentar |
| Clustering | k-means, k-medoids, ierarhic, DBSCAN; Elbow, Silhouette, Davies-Bouldin, Calinski-Harabasz | segmente și profiluri economice |
| Anomalii | minimum 2 metode, de exemplu IQR și Isolation Forest | proporție, caracteristici și semnificație economică |
| Serii de timp | staționaritate, sezonalitate, ARIMA/SARIMA sau smoothing vs. model ML cu lag-uri | prognoze evaluate prin MAE, RMSE, MAPE și validare temporală |
| NLP | tokenizare, stopwords, lematizare/stemming, TF-IDF, model de clasificare sau sentiment | interpretarea textelor comerciale |
| Graf economic | rețea produse–produse; minimum 2 măsuri de centralitate | relații și produse centrale |
| Scalabilitate | schemă Hadoop/MapReduce–Spark–MLlib și exemplu/pseudocod | argumentarea procesării distribuite |
| Etică și integrare | GDPR, bias, fairness, sinteză și minimum 5 recomandări susținute de rezultate | decizii economice și limite explicite |

### Analiza regulilor de asociere

Tranzacțiile sunt convertite într-o matrice binară **tranzacție × produs**. Apriori și FP-Growth vor fi rulate pe aceeași selecție de date și cu praguri comparabile. Regulile de forma `A → B` sunt analizate prin:

- **Support:** proporția tranzacțiilor care conțin simultan A și B.
- **Confidence:** proporția tranzacțiilor care conțin B dintre cele care conțin A.
- **Lift:** raportul dintre confidence și frecvența lui B; o valoare peste 1 indică o asociere pozitivă față de independență.
- **Conviction, leverage și Jaccard/cosine:** măsuri suplimentare pentru verificarea robusteții interpretării.

Se vor prezenta cel puțin cinci reguli relevante și o comparație între algoritmi privind itemset-urile obținute, regulile și timpul de execuție. Pragurile și filtrările vor fi motivate, nu alese doar pentru a produce reguli spectaculoase.

### Validare și interpretare

Pentru clasificare vor fi utilizate separări train/test, validare încrucișată și metrici adecvate distribuției claselor (inclusiv matrice de confuzie, ROC și Precision–Recall). Pentru prognoze se va păstra ordinea temporală. Pentru clustering se vor compara indicatorii de calitate, iar pentru toate componentele se vor discuta posibile erori, dezechilibre, supraînvățare și limite ale generalizării.

## Structura repository-ului

```text
market-basket-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/                 # date originale
│   ├── processed/           # date curățate și transformate
│   └── external/            # eventuale date auxiliare (NLP)
├── notebooks/
│   ├── 01_KDD_EDA.ipynb
│   ├── 02_Preprocessing_PCA.ipynb
│   ├── 03_Decision_Trees.ipynb
│   ├── 04_Advanced_Models.ipynb
│   ├── 05_Association_Rules.ipynb
│   ├── 06_Clustering.ipynb
│   ├── 07_Anomaly_Detection.ipynb
│   ├── 08_Time_Series.ipynb
│   ├── 09_NLP.ipynb
│   ├── 10_Product_Graph.ipynb
│   ├── 11_XAI.ipynb
│   └── 12_Big_Data_Spark.ipynb
├── src/
│   └── functions.py        # funcții reutilizabile
├── results/                # tabele și metrici
├── figures/                # vizualizări
├── report/                 # raportul final PDF
└── presentation/           # prezentarea proiectului
```

Structura reprezintă organizarea **planificată** a proiectului; existența unui notebook nu implică automat finalizarea implementării.

## Instalare și rulare

Este recomandat un mediu virtual Python. După descărcarea repository-ului:

```bash
python -m venv .venv
# Linux/macOS:
source .venv/bin/activate
# Windows PowerShell:
# .venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter lab
```

1. Descărcați datele din sursa UCI și plasați-le în `data/raw/`, conform numelui de fișier folosit în notebook-uri.
2. Executați notebook-urile în ordinea numerotării; etapele care folosesc date procesate trebuie rulate după preprocesare.
3. Verificați rezultatele salvate în `results/` și graficele din `figures/`.
4. Pentru reproducibilitate, utilizați un `RANDOM_STATE` comun, căi relative și versiuni de biblioteci înregistrate în `requirements.txt`.

**Notă:** instrucțiunile de rulare trebuie verificate și actualizate după implementarea efectivă a notebook-urilor; repository-ul inițial nu este prezentat drept aplicație deja funcțională.

## Rezultate și livrabile

După implementare, această secțiune va include tabele comparative pentru modele și algoritmi, vizualizările cerute, matricea de sinteză a rezultatelor și minimum cinci recomandări economice susținute de observații empirice. Livrabilele proiectului includ raport PDF, cod sursă, date redistribuibile conform condițiilor sursei, README, prezentare și fișe de contribuție individuală (acestea din urmă pot fi păstrate în documentația de predare, fără publicarea datelor personale).

## Limitări și utilizare responsabilă

Asocierile statistice nu demonstrează cauzalitate. Rezultatele pot fi influențate de sezonalitate, produse rare, anulări, înregistrări incomplete și particularitățile comerciantului. Analizele la nivel de client trebuie să respecte principiile minimizării datelor și protecției identificatorilor. Evaluarea bias-ului și a explicabilității va fi raportată la datele și modelele efectiv utilizate.

## Referințe

1. Chen, D. (2015). *Online Retail*. UCI Machine Learning Repository. DOI: [10.24432/C5BW33](https://doi.org/10.24432/C5BW33).
2. Chen, D., Sain, S. L., & Guo, K. (2012). *Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining*. Journal of Database Marketing & Customer Strategy Management, 19, 197–208.
3. Han, J., Kamber, M., & Pei, J. *Data Mining: Concepts and Techniques*.
4. [mlxtend — Association Rules](https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/association_rules/).
5. [scikit-learn — Decision Trees](https://scikit-learn.org/stable/modules/tree.html).
6. Materialele și enunțul proiectului de la disciplina Data Mining.
