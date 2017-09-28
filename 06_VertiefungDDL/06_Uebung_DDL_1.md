# Übungen

## Aufgabe 1
Erzeuge eine View, die folgendes Ergebnis repräsentiert, das nur Verkäufe vom `27.06.2015` umfasst:

| VNR  | VNAME    | UNR  | ANZAHL | ANR | ANAME         | APREIS  |
| ---- | -------- | ---- | ------ | --- | ------------- | ------- |
| 4321 | Jahred   | 1010 | 7      | 12  | Stiefel       | 89,99   |
| 3401 | Schmitz  | 1000 | 10     | 12  | Stiefel       | 89,99   |
| 4321 | Jahred   | 1011 | 15     | 11  | Pullover      | 35,2    |
| 1010 | Mueller  | 1006 | 40     | 11  | Pullover      | 35,2    |
| 5337 | Ritsch   | 1003 | 70     | 11  | Pullover      | 35,2    |
| 4321 | Jahred   | 1009 | 35     | 13  | Wintermantel  | 123,8   |
| 1010 | Mueller  | 1007 | 35     | 13  | Wintermantel  | 123,8   |

### Lösung
```sql
Create OR REPLACE VIEW v_Uebung06 AS
SELECT v.vnr, vname, unr, anzahl, v.anr, aname, apreis
FROM verkauf v
INNER JOIN artikel a ON ( v.anr = a.anr)
INNER JOIN vertreter vt ON (vt.vnr=v.vnr)
WHERE to_date('27.06.2015', 'dd.mm.yyyy') = Datum; 
```

## Aufgabe 2
Wie viele **Verkäufe** hat der Vertreter Mueller am `27.06.15` durchgeführt?

### Lösung
```sql
SELECT COUNT(anzahl) 
FROM v_Uebung06
WHERE VNAME = 'Mueller';
```

## Aufgabe 3
Wie viele **Artikel** hat der Vertreter Mueller am `27.06.15 verkauft?

### Lösung
```sql
SELECT SUM(anzahl) 
FROM v_Uebung06
WHERE VNAME = 'Mueller';
```

## Aufgabe 4
Wie viele Artikel wurden durchschnittlich am `27.06.15` verkauft?

### Lösung
```sql
SELECT AVG(anzahl) 
FROM verkauf
WHERE to_date('27.06.2015', 'dd.mm.yyyy') = Datum;
```

## Aufgabe 5
Welcher Artikel (`ANR` und `ANAME`) wurde am `27.06.15` nicht verkauft?

### Lösung
```sql
SELECT DISTINCT artikel.anr, ANAME
FROM ARTIKEL
INNER JOIN verkauf v ON (v.anr = artikel.anr)
WHERE to_date('27.06.2015', 'dd.mm.yyyy') != Datum;
```
