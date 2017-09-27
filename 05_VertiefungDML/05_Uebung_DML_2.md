# Übung

Löse folgende Aufgaben mit Hilfe von Unterabfragen.

## Aufgabe 1
Zeige alle Vertreter (`VNR`, `VNAME`) an, die bereits Artikel mit der `ANR` = `13` verkauft haben.

### Lösung
```sql
SELECT v.vnr, vname FROM Vertreter v WHERE v.vnr IN(SELECT VNR FROM Verkauf WHERE ANR = 13);
```

## Aufgabe 2
Zeige alle Artikel (`ANR`, `ANAME`) an, die der Vertreter mit der `VNR` = `4321` am `27.06.2015` verkauft hat.

### Lösung
```sql
SELECT a.anr,ANAME FROM Artikel a WHERE a.anr IN (SELECT anr FROM Verkauf WHERE VNR = 4321 AND Datum = to_date('27.06.2015', 'dd.mm.yyyy'));
```

## Aufgabe 3
Zeige alle Vertreter (`VNR`, `VNAME`) an, die bereits Artikel verkauft haben, deren Preis über `100`€ liegt.

### Lösung
```sql
SELECT v.vnr,VNAME FROM Vertreter v 
WHERE v.vnr IN (SELECT VNR FROM Artikel INNER JOIN Verkauf ON Artikel.anr=Verkauf.anr WHERE APREIS > 100);
```

## Aufgabe 4
Zeige alle Vertreter, die noch nie den Artikel mit der `ANR` = `22` verkauft haben.

### Lösung
```sql
SELECT * FROM Vertreter WHERE vnr NOT IN(SELECT VNR FROM Verkauf WHERE ANR = 22);
```

## Aufgabe 5
Welche Vertreter (`VNR`) haben am `27.06.2015` mehr Artikel mit `ANR` = `12` verkauft als der Vertreter mit `VNR` = `4321`?

### Lösung
```sql
SELECT VNR 
FROM Verkauf 
WHERE Anzahl > (
	SELECT Anzahl 
	FROM Verkauf 
	WHERE Datum = to_date('27.06.2015', 'dd.mm.yyyy') 
	AND VNR = (SELECT VNR FROM Vertreter WHERE VNAME= 'Jahred')  
	AND ANR = (SELECT ANR FROM Artikel WHERE ANAME= 'Stiefel')
)
AND Datum = to_date('27.06.2015', 'dd.mm.yyyy')
AND ANR =(SELECT ANR FROM Artikel WHERE ANAME= 'Stiefel');
```

