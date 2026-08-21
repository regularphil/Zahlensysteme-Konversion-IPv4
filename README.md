# Zahlensysteme-Konversion-IPv4

**Ein HTML-Tool zum Üben der manuellen Umrechnung zwischen Binär, Dezimal und Hexadezimal – speziell für IPv4-Adressen, Subnetting und Netzwerkberechnungen.**

---

---

## 📚 Grundlagen: Zahlensysteme im Detail

### **1. Dezimalsystem (Basis 10)**
- **Definition:** Das uns vertraute Zahlensystem mit 10 Ziffern (0–9).
- **Funktionsweise:** Jede Stelle repräsentiert eine Potenz von 10.
  - Beispiel: `200` = 2×10² + 0×10¹ + 0×10⁰ = 200 + 0 + 0 = **200**
- **Verwendung in IPv4:** Jedes Oktett einer IPv4-Adresse (z. B. `192.168.1.1`) wird als Dezimalzahl dargestellt (0–255).

---

### **2. Binärsystem (Basis 2)**
- **Definition:** Zahlensystem mit nur 2 Ziffern: **0** und **1** (Bit).
- **Funktionsweise:** Jede Stelle repräsentiert eine Potenz von 2.
  - Beispiel: `11001000` (Binär)
    = 1×2⁷ + 1×2⁶ + 0×2⁵ + 0×2⁴ + 1×2³ + 0×2² + 0×2¹ + 0×2⁰
    = 128 + 64 + 0 + 0 + 8 + 0 + 0 + 0
    = **200** (Dezimal)
- **Verwendung in IPv4:**
  - Jedes Oktett einer IPv4-Adresse besteht aus **8 Bit** (z. B. `192` = `11000000`).
  - Subnetzmasken werden oft in Binär dargestellt (z. B. `/24` = `11111111.11111111.11111111.00000000`).

---

### **3. Hexadezimalsystem (Basis 16)**
- **Definition:** Zahlensystem mit 16 Ziffern: **0–9** und **A–F** (A=10, B=11, ..., F=15).
- **Funktionsweise:** Jede Stelle repräsentiert eine Potenz von 16.
  - Beispiel: `0xC8` (Hexadezimal)
    = 12×16¹ + 8×16⁰
    = 192 + 8
    = **200** (Dezimal)
- **Verwendung in IPv4:**
  - Wird oft für MAC-Adressen oder kompakte Darstellung von Binärwerten verwendet.
  - Ein IPv4-Oktett (8 Bit) kann als **2 Hexadezimalstellen** dargestellt werden (z. B. `192` = `0xC0`).

---
### 🔢 Hexadezimal-Tabelle (1–16)


   Dezimal | Binär (8 Bit) | Hexadezimal |
 |---------|---------------|-------------|
 | 1       | `00000001`    | `0x01`      |
 | 2       | `00000010`    | `0x02`      |
 | 3       | `00000011`    | `0x03`      |
 | 4       | `00000100`    | `0x04`      |
 | 5       | `00000101`    | `0x05`      |
 | 6       | `00000110`    | `0x06`      |
 | 7       | `00000111`    | `0x07`      |
 | 8       | `00001000`    | `0x08`      |
 | 9       | `00001001`    | `0x09`      |
 | 10      | `00001010`    | `0x0A`      |
 | 11      | `00001011`    | `0x0B`      |
 | 12      | `00001100`    | `0x0C`      |
 | 13      | `00001101`    | `0x0D`      |
 | 14      | `00001110`    | `0x0E`      |
 | 15      | `00001111`    | `0x0F`      |
 | 16      | `00010000`    | `0x10`      |
---

## 🔄 Umrechnung zwischen den Systemen

---

### **1. Binär → Dezimal**
**Schritt-für-Schritt:**
1. Schreibe die Binärzahl auf und ordne jeder Stelle die entsprechende Potenz von 2 zu (von rechts nach links: 2⁰, 2¹, 2², ...).
2. Multipliziere jede Binärziffer mit ihrer Potenz von 2.
3. Addiere alle Ergebnisse.

**Beispiel:**
Binär: `11001000`
   Bit | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 |
 |-----|---|---|---|---|---|---|---|---|
 | 2ⁿ  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
 | Ergebnis | 128 | 64 | 0 | 0 | 8 | 0 | 0 | 0 |
**Summe:** 128 + 64 + 8 = **200** (Dezimal)

---

### **2. Binär → Hexadezimal**
**Schritt-für-Schritt:**
1. Teile die Binärzahl von rechts in **4er-Blöcke** auf (ggf. mit führenden Nullen auffüllen).
2. Rechne jeden 4er-Block in die entsprechende Hexadezimalziffer um.

**Beispiel:**
Binär: `11001000`
- Aufteilung: `1100 1000`
- Umrechnung:
  - `1100` = 12 (Dezimal) = **C** (Hexadezimal)
  - `1000` = 8 (Dezimal) = **8** (Hexadezimal)
- **Ergebnis:** `0xC8`

---

### 🔢 Dezimal → Binär (mit /2-Methode)

**Schritt-für-Schritt:**
1. Teile die Dezimalzahl durch **2** und notiere den **Rest** (0 oder 1).
2. Wiederhole den Vorgang mit dem **Quotienten**, bis der Quotient **0** ist.
3. Die Binärzahl ergibt sich aus den **Resten von unten nach oben** gelesen.

**Beispiel: Dezimal `200` → Binär**


   Schritt | Division | Quotient | Rest |
 |---------|----------|----------|------|
 | 1       | 200 / 2  | 100      | `0`  |
 | 2       | 100 / 2  | 50       | `0`  |
 | 3       | 50 / 2   | 25       | `0`  |
 | 4       | 25 / 2   | 12       | `1`  |
 | 5       | 12 / 2   | 6        | `0`  |
 | 6       | 6 / 2    | 3        | `0`  |
 | 7       | 3 / 2    | 1        | `1`  |
 | 8       | 1 / 2    | 0        | `1`  |

**Ergebnis:**
Die Reste von **unten nach oben** gelesen: `11001000` (Binär)

---
**Hinweis:** Diese Methode ist besonders nützlich für größere Zahlen, da sie systematisch und einfach anwendbar ist.

---

### **4. Dezimal → Hexadezimal**
**Schritt-für-Schritt:**
1. Teile die Dezimalzahl durch 16 und notiere den Rest.
2. Wiederhole den Vorgang mit dem Quotienten, bis der Quotient 0 ist.
3. Die Hexadezimalzahl ergibt sich aus den Resten (von unten nach oben gelesen).

**Beispiel:**
Dezimal: `200`
- 200 ÷ 16 = 12 (Rest: **8**)
- 12 ÷ 16 = 0 (Rest: **12** = **C**)
- **Ergebnis:** `0xC8`

---
### **5. Hexadezimal → Binär**
**Schritt-für-Schritt:**
1. Rechne jede Hexadezimalziffer in eine **4-stellige Binärzahl** um.
2. Kombiniere die Binärzahlen.

**Beispiel:**
Hexadezimal: `0xC8`
- `C` = 12 (Dezimal) = `1100` (Binär)
- `8` = 8 (Dezimal) = `1000` (Binär)
- **Ergebnis:** `11001000`

---
### **6. Hexadezimal → Dezimal**
**Schritt-für-Schritt:**
1. Rechne jede Hexadezimalziffer in ihre Dezimaläquivalente um.
2. Multipliziere jede Ziffer mit 16ⁿ (n = Position von rechts, beginnend bei 0).
3. Addiere alle Ergebnisse.

**Beispiel:**
Hexadezimal: `0xC8`
- `C` = 12, `8` = 8
- Berechnung: 12 × 16¹ + 8 × 16⁰ = 192 + 8 = **200** (Dezimal)

---

---

## 🎯 IPv4-Subnetting: Praktische Anwendung

### **Subnetzmaske in Binär**
- Eine Subnetzmaske wie `/24` bedeutet:
  - **24 Bit** für das Netzwerk, **8 Bit** für Hosts.
  - Binär: `11111111.11111111.11111111.00000000`
  - Dezimal: `255.255.255.0`

### **Netzadresse berechnen**
1. IP-Adresse und Subnetzmaske in Binär umrechnen.
2. **Bitweise AND-Operation** zwischen IP-Adresse und Subnetzmaske durchführen.
3. Ergebnis ist die Netzadresse.

**Beispiel:**
- IP: `192.168.1.10` (`11000000.10101000.00000001.00001010`)
- Subnetzmaske: `255.255.255.0` (`11111111.11111111.11111111.00000000`)
- **Netzadresse:** `192.168.1.0` (`11000000.10101000.00000001.00000000`)

---
### **Broadcast-Adresse berechnen**
1. Netzadresse in Binär umrechnen.
2. Alle Host-Bits (die durch die Subnetzmaske als 0 markiert sind) auf **1** setzen.
3. Ergebnis ist die Broadcast-Adresse.

**Beispiel:**
- Netzadresse: `192.168.1.0` (`11000000.10101000.00000001.00000000`)
- Host-Bits: `00000000` (letzte 8 Bit)
- **Broadcast-Adresse:** `192.168.1.255` (`11000000.10101000.00000001.11111111`)

---
### **Nutzbarer Host-Bereich**
- **Erste Adresse:** Netzadresse + 1
- **Letzte Adresse:** Broadcast-Adresse - 1
- **Anzahl Hosts:** 2ⁿ - 2 (n = Anzahl der Host-Bits)

**Beispiel:**
- Netzadresse: `192.168.1.0`
- Broadcast-Adresse: `192.168.1.255`
- **Host-Bereich:** `192.168.1.1` bis `192.168.1.254`
- **Anzahl Hosts:** 2⁸ - 2 = 254

---

---
## 📥 Download & Mitmachen

1. **Repository klonen:**
   ```bash
   git clone https://github.com/<username>/ipv4-binaertraining.git
