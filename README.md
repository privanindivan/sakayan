# 🚌 PH Jeepney Route Mapper

Crowdsourced mapping tool for informal public transport routes in the Philippines.

## Two Versions

### 1. Clean View (`clean.html`)
- **Minimal map tiles** (CartoDB Positron - distraction-free)
- **ONLY shows contributed POIs** (no OSM clutter)
- Best for: Data entry, focused mapping
- Color: Purple/Blue theme

### 2. Full OSM View (`full.html`)
- **Standard OpenStreetMap tiles** (all default POIs visible)
- **Contributed POIs overlay** (yellow markers to stand out)
- Best for: Context, comparing with existing infrastructure
- Color: Red/Yellow theme

---

## Features

### ✅ Implemented
- **My Location Button** 📍
  - Click to get your current GPS location
  - Auto-center map on your position
  - Shows "You are here" marker
  - Works on mobile browsers

- **CRUD POIs** (Points of Interest)
  - Name, type (terminal/stop/landmark/transfer)
  - Notes, contributor name
  - Click map to add location
  - Delete from list view
  
- **Draw Custom Routes**
  - Select POIs in sequence (A→B→C)
  - **Auto-routing** (OSRM) - suggests road paths
  - **Custom mode** - straight lines with direction arrows
  - Toggle between auto/custom

- **Crowdsourced Data**
  - Anyone can add/edit/delete (no auth for prototype)
  - Contributor name tracked per POI/route
  - LocalStorage persistence

- **Export/Import**
  - JSON format
  - Statistics dashboard
  - Full data portability

### ❌ Not Included (Prototype)
- Real-time tracking
- Photo uploads
- User authentication
- Fare calculator
- Backend database (LocalStorage only)

---

## Quick Start

1. **Run local server:**
   ```bash
   cd jeepney-mapper
   python -m http.server 8000
   ```

2. **Open in browser:**
   - Clean view: http://localhost:8000/clean.html
   - Full OSM: http://localhost:8000/full.html

3. **Add POIs:**
   - Click map → Fill form → Save
   - Repeat for terminals, stops, landmarks

4. **Create routes:**
   - Switch to Routes tab
   - Click POIs in order
   - Toggle auto-routing on/off
   - Save with route name

5. **Export data:**
   - Export tab → Download JSON
   - Share with team or import elsewhere

---

## Data Structure

```json
{
  "pois": [
    {
      "id": 1234567890,
      "name": "SM North Terminal",
      "type": "terminal",
      "notes": "Main jeepney terminal",
      "contributor": "Juan Dela Cruz",
      "lat": 14.6565,
      "lng": 121.0297,
      "created": "2026-02-10T03:30:00.000Z"
    }
  ],
  "routes": [
    {
      "id": 9876543210,
      "name": "Quiapo - Cubao",
      "contributor": "Maria Santos",
      "pois": [1234567890, 2345678901],
      "created": "2026-02-10T03:35:00.000Z"
    }
  ]
}
```

---

## Tech Stack

- **Leaflet.js** - Map rendering
- **Leaflet Routing Machine** - OSRM integration
- **CartoDB Positron** - Minimal tiles (clean view)
- **OpenStreetMap** - Full tiles (full view)
- **LocalStorage** - Data persistence (prototype)

---

## Next Steps (For Production)

1. **Backend database** (Firebase/Supabase/PostgreSQL)
2. **Basic auth** (contributor accounts)
3. **Photo uploads** (POI documentation)
4. **Vehicle type categorization** (jeepney/tricycle/UV)
5. **Fare data** (optional calculator)
6. **API** (public data access)
7. **Mobile optimization** (PWA)

---

## Contributing

This is a **prototype**. For now, anyone can CRUD data freely.

**To share data:**
1. Export JSON from Export tab
2. Share file with collaborators
3. They import into their instance
4. Data merges (no conflict resolution yet)

---

## License

Open for public good. Map data © OpenStreetMap contributors.
