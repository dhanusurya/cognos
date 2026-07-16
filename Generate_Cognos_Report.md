# Generating Reports in IBM Cognos Analytics

> **Applies to:** IBM Cognos Analytics 12.1.x (latest: 12.1.3 — June 2026)

----

## Overview

IBM Cognos Analytics — Reporting is a web-based report authoring tool that professional report authors and developers use to build sophisticated reports against multiple databases. This document covers the standard report generation workflow and highlights the latest capabilities introduced in Cognos Analytics 12.1.x.

----

## Prerequisites

Before generating a report, ensure the following:

- You have the **Authors** role or equivalent permissions to create and save reports.
- A suitable **data source** is available — either a **data module** or a **Framework Manager package**.
  > **Note:** OLAP and DMR packages are not supported for AI-assisted report generation (12.1.3+).
- Your browser session remains active during report generation.
- If using AI-assisted generation, the data source must be **indexed for AI**.
  > **Tip:** To index a data source, right-click its parent folder and select **Include for AI**.

----

## Method 1 — Standard Report Authoring

### Step 1 — Open Report Studio

**1.** Log in to IBM Cognos Analytics.

**2.** From the navigation menu, click **New** and select **Report**.

**3.** On the **Create a report** page, choose a template or theme.

> **12.1.1 update:** The Create a report page now shows only **Report** templates by default. Active Report templates are hidden unless you use the **Filter** icon to change the view. Your filter preference is saved between sessions.

### Step 2 — Select a Data Source

**4.** Select a **data module** or **Framework Manager package** as your data source.

**5.** Click **Open** to load the source into the authoring canvas.

### Step 3 — Add Data to the Report

**6.** From the **Sources** pane, drag and drop data items onto the report canvas.

**7.** Choose the appropriate report container for your data:

| Container | Best for |
|---|---|
| **List** | Tabular, row-by-row data |
| **Crosstab** | Multi-dimensional summaries |
| **Visualization** | Charts, graphs, and visual analysis |
| **Data table** | Structured tabular data with expandable rows |

### Step 4 — Apply Filters and Prompts

**8.** To filter data, create a **detail or summary filter** from the report toolbar or the query properties.

**9.** To add prompts, use **Build prompt page** or create parameters directly in the report page.

#### Automatic Relative Date Filtering *(New in 12.1.3)*

As of 12.1.3, you can apply **dynamic, time-based filters** that adjust automatically based on the current date — no manual updates required.

- Preset options include: **Year-to-Date**, **Quarter-to-Date**, **Month-to-Date**
- Supports flexible relative ranges configurable by direction, value, and time unit
- Supported for both **relational** and **hierarchical** data sources
- **Important:** For hierarchical data sources, this feature applies to newly created reports only.

### Step 5 — Configure Visualizations

**10.** For chart-based reports, select a visualization type from the **Visualizations** panel.

**11.** To add extra data values to tooltips in 11.1 visualizations *(New in 12.1.3)*:
- Drag and drop data items from your data source into the **Tooltip Values** field in the Data pane.
- Note: Tooltip values are not supported in Area, Bullet, River, Smooth area, Step area, or Schematics charts.

**12.** For crosstab reports, enable **interactive hierarchy navigation** *(New in 12.1.3)*:
- In the **Properties** panel, activate **Enable hierarchy expansion**.
- Set the **Rows per Page** property to an appropriate row count.
- Configure the initial display state to **Expanded** or **Collapsed**.
- Users can click the **Expand** / **Collapse** icons at runtime to navigate row hierarchies without extra server rendering.

### Step 6 — Apply a Conditional Palette *(New in 12.1.3)*

You can create a **Simple Conditional Palette** for 11.1 visualizations to differentiate data items with colours based on conditions.

> **Note:** Conditional palettes work only in reports run as **HTML**. A palette is removed if you convert its visualization to a different type.

### Step 7 — Run the Report

**13.** Click **Run** in the toolbar and select the desired output format:

| Output Format | Notes |
|---|---|
| **HTML** | Default interactive format; supports drill-through and prompts |
| **PDF** | Fixed-layout output; suitable for printing and distribution |
| **Excel** | Tabular data export |
| **CSV** | Flat data export; run options now configurable per report *(12.1.0+)* |
| **Markdown** | New in 12.1.3 — see below |

**14.** Respond to any prompts that appear and click **Finish** to generate the output.

----

## Method 2 — AI-Assisted Report Generation *(New in 12.1.3 — Preview)*

As of Cognos Analytics 12.1.3, you can generate a complete report by describing it in plain language.

### How It Works

**1.** Open any supported perspective in Cognos Analytics.

**2.** Describe the report you want — for example:
> *"Create a sales performance report by region and product line"*
> *"Show top 10 products by revenue for last quarter"*

**3.** Cognos Analytics interprets your request and generates the report using an available indexed data source. The generated report includes titles, summaries, KPIs, charts, and visualizations relevant to your request.

**4.** When generation completes, the report opens in **authoring view** for review and refinement using standard authoring tools.

### Requirements

| Requirement | Detail |
|---|---|
| Data source | Data module or Framework Manager package only (OLAP/DMR not supported) |
| Permissions | Access to the data source; create and edit report permissions |
| Browser session | Must remain active during generation |
| AI indexing | Data source must be indexed for AI — right-click parent folder → **Include for AI** |

### Query Agent *(Preview)*

As of 12.1.3, **Query Agent** allows you to interact with your data using natural language without writing SQL or building queries manually.

- Ask questions such as: *"What were the top 10 products by sales last year?"*
- The agent remembers conversation context for follow-up questions.
- Works with available reports, dashboards, and data modules.
- Open Query Agent and type your question — the more specific, the better the results.

----

## Output Format: Markdown *(New in 12.1.3)*

As of 12.1.3, reports can be rendered in **Markdown format** for use in AI workflows, documentation pipelines, and simplified sharing.

### How to Render a Report as Markdown

- **Interactive:** In Report Studio, select **Markdown** as the output format in the toolbar.
- **Background/Scheduled:** Configure the report output format as Markdown in the schedule or job settings.

> **Prerequisite:** You must have the `canGenerateMarkdownOutput` capability.
> **Important:** Markdown output is **not supported** in the classic viewer.

### Known Limitations

| Limitation | Workaround |
|---|---|
| Filter criteria not shown in output | Add filter values to the report title |
| Prompt controls not visible | Include prompt values in report headers |
| Drill-through links appear as plain text | Use HTML or PDF for drill-through |
| Nested list structures may flatten | Use flat lists or crosstabs instead |
| Summary rows and subtotals not rendered | Calculate aggregations in the query |
| Grouping column values show only in first row | Remove list grouping for complete data |

----

## Performance: Master-Detail Concurrent Execution *(New in 12.1.3)*

For list reports with **master-detail relationships**, concurrent query execution can speed up report delivery by up to **7–8 times**.

This feature is **disabled by default**. To enable it, an administrator must configure `rsvpproperties.xml`:

```xml
<structure>
    <property>concurrentDetailExecution</property>
    <value type="long">1</value>
</structure>
<structure>
    <property>concurrentDetailWindowSize</property>
    <value type="long">8</value>
</structure>
```

| Property | Description |
|---|---|
| `concurrentDetailExecution` | Set to `1` to enable parallel detail query execution |
| `concurrentDetailWindowSize` | Number of detail queries to run simultaneously (must be > 1) |

----

## Scheduling a Report

**1.** Navigate to the report in **Team content** or **My content**.

**2.** Click the **three dots (⋮)** action menu next to the report name and select **Properties**.

**3.** In the Properties panel, go to the **Schedule** tab and click **New schedule** or **Edit**.

**4.** Configure the frequency, format, and delivery options.

**5.** Click **Save**.

> **12.1.3 — Auto-Disabled Schedules:** If a scheduled report fails repeatedly, the system can automatically disable it after a configurable number of consecutive failures. See [Auto-Disabled Report Schedules](./Auto_Disabled_Report_Schedules.md) for details.

----

## Sharing and Distributing Reports

- **Share from the canvas:** Use the **Share** button to generate a shareable link or embed code.
- **Auto-refresh shared reports** *(12.1.1+)*: Enable the **Refresh Time** toggle in the Share window to configure automatic refresh intervals (in seconds, minutes, or hours).
- **Email delivery:** Configure SMTP settings under **Manage > Configuration** to enable report delivery by email.
- **Export to CSV:** As of 12.1.1, users can export visualization data directly to a `.csv` file if the author has enabled **Allow users access to data** under **Properties > Advanced**.

----

## Questions?

Contact the [#sos-compliance-reporting Slack channel](https://ibm-sos.slack.com/archives/C01MUGFGLEN).
