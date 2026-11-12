Acest folder conține setul de date Sentiment Labelled Sentences, preluat de la UCI Machine Learning Repository. L-am adăugat în proiect pentru partea de analiză a sentimentelor (NLP).

În proiectul nostru, Online Retail este sursa principală și ne ajută să analizăm ce produse se cumpără împreună și cum cumpără clienții. Totuși, Online Retail nu conține recenzii sau opinii scrise de clienți. De aceea, pentru partea de analiză a textelor, folosim un set de date separat, pe care îl păstrăm în data/external/.

Ce conține fiecare fișier:

- amazon_cells_labelled.txt conține 1.000 de propoziții din recenzii despre produse, în special telefoane și accesorii. Ne ajută să analizăm opinii pozitive și negative despre produse, fiind cel mai apropiat de tema comerțului online.

- imdb_labelled.txt conține 1.000 de propoziții din recenzii despre filme. Îl folosim pentru a observa cum funcționează analiza sentimentelor pe texte din alt domeniu.

- yelp_labelled.txt conține 1.000 de propoziții din recenzii despre restaurante. Îl folosim pentru a compara rezultatele analizei sentimentelor cu cele obținute pe celelalte două surse.

- readme.txt este documentul original care însoțește setul de date. Explică proveniența recenziilor și semnificația etichetelor. Îl păstrăm nemodificat.

În total sunt 3.000 de propoziții în limba engleză. Fiecare propoziție este urmată de o etichetă: 0 înseamnă sentiment negativ, iar 1 înseamnă sentiment pozitiv. Fiecare dintre cele trei fișiere are 500 de exemple negative și 500 pozitive. Textul și eticheta sunt separate prin TAB.

Ce vom face cu ele în proiect:

Mai întâi vom încărca fișierele și vom verifica textele, etichetele și eventualele valori lipsă sau duplicate. Apoi vom pregăti propozițiile pentru analiză și le vom transforma în caracteristici numerice, de exemplu cu TF-IDF. Vom antrena un model simplu de clasificare a sentimentelor, cum ar fi Logistic Regression sau Naive Bayes, și vom verifica cât de bine recunoaște opiniile pozitive și negative. Pentru evaluare vom folosi indicatori precum accuracy, precision, recall și F1-score. La final vom compara, dacă este util, rezultatele pentru Amazon, IMDb și Yelp.

Această analiză completează proiectul de Data Mining, dar este separată de Market Basket Analysis. Recenziile nu provin de la clienții din Online Retail și nu pot fi asociate direct cu facturile, produsele sau CustomerID-urile din acel fișier.

De ce păstrăm datele în external:

Folderul data/raw/ conține setul principal Online Retail, data/processed/ conține fișierele prelucrate din acesta, iar data/external/ conține un set suplimentar, provenit din altă sursă. În acest fel, organizarea proiectului este clară și putem arăta de unde vine fiecare analiză.

Sursa oficială:
https://archive.ics.uci.edu/dataset/331/sentiment+labelled+sentences



