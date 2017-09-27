# Übung

Für folgende Aufgaben werden die Tabellen Vertreter, Verkauf und Artikel verwendet.

## Aufgabe 1
Wie viel kostet der teuerste Artikel?

### Lösung
```sql
SELECT MAX(APREIS)
FROM Artikel;
```

## Aufgabe 2
Wie hoch ist die durchschnittliche Provision aller Vertreter?

### Lösung
```sql
SELECT AVG(Provision) Provisionsdurchschnitt
FROM Vertreter;
```

## Aufgabe 3
Wie viele Artikel hat der Vertreter Mueller insgesamt verkauft?

### Lösung
```sql
SELECT SUM(Anzahl)
FROM Verkauf
WHERE VNR = (SELECT VNR FROM Vertreter WHERE VNAME= 'Mueller');
```

## Aufgabe 4
Wie viele Wintermäntel hat der Vertreter Jahred insgesamt verkauft?

### Lösung
```sql
SELECT SUM(Anzahl)
FROM Verkauf
WHERE VNR = (SELECT VNR FROM Vertreter WHERE VNAME= 'Jahred')
AND anr=(SELECT anr FROM Artikel WHERE ANAME = 'Wintermantel');
```

## Aufgabe 5
Wessen Provision liegt über der durchschnittlichen Provision aller Vertreter?
> Tipp: Nutze hier eine Unterabfrage, um den Durchschnitt aller Vertreter zu ermitteln.

### Lösung
```sql
SELECT vnr, vname 
FROM Vertreter
WHERE Provision > (
	SELECT AVG(Provision)
	FROM Vertreter);
```

