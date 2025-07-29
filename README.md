# Reinforcement Learning – Flappy Bird mit DQN

## Motivation
Dieses Projekt wurde im Rahmen des Kurses *Reinforcement Learning* entwickelt.  
Ziel war es, ein praxisnahes Beispiel für die Anwendung von Reinforcement Learning zu implementieren.  
Die Wahl fiel auf *Flappy Bird*, da das Spiel einfach verständlich, schnell ausführbar und dennoch herausfordernd für einen RL-Agenten ist. Durch die geringe Anzahl möglicher Aktionen eignet es sich ideal zur Demonstration eines **Deep-Q-Network (DQN)**.  

Der Projektbericht beschreibt die Wahl der Umgebung, den Aufbau und das Training des RL-Agenten sowie die Analyse der Ergebnisse. Zusätzlich enthält er Visualisierungen, eine kritische Reflexion der Resultate und mögliche Verbesserungsansätze wie Double-DQN oder Dueling-DQN.

## Projektbeschreibung
Das Projekt implementiert einen **DQN-Agenten**, der lernt, *Flappy Bird* selbstständig zu spielen.  
Das Training erfolgt mit **PyTorch** in Kombination mit einer selbst erstellten **pygame-Umgebung**.  
Zur Stabilisierung des Lernprozesses wird ein **Replay Buffer** und ein **Target Network** verwendet. Während des Trainings werden **Rewards**, **Moving Averages**, **Histogramme** und **Lernkurven** visualisiert.

## Projektstruktur
```
├── flappy.ipynb          # Haupt-Notebook mit Code, Training und Visualisierung
├── requirements.txt      # Benötigte Python-Bibliotheken
├── README.md             # Projektbeschreibung und Anleitung
```

## Features
- Eigene **Flappy-Bird-Umgebung** mit pygame  
- **Deep-Q-Network (DQN)** zur Steuerung des Agenten  
- **Experience Replay** und **Target Network** für stabileres Training  
- **Training über mehrere Episoden mit ε-greedy-Policy**  
- **Visualisierung von Rewards, Moving Average, Histogrammen und Lernkurven**  
- **Automatisches Speichern des Modells während des Trainings**

## Installation

### 1️ Repository klonen oder herunterladen
```bash
git clone <REPO-URL>
cd <REPO-NAME>
```

### 2️ Benötigte Bibliotheken installieren
```bash
pip install -r requirements.txt
```

### 3️ Notebook starten
```bash
jupyter notebook
```

## Ausführung des Trainings
- Das Training erfolgt im Notebook `flappy.ipynb`.  
- Die Umgebung wird alle 10 Episoden visuell angezeigt.  
- Alle 500 Episoden wird das Modell automatisch gespeichert (`policy_net_epX.pth`).  
- Der Agent nutzt **ε-greedy**, wobei ε von 1.0 auf 0.05 abnimmt.

## Visualisierungen
Das Notebook erstellt automatisch verschiedene Diagramme:
- **Reward-Kurve** (Gesamt-Reward pro Episode)  
- **Moving Average** (geglättete Rewards über 50 Episoden)  
- **Histogramm der Rewards** (Verteilung der Belohnungen)  
- **Durchschnittlicher vs. Maximaler Reward** (Lernfortschritt im Verlauf)

Diese Plots sind auch im **Projektbericht** enthalten und dienen zur Bewertung des Trainings.

## Theorie
- **Zustandsraum:**  
  1. Vertikale Position des Vogels  
  2. Vertikale Geschwindigkeit  
  3. Horizontale Distanz zur nächsten Pipe  
  4. Differenz zwischen Vogelposition und Lückenmitte  

- **Aktionsraum:**  
  - `0` = nichts tun  
  - `1` = fliegen  

- **Reward-System:**  
  - +10 für jede durchflogene Pipe  
  - Negative Belohnung bei Kollision  
  - Zusätzliche Belohnung für zentrierte Flugbahn  

Das Training basiert auf dem **klassischen DQN-Ansatz (Mnih et al., 2015)** mit Replay Buffer, Target Network und der Bellman-Gleichung.

## Ergebnisse und Ausblick
- Der Agent konnte lernen, Pipes zu passieren und längere Episoden zu überleben.  
- Die Visualisierungen zeigen eine deutliche Leistungssteigerung.  
- Zukünftige Verbesserungen könnten **Double-DQN**, **Dueling-DQN** oder **Prioritized Experience Replay** sein, um Stabilität und Performance weiter zu erhöhen.
