# 🎪 Festa Major Blancs i Blaus · Granollers 2026

Web app completa per visualitzar el programa de la Festa Major (22-30 d'agost 2026) i apuntar-se a les activitats.

**Stack**: HTML + CSS + JS vanilla | Backend: Supabase (PostgreSQL) | Deploy: GitHub Pages

---

## 📋 Continguts

- `index.html` — App single-page completa (responsive, colors blanc i blau)
- `schema.sql` — SQL per crear taules i inserir totes les activitats
- `README.md` — Instruccions de setup (aquest arxiu)

---

## 🚀 Setup en 6 passos

### 1️⃣ Crear projecte a Supabase

1. Anar a [supabase.com](https://supabase.com)
2. Crear un compte (o fer login si ja en tens)
3. Crear un projecte nou:
   - Click en "New project"
   - Triar un nom (ej: "festa-major-granollers")
   - Establir contrasenya de la BD (guardada segura)
   - Triar regió (Europa recomanada)
   - Esperar ~1-2 minuts que es provisioni

### 2️⃣ Executar el SQL (crear taules + dades)

1. A la consola de Supabase, anar a **SQL Editor** (esquerra lateral)
2. Click en **"New Query"** o **"New SQL snippet"**
3. **Copiar tot el contingut** del fitxer `schema.sql` (aquest repositori)
4. **Enganxar** a l'editor de SQL de Supabase
5. Click en **"Run"** (el botó verd)
   - Hauria de crear les taules `activitats` i `inscripcions`, afegir índexs, habilitar RLS i inserir totes les activitats
   - Esperar que finalitzi (pots veure el progres a la part inferior)

**Si hi ha errors**, revisa que:
- No hi hagi caràcters mal codificats (assegura't que `schema.sql` està en UTF-8)
- Si el SQL falla a meitat, proba buidant la BD i repetint: `DROP TABLE IF EXISTS inscripcions CASCADE; DROP TABLE IF EXISTS activitats CASCADE;` (execute) i repeteix el SQL complet

### 3️⃣ Obtenir URL i API Key de Supabase

1. A Supabase, anar a **Settings** (icona d'engranatge a la part inferior esquerra)
2. A la secció **"API"** (lateral esquerre dins de Settings), trobaràs:
   - **Project URL** — copiar aquest valor (algo com `https://xxxxxxxxxxxx.supabase.co`)
   - **API Keys** → buscar la clau **"anon"** (públic) — copiar-la

**Guarda aquests dos valors** en un lloc segur (els usaràs al següent pas).

### 4️⃣ Configurar index.html

1. Obrir `index.html` amb un editor de text (VS Code, Sublime, Notepad++, etc.)
2. Buscar les línies (prop del final, dins del `<script>`):
   ```javascript
   const SUPABASE_URL = 'TU_SUPABASE_URL';
   const SUPABASE_KEY = 'TU_SUPABASE_ANON_KEY';
   ```
3. Substituir els valors placeholders:
   - `'TU_SUPABASE_URL'` → `'https://xxxxxxxxxxxx.supabase.co'`
   - `'TU_SUPABASE_ANON_KEY'` → `'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...'` (la clau "anon" de Supabase)
4. **Guardar** el fitxer

Exemple:
```javascript
const SUPABASE_URL = 'https://abcdefgh.supabase.co';
const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFiY2RlZmdoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MTAwMDAwMDALCJleHAiOjE4Mjk5OTk5OTl9.Xxxxxxxxxxxxxxxxxx_xXxXxXxX';
```

### 5️⃣ Provar en local

1. **Opció A** — Obrir directament:
   - Fer doble-click a `index.html` (s'obrirà al navegador)
   - Comprovar que es carreguen les activitats i la llista de dies
   
2. **Opció B** — Servidor estàtic (recomanat si hi ha problemes CORS):
   ```bash
   # Si tens Python 3 instal·lat:
   cd /Users/fran/Desktop/FM\ GRANOLLERS\ 2026
   python3 -m http.server 8000
   ```
   Després anar a `http://localhost:8000` al navegador

**Tests ràpids**:
- ✅ Es veuen els tabs dels 9 dies?
- ✅ Es carreguen les activitats de cada dia?
- ✅ Pots fer click a "Apunta't" i obrir el modal?
- ✅ Pots entrar un nom i inscriure't?
- ✅ Apareix el nom a la llista de participants?
- ✅ Pots eliminar la inscripció fent click a la "✕"?

Si alguna cosa no funciona:
- Obrir la consola del navegador (F12 → Console)
- Buscar errors en vermell (normalment seran errors de connexió a Supabase)
- Verifica que `SUPABASE_URL` i `SUPABASE_KEY` són correctes

### 6️⃣ Publicar a GitHub Pages

#### Opció A: Crear repo nou des de zero

1. Anar a [github.com](https://github.com) i criar un repositori nou:
   - Nom: `festa-major-granollers` (o el que prefereixis)
   - Privat o públic (públic si vols que sigui accessible)
   - Click "Create repository"

2. Clonar el repo al teu ordinador:
   ```bash
   git clone https://github.com/TU_USUARIO/festa-major-granollers.git
   cd festa-major-granollers
   ```

3. Copiar els fitxers:
   ```bash
   cp /Users/fran/Desktop/FM\ GRANOLLERS\ 2026/index.html .
   cp /Users/fran/Desktop/FM\ GRANOLLERS\ 2026/schema.sql .
   cp /Users/fran/Desktop/FM\ GRANOLLERS\ 2026/README.md .
   ```

4. Cometre i pujar:
   ```bash
   git add .
   git commit -m "Initial commit: Festa Major app"
   git push origin main
   ```

#### Opció B: Usar web de GitHub directament

1. Anar al repositori a GitHub
2. Click en "Add file" → "Upload files"
3. Seleccionar `index.html`, `schema.sql`, i `README.md`
4. Click "Commit changes"

#### Activar GitHub Pages

1. Al repositori, anar a **Settings** (pestanya dalt a la dreta)
2. Lateral esquerre → **Pages**
3. Sota "Build and deployment":
   - **Source** → seleccionar "Deploy from a branch"
   - **Branch** → seleccionar `main` i carpeta `/root`
   - Click "Save"
4. Esperar 1-2 minuts que es despliegui (hauries de veure un link verd: `https://teusuario.github.io/festa-major-granollers/`)

5. **Provar**: obrir la URL al navegador — hauria de funcionar exactament igual que en local

---

## 📝 Manteniment

### Afegir/editar activitats

Les activitats es troben a la taula `activitats` de Supabase. Pots:

1. **Via SQL Editor** (avançat):
   - Anar a SQL Editor → New Query
   - Exemple: afegir una activitat nova:
     ```sql
     INSERT INTO activitats (dia, hora, hora_sort, nom, lloc, organitzador, preu, descripcio) 
     VALUES ('Dissabte 22', '14.30h', '14:30', 'Nova activitat', 'Plaça Test', 'Organitzador', '5€', 'Descripció');
     ```

2. **Via Table Editor** (gràfic):
   - Anar a **Table Editor** (lateral esquerre)
   - Seleccionar taula `activitats`
   - Click en "Insert row" i omplir els camps

### Suprimir inscripcions

La taula `inscripcions` conté les inscripcions. Per netejar:
- SQL Editor: `DELETE FROM inscripcions WHERE activitat_id = ?;`
- Taula Editor: seleccionar files i eliminar

### Contrasenya de la BD

⚠️ **Important**: La clau "anon" que has configurada a `index.html` és **pública** (no és secret). Qualsevol pot veure el codi font i accedir a la BD. Això està bé per a una app de festa major (la gent pot veure i inscriure's), però:

- **No guardar secrets de la BD** en el codi frontend (no hi ha passwords o dades sensibles)
- **No fer queries sensibles** (ex: no accedir a taules d'administració)
- Si després vols restringir accés, implementa autenticació via Supabase Auth

---

## 🎨 Personalitzar disseny

Tots els colors i tipografies estan a la secció `:root` del `<style>` dins de `index.html`:

```css
:root {
  --color-blanc: #FFFFFF;
  --color-blau: #003DA5;
  --color-blau-clar: #1A5FCC;
  --color-gris: #F5F5F5;
  --color-accent: #FFD700;
}
```

Pots canviar aquests valors per a altres colors.

---

## 🛠️ Troubleshooting

| Problema | Solució |
|----------|---------|
| "Error al cargar las actividades" | Verifica que `SUPABASE_URL` i `SUPABASE_KEY` són correctes. Comprova la consola del navegador (F12) |
| No apareixen activitats | A Supabase, anar a Table Editor → `activitats` → verificar que hi ha dades |
| No puc apuntar-me | Verifica les policies RLS a Supabase (Settings → Policy — hauria de permetre INSERT/DELETE a anon) |
| No funciona en GitHub Pages | Assegura't que `index.html` és l'arxiu correcte i que es troba a l'arrel del repositori |
| CORS error | Supabase permet CORS per defecte amb REST API. Si persisteix, comprova que la URL de Supabase és correcta |

---

## 📱 Responsive i navegadors

- ✅ Funciona bé en mòbil (disseny mobile-first)
- ✅ Compatible amb Chrome, Firefox, Safari, Edge
- ✅ No requereix JavaScript compilat (vanilla JS)

---

## 🎉 Ja està!

Amb això ja hauries de tenir la web app funcionant en viu. Diverteix-te amb la Festa Major Blancs i Blaus! 🎪

---

**Preguntes o problemes?** Revisa els comentaris al codi de `index.html` i la consola del navegador (F12 → Console) per a més detalls.
