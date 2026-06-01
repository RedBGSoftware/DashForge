# DashForge Dashboards

Community and official dashboard packages for DashForge.

Each dashboard includes:
- a .dfdash package
- preview images
- Dashboard source
- optional assets


## Structure

```plaintext
dashboards/
├── index.json
│
├── initial-d-touge/
│   ├── initial-d-touge.dfdash
│   ├── preview.png
│   ├── README.md
│   └── package/
│       ├── manifest.json
│       ├── dashboard.json
│       └── assets/
│
└── neon-grid/
    ├── neon-grid.dfdash
    ├── .....
```


## index.json

index.json contains the dashboard catalog used by DashForge.

Example:

```json
[
  {
    "id": "initial-d-touge",
    "name": "Initial D Touge",
    "author": "RedBG",
    "version": "1.0.0",
    "type": "dashboard",
    "description": "Japanese mountain night telemetry dashboard.",
    "preview": "preview.png",
    "download": "initial-d-touge.dfdash",
    "premium": false,
    "minAppVersion": "1.0.0"
  }
]
```


## Dashboard Packages

.dfdash files are importable dashboard packages for DashForge.

They may contain:
- dashboard layouts
- themes
- assets

---

## Naming Conventions

Use lowercase kebab-case for:
- folders
- ids
- package names


Example:

```
initial-d-touge 
```

Not:
```
InitialDTouge 
```