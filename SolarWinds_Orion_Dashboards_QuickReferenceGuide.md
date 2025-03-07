# SolarWinds Dashboards Quick Reference Guide

## Overview
SolarWinds dashboards display network, system, and application performance data in the Orion Web Console. There are two types:
- **Classic Dashboards (Views):** Traditional views for summary or detailed data (pre-2020.2).
- **Modern Dashboards:** Introduced in 2020.2, offering dynamic, widget-based layouts for high-level summaries.

Dashboards can include maps, charts, KPIs, tables, and more, customizable to your needs.

---

## Accessing Dashboards
1. **Log in** to the SolarWinds Orion Web Console.
2. Navigate to:
   - **Classic Dashboards:** `My Dashboards` or `Settings > All Settings > Manage Views`.
   - **Modern Dashboards:** `Settings > Manage Dashboards/Views`.

---

## Creating a Dashboard

### Classic Dashboard (View)
1. Go to `Settings > All Settings > Manage Views`.
2. Click **Add New View**.
3. Enter a **Name** and select a **View Type** (e.g., Summary or Detail).
4. Click **Submit**.
5. On the **Customize View** page:
   - Click **Add Widgets**.
   - Search and drag widgets (e.g., "All Nodes - Tree", "Map") to the layout.
   - Click **Done Adding Widgets > Done Editing**.
6. Assign to users via `My Dashboards > Configure` or user account settings.

### Modern Dashboard
1. Go to `Settings > Manage Dashboards/Views`.
2. Click **Add Modern Dashboard**.
3. Provide a **Name**. Check **Immediately open this dashboard** to edit now, or click **Create** to save an empty dashboard.
4. In **Edit Dashboard** mode:
   - Drag **"Drag to create a new widget"** to the layout.
   - Select widget type (e.g., KPI, Proportional, Table).
   - Configure data (see "Customizing Widgets" below).
   - Click **Finish Configuring**.
5. Click **Done Editing** to save.

---

## Customizing Dashboards

### Classic Dashboard
- **Edit Layout:** Open the dashboard, click the pencil icon, and adjust widgets.
- **Add Widgets:** Click **Add Widgets**, search (e.g., "Map" or "Custom HTML"), and drag to the page.
- **Filter Data:** Edit a widget, add a SQL filter (e.g., `WHERE Status = 1` for "Up" nodes).
- **Save:** Click **Done Editing**.

### Modern Dashboard
- **Edit Layout:** Click the pencil icon on the dashboard.
- **Resize/Move Widgets:** Drag the bottom-right corner to resize or the top-left handle to move.
- **Add Widgets:** Drag **"Drag to create a new widget"** and configure.
- **Clone Dashboard:** On `Manage Dashboards`, select a dashboard, click **Duplicate**, rename, and adjust.
- **Refresh Rate:** Default is 45 seconds. Admins can adjust globally (`Settings > Web Console Settings > Modern Widget Refresh`) or per widget (toggle "Custom refresh rate" in widget settings).

---

## Customizing Widgets

### Common Widget Types
- **KPI:** Displays a single metric (e.g., node count).
- **Proportional:** Shows data as pie charts, donut charts, or stacked bars.
- **Table:** Lists detailed data (e.g., node status).
- **Time Series:** Plots metrics over time (Modern Dashboards only).

### Classic Dashboard Widgets
1. Edit a widget (click **Edit**).
2. Examples:
   - **Map:** Select a Network Atlas map, set zoom %.
   - **All Nodes - Tree:** Group by up to 3 criteria (e.g., Vendor, Status).
   - **Custom HTML:** Add static text or links (HTTPS not supported).

### Modern Dashboard Widgets
1. Edit a widget (click three dots > **Edit Widget**).
2. Configure:
   - **Data Source:** Use SWQL queries (e.g., `SELECT COUNT(NodeID) AS UpNodes FROM Orion.Nodes WHERE Status = 1`) or the GUI selector.
   - **Filters:** Limit data (e.g., by group or custom property).
   - **Presentation:** Set title, colors, or refresh interval.
3. Click **Save Changes**.

---

## Managing Dashboards

### Assign to Users
- **Classic:** Edit user account (`Settings > Manage Accounts > Edit User`), set default menu bars under **Default Menu Bars and Views**.
- **Modern:** Share via `Manage Dashboards` (public or private settings).

### Import/Export (Modern Only)
- **Export:** On `Manage Dashboards`, select a dashboard, click **Export**, save the JSON file.
- **Import:** Click **Import**, upload a JSON file (e.g., from THWACK community).

### Delete
- Select the dashboard in `Manage Dashboards/Views`, click **Delete**.

---

## Tips & Tricks
- **Permissions:** Ensure "Manage Dashboards" or "Allow Administrator Rights" is enabled for full control.
- **SWQL:** Use SWQL Studio (https://github.com/solarwinds/OrionSDK/releases/tag/v3.2.0.50049) to test complex queries for Modern Dashboards.
- **Performance:** Limit widgets per dashboard to avoid slow load times.
- **NOC Mode:** Enable for full-screen, rotating views (`Customize Page > Enable NOC View` for Classic).
- **Browser Compatibility:** Modern Dashboards don’t support IE11; use Chrome, Firefox, or Edge.

---

## Example SWQL Queries (Modern Dashboards)
- **Nodes Up:** `SELECT COUNT(NodeID) AS UpNodes FROM Orion.Nodes WHERE Status = 1`
- **Nodes by Group:** `SELECT COUNT(n.NodeID) AS NodeCount, c.Name AS GroupName FROM Orion.Nodes n JOIN Orion.ContainerMembers cm ON n.NodeID = cm.MemberPrimaryID JOIN Orion.Container c ON cm.ContainerID = c.ContainerID WHERE c.Name = 'YourGroupName' GROUP BY c.Name`
- **Down Nodes:** `SELECT Caption, Status FROM Orion.Nodes WHERE Status = 2`

---

## References

- **THWACK Community:** (https://thwack.solarwinds.com/) The SolarWinds THWACK forum.

- **Video Content:** 
1. https://youtu.be/9T1VlIvAfdo?si=9oQLAgbS_Ap_ZoPZ
