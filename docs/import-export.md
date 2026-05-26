
# ⇪ Import / Export

DashForge supports dashboard and asset import/export.

This system allows users to:
- backup telemetry setups
- share dashboards
- transfer layouts between devices
- distribute community templates
- restore complete cockpit configurations

<br>

---

<br>

## Exporting Dashboards

To export a dashboard:

1. Open the Dashboard library
2. Select a dashboard
3. Click on Export icon

DashForge generates an export package containing:
- dashboard layout
- widget configuration
- styles and themes
- associated assets

<br>

## Export Format

Dashboards are exported as JSON-based packages.

Example structure:

{
  "name": "Night Drift Setup",
  "theme": "amoled",
  "widgets": [
    {
      "type": "speedometer",
      "x": 120,
      "y": 80
    }
  ]
}

<br>

## What Is Included

Dashboard exports may contain:

| Item | Included |
|---|---|
| Widget layout | Yes |
| Widget styles | Yes |
| Dashboard theme | Yes |
| Premium widget references | Yes |
| Images / assets | Optional |
| Replay files | No |

<br>

---

<br>

## Importing Dashboards

To import a dashboard:

1. Open the Dashboard library
2. Choose Import
3. Select a compatible dashboard file

Imported dashboards automatically restore:
- layout
- widget positions
- sizing
- theme
- styles
- telemetry bindings

<br>

---

<br>

## Dashboard Compatibility

Older dashboard versions may not support:
- newer widgets
- premium widgets
- future telemetry systems

DashForge attempts to preserve unsupported widgets when possible.

<br>

## Premium Widgets

Some imported dashboards may require:
- Premium Widgets Pack
- specific telemetry fields
- compatible game profiles

<br>

## Assets

Some dashboards may include:
- overlay images
- background graphics
- custom UI assets

When sharing dashboards, keep:
- JSON files
- asset folders

together.

<br>

---

<br>

## Community Templates

Community dashboard templates are available in:

    /templates/dashboards

Users can:
- share racing HUDs
- create themed dashboards
- distribute telemetry setups
- build game-specific cockpit layouts

<br>

---

<br>

## Recommendations

For the best compatibility:

- export dashboards after major edits
- backup templates regularly
- test imported dashboards before competitive sessions
- keep game profiles updated

<br>

## Backup Recommendation

It is recommended to periodically backup:
- dashboards
- templates
- replay sessions
- custom game profiles

especially before updating the app.

<br>

---

<br>

## Future Improvements

Future DashForge versions may include:
- cloud sync
- dashboard marketplace
- online template sharing
- dashboard versioning
