# Advanced Tips and Tricks for SolarWinds Orion Dashboards

1. **Leverage Custom Properties for Dynamic Filtering**
   - Use custom properties (e.g., Location, Department, or Application) to group and filter data dynamically. Assign these properties to nodes, applications, or other entities, then use them in dashboard widgets to create tailored views.
   - Example: Create a custom property like "Site" and filter a widget to show only nodes from a specific site using SWQL (SolarWinds Query Language) queries.

2. **Master SWQL for Custom Widgets**
   - Write SWQL queries to pull specific data into modern dashboard widgets (e.g., Table or KPI widgets). Unlike SQL, SWQL is optimized for Orion’s database schema and supports relationships between entities.
   - Example: `SELECT N.Caption, N.Status FROM Orion.Nodes N WHERE N.CustomProperties.Department = 'Finance'` to display Finance department nodes.

3. **Optimize Widget Layout with Grid-Based Design**
   - In modern dashboards, use the grid-based layout to maximize screen real estate. Drag and resize widgets to fit more information without clutter, ensuring key metrics are immediately visible.
   - Tip: Place high-priority KPIs at the top and detailed tables/charts lower on the dashboard.

4. **Use PerfStack Integration for Real-Time Analysis**
   - Embed Performance Analysis (PerfStack) projects into dashboards to correlate metrics across nodes, applications, and volumes in real time. Add a PerfStack widget and link it to a saved project for instant troubleshooting views.
   - Example: Combine CPU, memory, and network traffic for a critical server in one widget.

5. **Customize Refresh Rates for Performance**
   - Adjust widget refresh intervals in modern dashboards to balance data freshness and system performance. Set critical widgets (e.g., alerts) to refresh every 10-15 seconds and less urgent ones (e.g., historical trends) to 60+ seconds.
   - How: Edit the widget, toggle "Custom refresh rate" in the Presentation section, and specify the interval.

6. **Build Application-Specific Dashboards**
   - Combine multiple components (e.g., IIS, SQL, and Orion services) into a single dashboard using AppInsight templates and custom SWQL queries. This provides a cohesive view of multi-tier applications.
   - Tip: Use the Visual Query Builder to simplify joining related entities without deep SWQL knowledge.

7. **Implement Account and View Limitations**
   - Apply account or view limitations to filter dashboard data based on user roles. This reduces noise and ensures users see only relevant information.
   - How: Go to Settings > Manage Accounts > Edit User, and set limitations under "Account Limitations."

8. **Clone and Modify Existing Dashboards**
   - Save time by duplicating built-in dashboards (e.g., Network Summary) and tweaking them to your needs. Adjust widgets, filters, or layouts instead of starting from scratch.
   - How: In Manage Dashboards, select a dashboard, click "Duplicate," and edit the clone.

9. **Add External Links for Contextual Data**
   - Enhance dashboards with hyperlinks to external tools or documentation. Add these as custom HTML widgets or menu bar items under My Dashboards > Configure.
   - Example: Link to a ticketing system like ServiceNow with a URL parameter for incident numbers.

10. **Utilize Intelligent Maps**
    - Embed Intelligent Maps to visualize network topology or group status dynamically. Customize maps with custom properties like Latitude and Longitude for geographic views.
    - Tip: Use the Worldwide Map widget and enable group display for a high-level status overview.

11. **Create KPI Widgets for Quick Insights**
    - Use KPI widgets in modern dashboards to highlight critical metrics (e.g., total down nodes, average response time). Pair with thresholds to color-code status (green, yellow, red).
    - Example: Show "Number of Active Alerts" with a SWQL query like `SELECT COUNT(*) AS ActiveAlerts FROM Orion.AlertObjects WHERE AlertActive IS NOT NULL`.

12. **Group and Aggregate Data Effectively**
    - In table widgets, use grouping and aggregation (e.g., Count, Average, Max) to summarize data. This is especially useful for large environments.
    - Example: Group nodes by status and count them with `SELECT Status, COUNT(*) AS NodeCount FROM Orion.Nodes GROUP BY Status`.

13. **Export and Share Dashboards**
    - Export custom dashboards as JSON files to share with colleagues or the THWACK community. Import dashboards from THWACK to adopt advanced setups quickly.
    - How: Go to Manage Dashboards, select a dashboard, and use the Export/Import options.

14. **Optimize for Mobile Viewing**
    - Design dashboards with mobile access in mind by keeping widgets compact and prioritizing vertical stacking. Test layouts in the SolarWinds Platform Web Console’s mobile view.

15. **Use Custom HTML for Advanced Formatting**
    - Add custom HTML widgets to display richly formatted text, embedded images, or scripts. This is ideal for headers, instructions, or branding.
    - Example: `<h2 style="color: #FF5733;">Critical Systems Overview</h2>` for a styled title.

16. **Set Visibility for Collaboration**
    - Make dashboards public or assign them to specific users/groups for team collaboration. By default, new dashboards are private—adjust this in the dashboard settings.
    - How: Edit the dashboard and change "Visibility" to "Public" or specific accounts.

17. **Monitor Hardware Health in Dashboards**
    - Add hardware health widgets to track sensors (e.g., temperature, fan speed) across devices. Filter by device type or location using custom properties for focused views.

18. **Balance Polling Load**
    - If dashboards load slowly, check polling engine distribution. Assign nodes to specific polling engines under Settings > Polling Engines to optimize performance.

19. **Incorporate NetPath for User Experience**
    - Add NetPath widgets to visualize network paths and latency from an end-user perspective. Customize queries to focus on internal or external services.
    - Example: Adapt a community query from THWACK for your specific paths.

20. **Test and Iterate with Feedback**
    - Regularly review dashboard usage with your team and refine based on feedback. Use the "Preview" mode while editing to test layouts before saving.
