# 1. Formel

## Beispiel (alles auf demselben Blatt)

### Deutsche Excel-Version

```excel
=WENN(ODER($C2=$B$2;$C2=$B$7;$C2=$B$9);$C:$C;$D:$D)
```

### Englische Excel-Version

```excel
=IF(OR($C2=$B$2,$C2=$B$7,$C2=$B$9),$C:$C,$D:$D)
```

---

## Beispiel mit zwei Blättern

### Deutsche Excel-Version

```excel
=WENN(ODER(Operation!$C2=Values!$B$2;Operation!$C2=Values!$B$7;Operation!$C2=Values!$B$9);Values!$C:$C;Values!$D:$D)
```

### Englische Excel-Version

```excel
=IF(OR(Operation!$C2=Values!$B$2,Operation!$C2=Values!$B$7,Operation!$C2=Values!$B$9),Values!$C:$C,Values!$D:$D)
```

---

# 2. Erklärung

Die Formel prüft den Wert in `C2`.

Wenn der Wert von `C2` mit einem der definierten Vergleichswerte übereinstimmt (`B2`, `B7` oder `B9`), wird die Liste aus **Spalte C** verwendet.

Andernfalls wird die Liste aus **Spalte D** verwendet.

### Logik

```text
C2 = B2  → Spalte C
C2 = B7  → Spalte C
C2 = B9  → Spalte C
sonst    → Spalte D
```

### Beispiel

```text
B2 = APPLE
B7 = BANANA
B9 = ORANGE

C2 = BANANA
```

Ergebnis:

```text
Dropdown verwendet Werte aus Spalte C
```

Wenn:

```text
C2 = MANGO
```

Ergebnis:

```text
Dropdown verwendet Werte aus Spalte D
```

---

# 3. Anleitung Datenüberprüfung

## Schritt 1 – Namensmanager öffnen

Menü:

```text
Formeln → Namensmanager → Neu
```

Name:

```text
MeineListe
```

Bezieht sich auf:

### Deutsche Excel-Version

```excel
=WENN(ODER(Operation!$C2=Values!$B$2;Operation!$C2=Values!$B$7;Operation!$C2=Values!$B$9);Values!$C:$C;Values!$D:$D)
```

### Englische Excel-Version

```excel
=IF(OR(Operation!$C2=Values!$B$2,Operation!$C2=Values!$B$7,Operation!$C2=Values!$B$9),Values!$C:$C,Values!$D:$D)
```

Speichern.

---

## Schritt 2 – Datenüberprüfung einrichten

Zelle auswählen.

Menü:

```text
Daten → Datenüberprüfung
```

Zulassen:

```text
Liste
```

Quelle:

```excel
=MeineListe
```

Bestätigen.

---

## Schritt 3 – Testen

### Fall 1

```text
Values!B2 = APPLE
Values!B7 = BANANA
Values!B9 = ORANGE

Operation!C2 = APPLE
```

Ergebnis:

```text
Dropdown verwendet Values!C:C
```

---

### Fall 2

```text
Operation!C2 = MANGO
```

Ergebnis:

```text
Dropdown verwendet Values!D:D
```
