# Übungen

Im folgenden Skript werden die Beispiel-Tabellen `VERTRETER`, `VERKAUF` und `ARTIKEL` verwendet.

## Aufgabe 1
Führe das SQL-Skript [DB-Vertreter](./SQL_-_DB-Vertreter.sql) in SQLPlus aus, um die Tabellen anzulegen und mit Beispieldaten zu füllen. Wie lautet dein Befehl um das SQL-Skript auszuführen?

### Lösung
```sql
Start H:\workspace\github\AJay1506\vgdb_ws1718\05_VertiefungDML\SQL_-_DB-Vertreter.sql
```

## Aufgabe 2
Mache dich mit den Tabellen vertraut bzgl.:
* Spalten und Datentypen
* Beziehung der Tabellen zueinander
* Datensätzen in den Tabellen und was diese bedeuten

## Aufgabe 3
Zeige alle Vertreter mit `NAME` und `VNR` an, die eine Provision von  weniger als 7% erhalten. 

### Lösung
```sql
SELECT VNAME,VNR FROM vertreter WHERE provision < 7;
```

## Aufgabe 4
Bei welchen Artikeln (`NAME` und `ARTIKELNUMMER`) liegt der Preis über `100`?

### Lösung
```sql
SELECT ANAME,ANR FROM artikel WHERE APREIS >100;
```

## Aufgabe 5
Zeige alle Vertreter an, die vor dem 01.01.1980 geboren sind.

###Lösung
```sql
SELECT * FROM vertreter WHERE to_date(geburtsdatum, 'dd.mm.yyyy') < '01.01.1980';
```

## Aufgabe 6
Füge dich als Vetreter in die Tabelle Vetreter ein mit einer Provision von 6% und der Mitarbeiternummer 7777.

###Lösung
```sql
INSERT INTO vertreter values (257, 'Jahn', to_date('15.06.1992'), 6);
```

## Aufgabe 7

###Lösung
```sql

```

## Aufgabe 8

###Lösung
```sql
UPDATE Artikel SET APREIS = 88.90 WHERE ANAME = 'Stiefel';
```

## Aufgabe 9

###Lösung
```sql
ALTER TABLE Vertreter ADD (bonus NUMBER(4,0));
```

## Aufgabe 10

###Lösung
```sql
UPDATE Vertreter SET bonus = 500;
```

## Aufgabe 11

###Lösung
```sql
ALTER TABLE Vertreter modify (VNAME VARCHAR2(20));
```

## Aufgabe 12

###Lösung
```sql
SELECT * FROM verkauf WHERE datum IS NOT NULL;
```