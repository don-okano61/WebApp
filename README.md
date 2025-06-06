Hier ist eine **README.md**-Datei mit den **wichtigsten Korrekturen und Hinweisen**, die du in deinem Projekt beachten solltest:

```markdown
# Bewerbungsverwaltung – Flask & Frontend-Projekt

Dieses Projekt ist eine einfache Bewerbungsverwaltungs-App mit **Flask** als Backend und **HTML/CSS/JavaScript** als Frontend. 🚀

## 📂 Projektstruktur
```
bewerbungsverwaltung/
│── backend/
│   ├── __init__.py    # Flask Initialisierung
│   ├── app.py         # Hauptanwendung
│   ├── models.py      # Datenbankmodelle
│   ├── routes.py      # API-Endpunkte
│── frontend/
│   ├── index.html     # Web-Oberfläche
│   ├── styles.css     # Styling
│   ├── app.js         # Interaktivität
```

---

## 🔧 Wichtige Korrekturen

### ✅ **1️⃣ Sicherstellen, dass `__init__.py` existiert**
`backend/__init__.py` ist **erforderlich**, damit `backend` als **Python-Modul** erkannt wird. Falls es fehlt, erstelle es mit:
```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config["SQLALCHEMY_DATABASE_URI"] = "postgresql://USER:PASSWORD@localhost/bewerbungen_db"

db = SQLAlchemy(app)
```

### ✅ **2️⃣ Import in `routes.py` korrigieren**
Falls du Folgendes hattest:
```python
from models import Bewerbung  # ❌ Fehlerhaft
```
Ersetze es mit:
```python
from backend.models import Bewerbung  # ✅ Korrekt
```

### ✅ **3️⃣ Anwendungskontext für `db.create_all()`**
Falls du einen **Application Context Error** hattest:
```python
db.create_all()  # ❌ Fehlerhaft
```
Ersetze es durch:
```python
with app.app_context():
    db.create_all()  # ✅ Korrekt
```

### ✅ **4️⃣ Route für Startseite (`/`) hinzufügen**
Falls du eine **404-Fehlermeldung** für `http://127.0.0.1:5000` erhalten hast, ergänze `routes.py`:
```python
@api_bp.route("/", methods=["GET"])
def home():
    return "<h1>Willkommen zur Bewerbungsverwaltung!</h1><p>Diese API verwaltet Bewerbungen.</p>"
```

### ✅ **5️⃣ Projekt richtig starten**
Falls du `ModuleNotFoundError`-Fehler hattest, **wechsel zuerst ins Hauptverzeichnis**:
```bash
cd C:\Users\alojk\OneDrive\Desktop\Projekt\bewerbungsverwaltung
python -m backend.app
```
Falls das nicht funktioniert:
```bash
python backend/app.py
```

---

## 🚀 Projekt starten
1️⃣ Stelle sicher, dass du eine **virtuelle Umgebung** (`venv`) nutzt:
```bash
python -m venv venv
venv\Scripts\activate  # (Windows)
source venv/bin/activate  # (Mac/Linux)
```
2️⃣ Installiere die Abhängigkeiten:
```bash
pip install flask flask_sqlalchemy psycopg2
```
3️⃣ Starte die Anwendung:
```bash
python -m backend.app
```
4️⃣ Öffne den Browser:  
🔗 **[http://127.0.0.1:5000](http://127.0.0.1:5000)**  

---

## 🏆 Erweiterungen
✅ **Login-Funktion hinzufügen**  
✅ **Admin-Oberfläche für Bewerbungen**  
✅ **E-Mail-Benachrichtigungen nach Status-Änderung**  
