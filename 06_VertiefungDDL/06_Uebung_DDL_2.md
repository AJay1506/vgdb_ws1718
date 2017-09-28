# Übungen

Führe das Skript [DB-Vertreter](./SQL_-_DB-Vertreter.sql) aus.

## Aufgabe 1
Lege für die Tabellen `VERTRETER`, `VERKAUF` und `ARTIKEL` Primary Key Constraints (`PK`) an.

### Lösung
```sql
ALTER TABLE Vertreter
ADD CONSTRAINT pkver PRIMARY KEY (vnr);	

ALTER TABLE Verkauf
ADD CONSTRAINT pkverk PRIMARY KEY (unr);

ALTER TABLE Artikel
ADD CONSTRAINT pkart PRIMARY KEY (anr);	
```

## Aufgabe 2
Lege für die Tabelle `VERKAUF` alle notwendigen Foreign Key Constraints (`FK`) an.

### Lösung
```sql
ALTER TABLE verkauf
ADD CONSTRAINT fkverk_Art FOREIGN KEY(anr) REFERENCES artikel;
```

## Aufgabe 3
Lösche den Foreign Key Constraint `FK_DEPTNO`. Dieser ist für die Spalte `DEPTNO` in der Tabelle `EMP` definiert.

### Lösung
```sql
ALTER TABLE emp
DROP CONSTRAINT FK_deptno;
```

## Aufgabe 4
Lege den benötigten Foreign Key Constraint (`FK`) für die Tabelle `EMP` neu an.

### Lösung
```sql
ALTER TABLE emp
ADD CONSTRAINT fkdeptno FOREIGN KEY(DEPTNO) REFERENCES dept(DEPTNO);
```

