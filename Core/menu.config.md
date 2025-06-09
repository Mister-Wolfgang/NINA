# Menu Configuration P.R.I.M.A.
*Auto-génération menu dynamique*

## 🔧 **Structure**
```json
{
  "categories": {
    "dev": {"icon": "💻", "range": [1,5], "color": "blue"},
    "manage": {"icon": "📊", "range": [6,8], "color": "green"}, 
    "creative": {"icon": "🎨", "range": [9,12], "color": "purple"},
    "social": {"icon": "🎮", "range": [13,16], "color": "orange"},
    "hybrid": {"icon": "🔄", "range": [17,19], "color": "yellow"},
    "system": {"icon": "⚙️", "range": [20,20], "color": "red"}
  }
}
```

## ⚡ **Auto-Discovery**
- Scan `./*/` pour `.instructions.md`
- Map fichiers → numéros séquentiels
- Groupe par cortex
- Generate menu formaté

## 🎯 **Templates**
**Standard** : `{num}. [{emoji} {name}] - {description}`  
**Compact** : `{emoji}{name}({num})`  
**Debug** : `{path} → {num} ({status})`
