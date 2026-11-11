# Market Basket Analysis: Descoperirea tiparelor de cumpărare prin Apriori și FP-Growth

## 1. Despre proiect

Comportamentul de cumpărare al consumatorilor reprezintă o sursă importantă de informații pentru înțelegerea cererii și fundamentarea deciziilor comerciale. Datele generate de tranzacțiile unui magazin pot evidenția nu doar produsele preferate de clienți, ci și relațiile dintre produsele achiziționate în cadrul aceleiași comenzi.

Acest proiect urmărește analiza tiparelor de cumpărare prin aplicarea tehnicilor de Data Mining asupra unui set de date tranzacționale. Accentul este pus pe identificarea produselor cumpărate frecvent împreună, utilizând algoritmii **Apriori** și **FP-Growth**, precum și pe interpretarea regulilor de asociere rezultate.

Analiza este completată prin metode de explorare a datelor, clasificare, clustering, detectare a anomaliilor și alte tehnici de extragere a cunoștințelor, pentru a construi o perspectivă mai amplă asupra comportamentului de cumpărare.

Proiectul urmărește transformarea datelor brute în informații relevante economic, care pot susține decizii privind recomandările de produse, organizarea ofertelor și identificarea oportunităților comerciale.

## 2. Motivația alegerii temei

În comerțul modern, volumul mare de tranzacții face dificilă identificarea manuală a relațiilor dintre produse și a comportamentelor recurente de cumpărare. Metodele de Data Mining permit analizarea sistematică a acestor date și descoperirea unor tipare care nu sunt evidente la o examinare directă.

Alegerea temei *Market Basket Analysis* pornește de la interesul pentru aplicabilitatea practică a algoritmilor de asociere în domeniul economic. Identificarea produselor cumpărate împreună poate contribui la formularea unor ipoteze privind preferințele consumatorilor și la dezvoltarea unor strategii comerciale bazate pe date.

Apriori și FP-Growth sunt două metode consacrate pentru identificarea seturilor frecvente de produse. Compararea acestora oferă posibilitatea de a analiza atât rezultatele obținute, cât și diferențele dintre abordările algoritmice.

Tema permite, de asemenea, integrarea mai multor tehnici de analiză într-un proces coerent, de la pregătirea datelor până la interpretarea economică a rezultatelor.

## 3. Problema economică

Problema analizată constă în identificarea relațiilor dintre produsele achiziționate în cadrul tranzacțiilor comerciale și evaluarea modului în care aceste relații pot fi utilizate pentru fundamentarea deciziilor economice.

Analiza urmărește să răspundă unei întrebări centrale:

**Cum pot fi utilizate tiparele de cumpărare identificate prin Data Mining pentru a susține deciziile comerciale ale unui magazin?**

Pentru investigarea acestei probleme sunt analizate frecvența achizițiilor, asocierile dintre produse, caracteristicile tranzacțiilor și, în măsura în care datele permit, diferențele dintre comportamentele de cumpărare.

## 4. Scopul și obiectivele proiectului

### Scopul general

Identificarea și interpretarea tiparelor de cumpărare din date tranzacționale prin utilizarea algoritmilor Apriori și FP-Growth, în cadrul unui proces integrat de Data Mining.

### Obiective specifice

1. Explorarea și pregătirea unui set de date tranzacționale pentru analiză.
2. Identificarea produselor și combinațiilor de produse care apar frecvent în tranzacții.
3. Generarea și evaluarea regulilor de asociere utilizând indicatori precum support, confidence și lift.
4. Compararea algoritmilor Apriori și FP-Growth din perspectiva rezultatelor și a eficienței computaționale.
5. Investigarea comportamentului de cumpărare prin metode complementare de Data Mining.
6. Interpretarea economică a rezultatelor și formularea unor recomandări bazate pe date.

## 5. Întrebări de cercetare

Analiza este orientată de următoarele întrebări:

- Care sunt produsele cumpărate cel mai frecvent?
- Ce combinații de produse apar în mod repetat în tranzacții?
- Ce reguli de asociere indică relații relevante între produse?
- Cum diferă rezultatele obținute prin Apriori și FP-Growth?
- Care dintre cei doi algoritmi este mai eficient pentru setul de date analizat?
- Pot fi identificate categorii distincte de comportament de cumpărare?
- Există tranzacții sau comportamente neobișnuite care necesită o analiză separată?
- Cum pot fi transformate rezultatele în recomandări comerciale concrete?

Răspunsurile vor fi formulate pe baza rezultatelor obținute în urma implementării și evaluării metodelor utilizate.

## 6. Setul de date

Pentru realizarea analizei este propus setul de date **Online Retail**, disponibil în UCI Machine Learning Repository.

Acesta conține tranzacții realizate de un comerciant online din Regatul Unit, în perioada 1 decembrie 2010 – 9 decembrie 2011.

Sursa oficială:

[UCI Machine Learning Repository – Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)

Setul de date include următoarele variabile:

- **InvoiceNo** – identificatorul tranzacției;
- **StockCode** – codul produsului;
- **Description** – descrierea produsului;
- **Quantity** – cantitatea înregistrată;
- **InvoiceDate** – data și ora tranzacției;
- **UnitPrice** – prețul unitar;
- **CustomerID** – identificatorul clientului;
- **Country** – țara asociată clientului.

Aceste variabile permit analiza produselor achiziționate împreună, a valorii tranzacțiilor și a distribuției cumpărăturilor în timp.

Înaintea aplicării algoritmilor, datele vor fi verificate pentru identificarea valorilor lipsă, a duplicatelor, a tranzacțiilor anulate și a altor înregistrări care pot influența rezultatele.

Pentru analiza regulilor de asociere, tranzacțiile vor fi transformate într-o matrice de tip tranzacție–produs, care indică prezența sau absența fiecărui produs într-o comandă.

Datele originale vor fi păstrate separat de versiunile procesate, pentru a asigura trasabilitatea transformărilor.

## 7. Metodologie

Analiza este organizată conform etapelor **Knowledge Discovery in Databases (KDD)** și cadrului metodologic **CRISP-DM**, care oferă o structură pentru desfășurarea proiectelor de analiză a datelor.

### 7.1. Înțelegerea problemei și a datelor

Prima parte urmărește definirea problemei economice, identificarea obiectivelor și familiarizarea cu structura setului de date.

Vor fi analizate dimensiunea datasetului, tipurile variabilelor, distribuțiile, valorile lipsă și eventualele particularități ale tranzacțiilor.

Analiza exploratorie va include statistici descriptive și reprezentări grafice relevante pentru înțelegerea comportamentului de cumpărare.

### 7.2. Pregătirea și transformarea datelor

Datele vor fi curățate și transformate în funcție de cerințele fiecărei metode.

Vor fi investigate valorile lipsă, duplicatele, observațiile extreme și necesitatea aplicării unor transformări numerice sau categoriale.

Pentru metodele care utilizează variabile numerice vor fi analizate tehnici de scalare și reducere a dimensionalității, inclusiv **Principal Component Analysis (PCA)**.

Pentru algoritmii de asociere, datele vor fi organizate la nivel de tranzacție, astfel încât fiecare comandă să poată fi reprezentată prin produsele pe care le conține.

### 7.3. Analiza regulilor de asociere

Componenta principală a proiectului constă în aplicarea algoritmilor **Apriori** și **FP-Growth** pentru identificarea seturilor frecvente de produse.

Apriori explorează combinațiile de produse prin generarea și verificarea succesivă a seturilor candidate.

FP-Growth utilizează o reprezentare compactă a tranzacțiilor, evitând generarea explicită a tuturor candidaților în aceeași manieră ca Apriori.

Pentru comparabilitate, ambii algoritmi vor fi aplicați asupra aceleiași reprezentări a datelor și vor utiliza praguri echivalente.

Regulile de asociere vor fi evaluate prin:

- **Support** – proporția tranzacțiilor în care apare o combinație de produse;
- **Confidence** – proporția tranzacțiilor care conțin antecedentul și includ și consecventul;
- **Lift** – raportul dintre asocierea observată și cea așteptată în condiții de independență.

Pentru o analiză suplimentară vor fi utilizați și indicatori precum leverage, conviction și cosine sau Jaccard.

Rezultatele vor fi comparate din perspectiva numărului de combinații frecvente, a regulilor identificate și a timpului de execuție.

Regulile selectate vor fi interpretate în raport cu posibile aplicații comerciale, precum recomandările de produse și ofertele complementare.

### 7.4. Analize complementare

Pentru extinderea interpretării economice vor fi utilizate și alte metode de Data Mining.

**Clasificarea** va permite investigarea unei probleme predictive definite pe baza variabilelor disponibile. Vor fi analizate metode bazate pe arbori de decizie și algoritmi suplimentari de clasificare, iar performanța acestora va fi evaluată prin indicatori adecvați.

**Clusteringul** va fi utilizat pentru identificarea unor grupuri de observații cu caracteristici similare, prin metode precum K-Means, K-Medoids, clustering ierarhic și DBSCAN.

**Detectarea anomaliilor** va urmări identificarea tranzacțiilor sau comportamentelor neobișnuite, utilizând metode statistice și algoritmice.

**Analiza seriilor de timp** va examina evoluția temporală a unor indicatori economici derivați din tranzacții, precum valoarea vânzărilor.

**Analiza textului (NLP)** va fi realizată în limita informațiilor textuale disponibile și a relevanței acestora pentru problema economică. Eventualele analize care necesită texte suplimentare vor utiliza surse documentate separat.

**Analiza grafurilor** va permite reprezentarea relațiilor dintre produse sub forma unei rețele și investigarea structurii acesteia prin indicatori specifici.

**Explicabilitatea modelelor (XAI)** va contribui la interpretarea factorilor care influențează predicțiile obținute prin clasificare.

Vor fi discutate și posibilitățile de extindere a analizei către volume mari de date, prin instrumente precum Apache Spark.

### 7.5. Evaluarea și interpretarea rezultatelor

Rezultatele fiecărei metode vor fi evaluate prin indicatori corespunzători.

În cazul clasificării vor fi analizate performanța predictivă, capacitatea de generalizare și eventualele dezechilibre dintre clase.

Pentru clustering vor fi utilizate criterii de evaluare a separării și coeziunii grupurilor, alături de interpretarea caracteristicilor acestora.

Pentru regulile de asociere, accentul va fi pus pe relevanța indicatorilor și pe utilitatea economică a relațiilor identificate.

Interpretarea finală va urmări corelarea rezultatelor obținute prin metode diferite, evitând tratarea acestora ca analize independente.

## 8. Structura proiectului

Repository-ul este organizat astfel încât datele, codul, rezultatele și documentația să fie păstrate separat.

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
│   ├── 01_EDA_Preprocessing.ipynb
│   ├── 02_PCA.ipynb
│   ├── 03_Classification.ipynb
│   ├── 04_Association_Rules.ipynb
│   ├── 05_Clustering_Anomalies.ipynb
│   ├── 06_Time_Series.ipynb
│   └── 07_NLP_Graph_XAI.ipynb
│
├── src/
│   └── functions.py
│
├── figures/
├── results/
├── report/
└── presentation/
```

### Descrierea directoarelor

**data/** conține seturile de date originale, procesate și eventualele surse auxiliare.

**notebooks/** conține analizele realizate în Python, organizate în ordinea logică a proiectului.

**src/** include funcțiile reutilizabile pentru pregătirea datelor, evaluarea modelelor și generarea rezultatelor.

**figures/** este destinat reprezentărilor grafice.

**results/** conține rezultatele analitice exportate, inclusiv tabelele comparative și regulile de asociere.

**report/** conține raportul final al proiectului.

**presentation/** include materialele utilizate pentru prezentarea rezultatelor.

Structura poate fi adaptată pe parcursul implementării, cu păstrarea separării dintre date, cod și rezultate.

## 9. Tehnologii și biblioteci

Implementarea este realizată în **Python**, utilizând biblioteci pentru prelucrarea datelor, învățare automată și vizualizare.

Principalele instrumente avute în vedere sunt:

- **pandas** – manipularea și analiza datelor;
- **NumPy** – operații numerice;
- **Matplotlib** și **Seaborn** – vizualizare;
- **scikit-learn** – clasificare, clustering, PCA și evaluare;
- **mlxtend** – Apriori, FP-Growth și reguli de asociere;
- **SciPy** – metode statistice;
- **statsmodels** – analiza seriilor de timp;
- **NetworkX** – analiza grafurilor;
- **SHAP** – interpretabilitatea modelelor;
- **NLTK** – prelucrarea textului.

În funcție de implementarea efectivă pot fi utilizate și alte biblioteci, documentate în fișierul `requirements.txt`.

## 10. Instalare și rulare

### 10.1. Descărcarea repository-ului

```bash
git clone https://github.com/UTILIZATOR/market-basket-analysis.git
cd market-basket-analysis
```

Adresa de mai sus este un exemplu și trebuie înlocuită cu adresa reală a repository-ului.

### 10.2. Crearea unui mediu virtual

```bash
python -m venv .venv
```

Activarea mediului virtual pe Windows:

```bash
.venv\Scripts\activate
```

Activarea pe Linux sau macOS:

```bash
source .venv/bin/activate
```

### 10.3. Instalarea dependențelor

```bash
pip install -r requirements.txt
```

### 10.4. Pregătirea datelor

Setul de date poate fi descărcat din sursa oficială:

[Online Retail – UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail)

Fișierul original se plasează în directorul:

```text
data/raw/
```

### 10.5. Executarea analizelor

Notebook-urile se deschid în Jupyter Notebook sau într-un mediu compatibil și se execută în ordinea indicată de denumirea fișierelor.

Ordinea generală este:

```text
Încărcarea datelor
        ↓
Analiza exploratorie
        ↓
Curățarea și transformarea datelor
        ↓
PCA și clasificare
        ↓
Apriori și FP-Growth
        ↓
Clustering și detectarea anomaliilor
        ↓
Analize temporale, textuale și de rețea
        ↓
Evaluarea și interpretarea rezultatelor
        ↓
Concluzii și recomandări economice
```

Fișierele generate în urma analizelor vor fi salvate în directoarele `results/` și `figures/`.

## 11. Rezultate urmărite

Prin implementarea proiectului se urmărește obținerea unei imagini structurate asupra relațiilor dintre produsele cumpărate și asupra comportamentului tranzacțional.

Rezultatele principale vizate sunt:

- identificarea produselor și combinațiilor de produse frecvente;
- extragerea regulilor de asociere relevante;
- compararea performanței algoritmilor Apriori și FP-Growth;
- identificarea unor grupuri de comportamente similare;
- evidențierea tranzacțiilor neobișnuite;
- analiza evoluției unor indicatori economici în timp;
- interpretarea rezultatelor prin reprezentări grafice și indicatori cantitativi.

Rezultatele vor fi prezentate după executarea algoritmilor și vor fi însoțite de explicații privind semnificația și limitele lor.

## 12. Relevanță economică

Analiza regulilor de asociere poate oferi informații utile pentru înțelegerea relațiilor dintre produsele comercializate.

În funcție de rezultatele obținute, aceste informații pot fundamenta propuneri privind:

- recomandarea unor produse complementare;
- dezvoltarea unor oferte comerciale bazate pe combinații de produse;
- organizarea campaniilor de promovare;
- identificarea unor categorii de produse cu relații de cumpărare recurente;
- analiza comportamentelor de consum și a diferențelor dintre segmente.

O regulă de asociere nu demonstrează, prin ea însăși, existența unei relații cauzale. De aceea, recomandările vor fi formulate cu prudență și raportate la contextul economic al datelor.

## 13. Limitări și aspecte etice

Rezultatele proiectului depind de caracteristicile și calitatea setului de date utilizat.

Datele reflectă activitatea unui anumit comerciant într-o perioadă determinată, astfel încât tiparele identificate nu pot fi generalizate automat la alte magazine sau piețe.

Preprocesarea poate influența rezultatele, în special prin deciziile privind tranzacțiile anulate, valorile lipsă și produsele cu frecvență redusă.

De asemenea, indicatorii utilizați pentru evaluarea regulilor de asociere trebuie interpretați împreună, pentru a evita concluziile bazate exclusiv pe frecvență.

Din perspectivă etică, analiza va urmări utilizarea responsabilă a datelor, limitarea prelucrării informațiilor personale și prezentarea transparentă a metodelor și limitărilor.

Identificatorii clienților vor fi tratați ca variabile tehnice de analiză, fără încercarea de identificare a persoanelor.

## 14. Documentație și livrabile

Repository-ul este destinat să reunească materialele necesare pentru înțelegerea și reproducerea analizei:

- codul Python și notebook-urile utilizate;
- informații privind sursa și pregătirea datelor;
- lista dependențelor;
- reprezentările grafice;
- rezultatele exportate;
- raportul final;
- prezentarea proiectului.

Raportul va detalia metodologia, implementarea, evaluarea rezultatelor și concluziile economice.

Fișierele de date vor fi distribuite numai în măsura permisă de condițiile sursei originale.

## 15. Referințe

1. Chen, D. (2015). *Online Retail*. UCI Machine Learning Repository.  
   https://doi.org/10.24432/C5BW33

2. Agrawal, R., & Srikant, R. (1994). *Fast Algorithms for Mining Association Rules in Large Databases*. Proceedings of the 20th International Conference on Very Large Data Bases (VLDB), 487–499.

3. Han, J., Pei, J., & Yin, Y. (2000). *Mining Frequent Patterns without Candidate Generation*. Proceedings of the 2000 ACM SIGMOD International Conference on Management of Data, 1–12.  
   https://doi.org/10.1145/342009.335372

4. Han, J., Kamber, M., & Pei, J. (2011). *Data Mining: Concepts and Techniques* (3rd ed.). Morgan Kaufmann.

5. Chapman, P., Clinton, J., Kerber, R., Khabaza, T., Reinartz, T., Shearer, C., & Wirth, R. (2000). *CRISP-DM 1.0: Step-by-step Data Mining Guide*.

6. Raschka, S. *mlxtend: Frequent Pattern Mining*. Documentație oficială.  
   https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/

7. scikit-learn Developers. *scikit-learn User Guide*. Documentație oficială.  
   https://scikit-learn.org/stable/user_guide.html

8. pandas Development Team. *pandas Documentation*.  
   https://pandas.pydata.org/docs/

9. NetworkX Developers. *NetworkX Documentation*.  
   https://networkx.org/documentation/stable/

10. Lundberg, S. M., & Lee, S.-I. (2017). *A Unified Approach to Interpreting Model Predictions*. Advances in Neural Information Processing Systems, 30.  
    https://arxiv.org/abs/1705.07874
