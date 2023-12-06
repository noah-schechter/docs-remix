---
title: Import and export data
description: Data on Atlos is easily portable.
---

Data on Atlos is easily portable. Our goal is to support your investigations wherever they might go, not to lock you in.

## Data import
Researchers that have accumulated a large amount of data before beginning working on Atlos can import their data into Atlos. However, we recommend keeping your investigation on Atlos whenever possible. Our change-tracking and archival systems can’t be used on data that’s not yet in Atlos—the faster data is added to the platform, the faster we can assure its integrity. 

### How to import data
To import data:
1. Navigate to the **Projects** page.
2. Select the relevant project. 
3. Navigate to the **Manage** page and scroll to the **Bulk import** section at the bottom of the page. 
4. Click **Upload a file**. 
5. Click **Publish to Atlos** once Atlos has processed your CSV. 

See the [formatting](/docs/import-and-export-data#formatting-for-bulk-import) section below for a full explanation of acceptable CSV formats. Note that bulk import is accessible only to project owners and managers. 

### What is a CSV? 
Atlos uses CSVs to make the platform compatible with all spreadsheet software. CSVs standardize spreadsheet data as values separated by commas. 

For reference, we’ve included a spreadsheet and CSV representing the same data: 

_Spreadsheet_
{% table %}
* status
* description
* sensitive
---
* Unclaimed 
* Explosion along river
* Not Sensitive
---
* In Progress
* Explosion along road
* "Deleted by Source,Deceptive or Misleading"
{% /table %}

_CSV_

status,description,sensitive

Unclaimed,Incident along river,Not Sensitive

In Progress,Incident along road,"Deleted by Source,Deceptive or Misleading" 

### Recommended workflow
We intend for CSV files to be a tool for transferring data from your spreadsheet to Atlos. We recommend you:
1. Edit your data in a spreadsheet (Google Sheets or Microsoft Excel both work).
2. Export your spreadsheet as a CSV.
3. Import that CSV into Atlos. 

### Formatting for bulk import
On this page, we visualize the format Atlos requires for bulk import in its spreadsheet format before the data has been exported into a CSV.

**Required columns—** Atlos requires three columns in all bulk imports. Spreadsheets must include three titles in the first row:

{% table %}
* status
* description
* sensitive
{% /table %}


**Order—** The order of these column headers is not relevant; Atlos will not treat the following tables differently:

{% table %}
* sensitive
* status 
* description 
---
* Not Sensitive
* Unclaimed 
* Explosion along river
---
* "Deleted by Source,Deceptive or Misleading"
* In Progress
* Explosion along road
{% /table %}



**Case sensitivity—** Bulk import is sensitive to the capitalization of column names. Bulk import of a spreadsheet with the sensitivity column titled “Sensitive” will fail because the title is capitalized. 

**Optional columns—** It’s possible to import more data than just status, description, and sensitivity. The full list of allowed columns is dependent on each project’s list of attributes. Instead of providing comprehensive documentation of permissible columns here, we provide it in the in-platform documentation on the Bulk Import page. As an example, here’s a spreadsheet that can be bulk imported into a project that uses Atlos’ default data model:

[TOOO: make this smaller]
{% table %} 
* location
* status
* description
* date
* sensitive
* source_1
* Impact
* Equipment Used
---
* 50.476776185687186, 34.92377349447404
* Unclaimed
* https://ukraine.bellingcat.com/?id=CIV1483
* 2022-10-02
* Not Sensitive
* https://t.me/hyevuy_dnepr/37868
* Roads/Highways/Transport, Administrative, Commercial
* Land mines
--- 
* 46.63123689796267,32.61207480964933
* In Progress
* https://ukraine.bellingcat.com/?id=CIV1738
* 2022-23-12
* Not Sensitive
* https://twitter.com/Tendar/status/1606406179604897798
* Residential
* Incendiary munitions

{% /table %}

**Differences between bulk export and bulk import—** Bulk exports are compatible with bulk imports; it is possible to bulk import a CSV that you’ve exported from Atlos. However, bulk import will not process all data included in bulk exports. Specifically, if you include “slug”, “inserted_at”, and “updated_at” columns in a bulk import, Atlos will not interpret these fields. These fields are relevant to exports, because they describe key information about incidents:
- **“slug”** refers to incident IDs.
- **“inserted_at”** describes when an incident was created. 
- **“updated_at”** refers to the last time that an incident was edited. 

These fields will not impact data that has been bulk imported to Atlos because they describe metadata about incidents that is automatically generated. 

[VIDEO]

## Data export
We think Atlos is a great tool for collaboration at scale, but it's not the best tool for every job. Whether investigators are looking to archive media forensically, publish data, or just take another look in a Google Sheet, sometimes it’s necessary to export data. Atlos make exporting to a CSV extremely simple. See [here](#what-is-a-csv) for more information on the CSV file type.

### How to export data
To export all of a project’s data:
1. Navigate to **Projects** page.
2. Select the project whose data you wish to export. 
3. Click **Export** on the top-right corner of the project's page. 

To export the results of any search, click the ![Paperclip](/images/paperclip.png) icon in the search bar.

{{< callout type="info" >}}
To programatically extract data from your project, use our project-scoped [API](/docs/api).
{{< /callout >}}