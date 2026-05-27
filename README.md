# Umweltmonitoring-Kaggle-Challange-Beijing
In dieser Challenge sagen Sie für 12 Luftqualitätsstationen in Beijing das nächste PM2.5-Tagesmittel vorher. Die Daten stammen aus dem Datensatz Beijing Multi-Site Air Quality und wurden für diese Aufgabe von Stundenwerten auf Tagesebene aggregiert.

## Aktueller Modellansatz

Die Submission verwendet ausschließlich Features, die auch im Testzeitraum bekannt sind: Station, Windrichtung, Luftschadstoff- und Wettervariablen sowie Monat und Wochentag. `pm25`-Lag-Features werden bewusst nicht verwendet, weil vergangene Zielwerte innerhalb des mehrmonatigen Testzeitraums bei der Batch-Vorhersage nicht vorliegen.

Die Regularisierung wird mit chronologischen Validierungsfenstern innerhalb des Fit-Zeitraums abgestimmt. Das ausgeführte Notebook wählt `Lasso(alpha=0.1)` und erreicht auf dem zeitlich späteren Holdout von Januar bis Juni 2016 einen MSE von `475.884`.

Das Notebook `notebookf1e5f185e6.ipynb` enthält EDA, Modellierung und die Erzeugung von `submission.csv`. Das Skript `baseline_solutionpy.sec` enthält die entsprechende Kaggle-Pipeline mit Kaggle-Pfaden.
