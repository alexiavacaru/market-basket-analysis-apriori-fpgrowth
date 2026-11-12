
Acest folder conține setul de date Sentiment Labelled Sentences, preluat de la UCI Machine Learning Repository. Îl folosim în proiectul nostru de Data Mining pentru analiza sentimentelor (NLP), deoarece setul principal, Online Retail, conține informații despre cumpărături, dar nu și recenzii ale clienților.

Ce conține folderul??

Setul include 3.000 de propoziții în limba engleză, împărțite în trei fișiere:

* amazon_cells_labelled.txt – 1.000 de recenzii despre produse, în special telefoane și accesorii. Este cel mai apropiat de tema comerțului online.
* imdb_labelled.txt – 1.000 de recenzii despre filme, folosite pentru a testa analiza sentimentelor într-un alt domeniu.
* yelp_labelled.txt – 1.000 de recenzii despre restaurante, folosite pentru compararea rezultatelor.
* readme.txt – documentația originală a setului de date, pe care o păstrăm nemodificată.

Fiecare propoziție are o etichetă: 0 = negativ, 1 = pozitiv. Fiecare sursă conține 500 de exemple negative și 500 pozitive.

Cum vom folosi datele

* verificăm și curățăm textele – identificăm valorile lipsă, duplicatele și eventualele erori;
* pregătim datele pentru analiză – transformăm textele în valori numerice folosind TF-IDF;
* antrenăm un model de clasificare – folosim Logistic Regression sau Naive Bayes pentru a identifica automat sentimentul;
* evaluăm rezultatele – calculăm accuracy, precision, recall și F1-score și comparăm rezultatele între Amazon, IMDb și Yelp.

Legătura cu proiectul nostru

Proiectul nostru analizează datele Online Retail prin mai multe metode de Data Mining:

* Market Basket Analysis – identificăm produsele cumpărate împreună, folosind Apriori și FP-Growth;
* analiza clienților – calculăm indicatori precum numărul comenzilor și valoarea cumpărăturilor, pentru segmentarea clienților;
* analiza sentimentelor (NLP) – folosim setul extern pentru clasificarea recenziilor pozitive și negative.

Analiza NLP completează proiectul, dar este independentă de Online Retail. Recenziile nu aparțin clienților din setul principal și nu pot fi asociate direct cu facturile sau produsele lor.

De ce păstrăm datele în external

* data/raw/ – datele originale Online Retail;
* data/processed/ – tranzacțiile curățate, matricea coșurilor și indicatorii clienților;
* data/external/ – datele suplimentare pentru analiza sentimentelor, provenite dintr-o sursă separată.

Această organizare ne permite să păstrăm separat datele originale, cele prelucrate și cele externe, astfel încât proiectul să fie ușor de urmărit și reprodus.

Sursa oficială:

https://archive.ics.uci.edu/dataset/331/sentiment+labelled+sentences
