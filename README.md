# market basket analysis – descoperirea tiparelor de cumpărare prin Apriori și FP-Growth

## despre proiect

În acest proiect analizăm comportamentul de cumpărare al clienților unui magazin online, pornind de la date tranzacționale reale.

Ne interesează în special produsele cumpărate împreună și modul în care aceste relații pot fi folosite pentru a înțelege mai bine obiceiurile de cumpărare.

Pentru identificarea tiparelor frecvente utilizăm algoritmii Apriori și FP-Growth, iar regulile de asociere obținute sunt analizate din perspectivă economică.

Proiectul face parte dintr-o analiză mai amplă de Data Mining, care include explorarea și pregătirea datelor, clasificare, clustering, detectarea anomaliilor, serii de timp, analiza textului și a grafurilor.

Ne propunem să folosim aceste metode într-un proces comun, astfel încât rezultatele să contribuie la înțelegerea aceleiași probleme economice.

## motivația alegerii temei

Am ales această temă deoarece datele despre cumpărături pot oferi informații care nu sunt evidente atunci când analizăm fiecare produs separat.

De exemplu, două produse pot avea vânzări individuale moderate, dar pot apărea frecvent în aceeași comandă. Identificarea unor astfel de relații poate fi utilă pentru recomandarea produselor complementare, organizarea ofertelor sau analiza preferințelor clienților.

Analiza coșului de cumpărături reprezintă o aplicație cunoscută a regulilor de asociere. Algoritmul Apriori, prezentat de Agrawal și Srikant (1994), și algoritmul FP-Growth, propus de Han, Pei și Yin (2000), urmăresc identificarea seturilor frecvente, dar folosesc abordări diferite.

Am considerat interesant să comparăm aceste metode pe același set de date, pentru a observa dacă obținem aceleași combinații de produse și cum diferă timpul necesar procesării.

Tema ne permite să aplicăm metodele studiate la Data Mining într-un context economic concret și să înțelegem cum pot fi transformate rezultatele unei analize în recomandări comerciale.

## problema economică și obiectivele

Problema de la care pornim este identificarea relațiilor dintre produsele cumpărate în cadrul aceleiași tranzacții.

Scopul principal este să descoperim tipare de cumpărare și să analizăm în ce măsură acestea pot susține decizii comerciale.

Pentru aceasta, ne propunem:

- să explorăm și să pregătim datele tranzacționale;
- să identificăm produsele și combinațiile cumpărate frecvent;
- să aplicăm Apriori și FP-Growth și să comparăm rezultatele;
- să evaluăm regulile de asociere prin support, confidence și lift;
- să analizăm comportamentul de cumpărare și prin alte metode de Data Mining;
- să interpretăm rezultatele și să formulăm recomandări economice.

## întrebări de cercetare

Pe parcursul analizei încercăm să răspundem la următoarele întrebări:

- Ce produse sunt cumpărate cel mai frecvent împreună?
- Ce reguli de asociere sunt relevante pentru înțelegerea comportamentului de cumpărare?
- Ce diferențe există între Apriori și FP-Growth?
- Care dintre cei doi algoritmi este mai eficient pentru datele analizate?
- Pot fi identificate grupuri de clienți cu obiceiuri de cumpărare asemănătoare?
- Cum evoluează vânzările în timp?
- Există tranzacții sau comportamente neobișnuite?
- Ce recomandări comerciale pot fi formulate pe baza rezultatelor?

## datele utilizate

Folosim setul de date **Online Retail**, disponibil în UCI Machine Learning Repository.

Acesta conține tranzacții ale unui comerciant online din Regatul Unit, înregistrate în perioada 1 decembrie 2010 – 9 decembrie 2011.

Setul de date include informații despre:

- identificatorul tranzacției (`InvoiceNo`);
- codul produsului (`StockCode`);
- descrierea produsului (`Description`);
- cantitatea cumpărată (`Quantity`);
- data tranzacției (`InvoiceDate`);
- prețul unitar (`UnitPrice`);
- identificatorul clientului (`CustomerID`);
- țara clientului (`Country`).

Aceste variabile permit reconstruirea coșurilor de cumpărături, calcularea valorii tranzacțiilor și analiza comportamentului clienților.

Înainte de aplicarea algoritmilor, verificăm valorile lipsă, duplicatele, tranzacțiile anulate și observațiile neobișnuite.

Datele originale sunt păstrate separat de cele procesate.

**sursa datasetului:** [Online Retail – UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail)

## metodologia

Analiza urmărește etapele KDD și CRISP-DM, pornind de la înțelegerea problemei economice și ajungând la interpretarea rezultatelor.

Începem cu analiza exploratorie a datelor (EDA), pentru a observa distribuțiile, valorile lipsă, caracteristicile tranzacțiilor și eventualele probleme de calitate a datelor.

Continuăm cu preprocesarea, transformarea variabilelor și reducerea dimensionalității prin PCA, acolo unde este relevantă.

Pentru clasificare, definim o problemă predictivă pornind de la informațiile disponibile în dataset. Comparăm arbori de decizie și modele suplimentare, evaluăm performanța acestora și analizăm factorii care influențează predicțiile.

Partea centrală a proiectului este analiza regulilor de asociere. Transformăm datele într-o matrice tranzacție–produs și aplicăm Apriori și FP-Growth în condiții comparabile.

Evaluăm regulile prin support, confidence și lift, completate de indicatori precum leverage și conviction. Urmărim atât relevanța relațiilor identificate, cât și diferențele dintre algoritmi.

Pentru a completa analiza, folosim metode de clustering pentru gruparea observațiilor, tehnici de detectare a anomaliilor și modele pentru analiza evoluției vânzărilor în timp.

Investigăm și informațiile textuale disponibile, precum și relațiile dintre produse reprezentate sub forma unui graf.

În cazul modelelor predictive, utilizăm metode de explicabilitate (XAI), iar interpretarea finală ține cont de aspectele etice, de posibilele erori și de limitele datelor.

Componenta Big Data este abordată prin prezentarea posibilităților de procesare distribuită, inclusiv utilizarea Apache Spark.

La final, reunim rezultatele pentru a formula concluzii și recomandări economice susținute de analiză.

## structura proiectului

```text
market-basket-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── notebooks/
│   ├── 01_KDD_EDA.ipynb
│   ├── 02_Preprocessing_PCA.ipynb
│   ├── 03_Decision_Trees.ipynb
│   ├── 04_Advanced_Models.ipynb
│   ├── 05_Association_Rules.ipynb
│   ├── 06_Clustering.ipynb
│   └── 07_NLP_TimeSeries_Graph_XAI.ipynb
│
├── src/
│   └── functions.py
│
├── figures/
├── results/
├── report/
└── presentation/
```

Structura urmărește organizarea recomandată pentru proiect.

Folderul `data/` conține datele originale, procesate și eventualele seturi auxiliare.

În `notebooks/` sunt organizate analizele realizate în Python, iar `src/` conține funcțiile reutilizabile.

Graficele și rezultatele sunt salvate în `figures/` și `results/`, iar raportul și prezentarea finală sunt păstrate separat.

## tehnologii utilizate

Proiectul este realizat în Python.

Bibliotecile principale sunt:

- `pandas` și `numpy` – prelucrarea datelor;
- `matplotlib` și `seaborn` – vizualizare;
- `mlxtend` – Apriori, FP-Growth și reguli de asociere;
- `scikit-learn` – PCA, clasificare, clustering și evaluare;
- `xgboost` – modele de clasificare;
- `statsmodels` – serii de timp;
- `nltk` – prelucrarea textului;
- `networkx` – analiza grafurilor;
- `shap` – explicabilitatea modelelor.

Lista bibliotecilor necesare se găsește în `requirements.txt`.

## instalare și rulare

Proiectul poate fi rulat în Python, folosind Jupyter Notebook sau JupyterLab.

Pentru instalarea bibliotecilor:

```bash
pip install -r requirements.txt
```

Datasetul se descarcă din [sursa oficială UCI](https://archive.ics.uci.edu/dataset/352/online+retail) și se salvează în folderul:

```text
data/raw/
```

Notebook-urile se execută în ordinea indicată de numele fișierelor.

Pentru reproducerea rezultatelor folosim căi relative către fișiere și o valoare fixă pentru `random_state`, acolo unde algoritmii permit acest lucru.

Rezultatele sunt salvate în `results/`, iar graficele în `figures/`.

## rezultate urmărite

Ne propunem să obținem reguli de asociere relevante, să comparăm Apriori și FP-Growth și să identificăm informații utile despre comportamentul de cumpărare.

Analizele complementare vor contribui la înțelegerea segmentelor de clienți, a tranzacțiilor neobișnuite și a evoluției vânzărilor.

Rezultatele vor fi evaluate și interpretate împreună, nu doar prezentate ca valori numerice.

Pe baza acestora vom formula recomandări comerciale concrete, ținând cont de faptul că o asociere între produse nu demonstrează automat o relație de cauzalitate.

## limite și utilizarea responsabilă a datelor

Datele provin de la un singur comerciant și acoperă o perioadă limitată, astfel încât rezultatele nu pot fi generalizate automat la alte magazine.

De asemenea, regulile identificate depind de modul de pregătire a tranzacțiilor și de pragurile alese pentru algoritmi.

În interpretarea rezultatelor vom avea în vedere aceste limite, precum și posibilele erori sau diferențe de reprezentare a anumitor categorii de observații.

## contribuții

Proiectul este realizat de trei studenți, cu responsabilități împărțite între pregătirea datelor, implementarea algoritmilor și interpretarea rezultatelor.

Contribuțiile individuale vor fi prezentate prin activitățile realizate, notebook-urile dezvoltate și rezultatele obținute de fiecare membru.

## documentație

- [Online Retail – UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail)
- [Apriori – mlxtend](https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/apriori/)
- [FP-Growth – mlxtend](https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/fpgrowth/)
- [Reguli de asociere – mlxtend](https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/association_rules/)
- [scikit-learn – documentație oficială](https://scikit-learn.org/stable/user_guide.html)
