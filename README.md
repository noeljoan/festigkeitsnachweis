# ⚙ Festigkeitsnachweis FKM — Achse mit Absatz

Interaktive Web-App zur Berechnung des statischen Festigkeitsnachweises und Dauerfestigkeitsnachweises für stabförmige Bauteile (Achsen/Wellen mit Absatz) nach der **FKM-Richtlinie** und **DIN EN 10083-1**.

🔗 **Live-Demo:** [https://noeljoan.github.io/festigkeitsnachweis-fkm/)

---

## Screenshot

![Dashboard](screenshot.png)

## Inhalt

- [Funktionsumfang](#funktionsumfang)
- [Berechnungsgrundlagen](#berechnungsgrundlagen)
- [Werkstoffvorauswahl](#werkstoffvorauswahl)
- [Installation](#installation)
- [Deployment auf GitHub Pages](#deployment-auf-github-pages)
- [Projektstruktur](#projektstruktur)

---

## Funktionsumfang

- **Statischer Festigkeitsnachweis** (FKM Kap. 1) mit plastischer Stützzahl
- **Dauerfestigkeitsnachweis** (FKM Kap. 2) mit Mittelspannungseinfluss
- Berechnung von Kerbwirkungs-, Rauheits- und Konstruktionsfaktoren
- Auslastungsgrade nach von-Mises (GH-Hypothese) für kombinierte Biegung + Torsion
- Technologischer Größenfaktor (Kd,m / Kd,p) nach Bauteilabmessung
- Werkstoffvorauswahl mit Kennwerten nach DIN EN 10083-1
- Ergebnisanzeige in 4 Tabs: Statisch · Dauerfestigkeit · Faktoren · Spannungen

---

## Berechnungsgrundlagen

| Nachweis | Norm / Quelle |
|---|---|
| Statischer Festigkeitsnachweis | FKM-Richtlinie, Kap. 1 |
| Dauerfestigkeitsnachweis | FKM-Richtlinie, Kap. 2 |
| Werkstoffkennwerte | DIN EN 10083-1 (Vergütungsstahl) |
| Kerbwirkungszahl (rechnerisch) | FKM Tab. 2.3.2 / 2.3.3, Gl. 2.3.10 |
| Mittelspannungsempfindlichkeit | FKM Gl. 2.4.34 |
| Sicherheitsfaktoren | FKM Tab. 1.5.1 / 2.5.1 |

Anwendungsbereich: **stabförmige Bauteile**, Nennspannungskonzept, Überlastungsfall F2, zyklisch konstante Belastung (Umlaufbiegung + Torsion).

---

## Werkstoffvorauswahl

| Werkstoff | Rm,N [MPa] | Re,N [MPa] |
|---|---|---|
| 41Cr4 | 1000 | 800 |
| 42CrMo4 | 1100 | 900 |
| 34CrMo4 | 1000 | 800 |
| C45 | 700 | 490 |
| 34CrNiMo6 | 1200 | 1000 |
| 30CrNiMo8 | 1250 | 1050 |
| 37Cr4 | 950 | 750 |

Benutzerdefinierte Werkstoffkennwerte sind ebenfalls eingebbar.

---

## Installation

```bash
git clone https://github.com/noeljoan/festigkeitsnachweis-fkm.git
cd festigkeitsnachweis-fkm
npm install
npm run dev
```

Öffne anschließend [http://localhost:5173](http://localhost:5173) im Browser.

### Voraussetzungen

- Node.js ≥ 18
- npm ≥ 9

---

## Deployment auf GitHub Pages

```bash
npm run deploy
```

Dieser Befehl baut die App (`vite build`) und veröffentlicht den `dist`-Ordner auf dem Branch `gh-pages`.

Einmalige Einrichtung in **GitHub → Settings → Pages**:

- Source: `Deploy from a branch`
- Branch: `gh-pages` / `/ (root)`

> **Hinweis:** In `vite.config.js` muss `base` auf den Repo-Namen gesetzt sein:
> ```js
> export default defineConfig({
>   base: '/festigkeitsnachweis-fkm/',
>   plugins: [react()],
> })
> ```

---

## Projektstruktur

```
festigkeitsnachweis-fkm/
├── src/
│   ├── App.jsx          # Hauptkomponente (Berechnung + GUI)
│   └── main.jsx         # React-Einstiegspunkt
├── public/
├── index.html
├── vite.config.js
├── package.json
└── README.md
```

---

## Anwendungsbeispiel

Die Standardwerte entsprechen dem Beispiel **6.1 „Achse mit Absatz"** aus der FKM-Richtlinie:

![Anwendungsbeispiel](Anwendungsbeispiel.pdf)
![Dashboard](geometrie.png)

| Parameter | Wert |
|---|---|
| Werkstoff | 41Cr4 (DIN EN 10083) |
| d / D | 42 mm / 50 mm |
| r/d | 0,119 |
| Biegespannung Sa,b | ±150 MPa |
| Torsion Tm,t ± Ta,t | 50 ± 100 MPa |
| Sicherheit jm / jD | 1,75 / 1,2 |

Ergebnis: statischer Auslastungsgrad **47 %**, zyklischer Auslastungsgrad **≈ 102 %** (Nachweis annähernd erbracht).

---

## Lizenz

MIT License — frei verwendbar und erweiterbar.

---

*Erstellt mit React + Vite · Berechnung nach FKM-Richtlinie (6. Auflage)*
