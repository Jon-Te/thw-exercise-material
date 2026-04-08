# THW Materialanforderung - Programmier-Workshop

## Projektübersicht
Ihr entwickelt eine Webseite für das THW (Technisches Hilfswerk), mit der Helferinnen und Helfer Materialien für Einsätze anfordern können.

## Aufgaben

### 📋 Aufgabe 1: Eingabefelder hinzufügen
**Datei:** `src/app/app.html`

**Ziel:** Erstelle ein Formular, damit Helferinnen und Helfer ihre Daten eingeben können.

**Anforderungen:**
- Eingabefeld für den Namen des Anfragers (Text)
- Eingabefeld für die E-Mail-Adresse (Email)
- Dropdown für die Abteilung mit den Optionen: "Bergung", "Fachgruppe Räumen", "Fachgruppe Wasserschaden"
- Dropdown für die Dringlichkeit mit den Optionen: "Normal", "Hoch", "Sehr hoch"

**Beispiel für ein Textfeld:**
```html
<div class="form-group">
  <label for="example">Beispiel-Label:</label>
  <input type="text" id="example" [(ngModel)]="exampleVariable" placeholder="Beispiel-Text">
</div>
```

**Beispiel für ein Dropdown:**
```html
<div class="form-group">
  <label for="color">Farbe:</label>
  <select id="color" [(ngModel)]="selectedColor">
    <option value="">Bitte wählen...</option>
    <option value="rot">Rot</option>
    <option value="blau">Blau</option>
  </select>
</div>
```

**Hinweise:**
- Die Variablen `requesterName`, `email`, `department`, `priority` sind bereits in der TypeScript-Datei definiert
- Verwende die passenden input-Typen (text, email)

### 🔘 Aufgabe 2: Submit-Button hinzufügen
**Datei:** `src/app/app.html`

**Ziel:** Füge einen Button hinzu, mit dem die Anfrage gesendet werden kann.

**Anforderungen:**
- Button mit dem Text "Anfrage senden"
- Beim Klick soll die Methode `submitRequest()` aufgerufen werden

**Beispiel für einen Button:**
```html
<button class="example-btn" (click)="exampleMethod()">
  Beispiel-Button
</button>
```

**Hinweise:**
- Die CSS-Klasse `submit-btn` ist bereits definiert
- Die Methode `submitRequest()` existiert bereits

### 📊 Aufgabe 3: Anfragen-Liste anzeigen
**Datei:** `src/app/app.html`

**Ziel:** Zeige alle gesendeten Anfragen in einer Liste an.

**Anforderungen:**
- Durchlaufe das Array `submittedRequests` und zeige für jede Anfrage:
  - Name des Anfragenden als Überschrift
  - Abteilung
  - Anzahl der ausgewählten Materialien
  - Status der Anfrage
  - Dringlichkeit

**Beispiel für eine Liste:**
```html
<div class="item" *ngFor="let person of people">
  <h3>{{person.name}}</h3>
  <p><strong>Alter:</strong> {{person.age}}</p>
  <p><strong>Hobbys:</strong> {{person.hobbies.length}} Stück</p>
</div>
```

**Hinweise:**
- Verwende die CSS-Klasse `request-item` für jeden Eintrag
- Das Array heißt `submittedRequests`
- Für die Materialien-Anzahl verwende `materials.length`

### ⚡ Aufgabe 4: Material auswählen/abwählen
**Datei:** `src/app/app.ts`
**Wo:** In der Methode `toggleMaterial()`

**Ziel:** Implementiere die Logik zum Hinzufügen und Entfernen von Materialien.

**Anforderungen:**
- Wenn das Material bereits ausgewählt ist, entferne es aus `selectedMaterials`
- Wenn das Material noch nicht ausgewählt ist, füge es zu `selectedMaterials` hinzu

**Beispiel für Array-Operationen:**
```typescript
// Prüfen ob ein Element im Array ist:
if (this.fruits.includes(apple)) {
  // Element ist bereits da
}

// Element aus Array entfernen:
this.fruits = this.fruits.filter(fruit => fruit.id !== apple.id);

// Element zum Array hinzufügen:
this.fruits.push(apple);
```

**Hinweise:**
- Verwende die `id` zum Vergleichen von Materialien
- Das Array `selectedMaterials` ist bereits definiert

### 📤 Aufgabe 5: Anfrage senden (20 Minuten)
**Datei:** `src/app/app.ts`
**Wo:** In der Methode `submitRequest()`

**Ziel:** Implementiere die Logik zum Senden einer Materialanfrage.

**Anforderungen:**
- Validiere, dass alle Pflichtfelder ausgefüllt sind
- Validiere, dass mindestens ein Material ausgewählt wurde
- Erstelle eine neue Anfrage mit allen Daten
- Füge die Anfrage zur Liste `submittedRequests` hinzu
- Setze das Formular zurück
- Zeige eine Erfolgsmeldung an

**Beispiel für Validierung:**
```typescript
if (!this.username || !this.password) {
  alert('Bitte alle Felder ausfüllen!');
  return;
}

if (this.selectedItems.length === 0) {
  alert('Bitte mindestens ein Element auswählen!');
  return;
}
```

**Beispiel für Objekt erstellen:**
```typescript
const newUser = {
  id: this.users.length + 1,
  name: this.username,
  createdAt: new Date(),
  active: true
};

this.users.push(newUser);
```

**Hinweise:**
- Verwende `alert()` für Meldungen
- Der Status neuer Anfragen ist "Offen"
- Die Methode `resetForm()` existiert bereits
- Das Interface `MaterialRequest` ist bereits definiert

## 🎯 Bonus-Aufgaben (für schnelle Schüler)

### Bonus 1: Anfrage-Zähler
**Ziel:** Zeige die Anzahl der offenen Anfragen im Header an.
**Hinweis:** Filtere `submittedRequests` nach Status "Offen"

### Bonus 2: Materialien nach Kategorie filtern
**Ziel:** Füge Buttons hinzu, um nur bestimmte Material-Kategorien anzuzeigen.
**Hinweis:** Verwende eine neue Variable `selectedCategory` und filtere die Materialien

### Bonus 3: Anfrage löschen
**Ziel:** Füge einen "Löschen"-Button zu jeder Anfrage hinzu.
**Hinweis:** Verwende `splice()` oder `filter()` um eine Anfrage zu entfernen

## 🚀 Projekt starten
```bash
npm start
```
Die Webseite ist dann unter http://localhost:4200 erreichbar.

## 💡 Tipps
- Nutzt die Browser-Entwicklertools (F12) um Fehler zu finden
- Die Console zeigt hilfreiche Nachrichten an
- Schaut euch die bereits vorhandenen Variablen in `app.ts` an
- Bei Problemen fragt euren Workshop-Leiter!

## 📱 Erwartetes Ergebnis
Nach Abschluss aller Aufgaben habt ihr eine funktionsfähige THW-Materialanforderungs-Webseite, bei der:
- Helfer ihre Daten eingeben können
- Material aus einer Liste auswählen können
- Anfragen gesendet werden können
- Alle Anfragen in einer Übersicht angezeigt werden
