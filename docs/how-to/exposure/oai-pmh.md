# OAI-PMH Configuration and Harvesting

Your OAI-PMH endpoint is at `/oai/request` (formerly `/oai2` in Islandora 7).

In order to properly enable OAI-PMH harvesting, you will need to configure your OAI module at `/admin/config/services/rest/oai-pmh`.

Some basic settings:

- What to expose:
    - Check all boxes except Entity Reference
- Metadata mappings:
    - mdRecord: DPLAVA
    - oai_qdc: DGI Standard Qualified Dublin Core
    - oai_raw: None
    - oai_dc: OAI Dublin Core (RDF Mapping)
    - mods: None
- Set your repository name and admin email
- Leave other settings as-is

The fullest sets of metadata are either `mdRecord` or `oai_qdc`. `mdRecord` is recommended, as it includes a link to the media, in the field `edm:preview`. 

A request will look something like this: `https://yoursite.arcabc.ca/oai/request?verb=ListSets&metadataPrefix=mdRecord`

If you have provided harvesting information to an outside organization for your Islandora 7 site, you will need to give them the new request path and metadata schema.

## Special considerations for EDS (EBSCO Discovery Service)

Many Arca partners include their repositories in their EDS implementations. Following are the questions EBSCO will ask about your repository, with some answers to assist you.

1. What is the name of this database?
    * Enter your repository's name as configured in your site settings.
2. What type of database?
    * Select the primary purpose of your repository, either "Institutional Repository" or "Digital Archive".
3. IR Software/Vendor
    * Islandora
4. Other
    * 4a: mdRecord/DPLAVA
    * 4b: http://dplava.lib.virginia.edu; https://dplava.lib.virginia.edu/dplava.xsd
5. Does your IR have a Harvest URL?
    * Yes
    * 5.1) https://[yoursite.arcabc.ca]/oai/request/
    * 5.2) "Should all data sets be included in the harvest?": [your choice]
    * 5.3) Weekly, at set day/time [unless you require more frequent harvesting]
    * 5.4) Annually
    * 5.5) No
6. If data is not OAI accessible, can you send records via File Transfer Protocol (FTP)? 
    * No
7. How many records are currently in your database?
    * For a rough count, run an empty search and check the number of records returned.
8. Which metadata element contains a link back to the metadata record on your site? 
    * `<dcterms:identifier>`
    * 8a) EBSCO uses “Online Access” as the default link label. If you want to customize the label for this link, please indicate what it should be: [your choice]
9. Which metadata element contains a link to the item/document/image?
    * `<edm:preview>`
    * 9a) EBSCO uses “Online Access” as the default link label. If you want to customize the label for this link, please indicate what it should be: [your choice]
10. If your data contains links for internal use only or links that need to be authenticated, please indicate that here.  EBSCO tests links remotely during the build process. - please let us know if these links do not work remotely
    * Yes, links work remotely [unless you have protected content that needs to be harvested as well]
11. If direct links are not provided or accessible in data, please provide a base URL to construct the link
    * Not applicable (links are present in metadata)
12. [leave blank]
13. [leave blank]
14. If `<dc:coverage>` is present in your data, should it be searched as a subject (i.e. geographic or chronological)?
    * Other (not applicable)
15. If `<dc:contributor>` is present in your data, should it be searched as an Author?
    * Your choice (we have dc:creator and dc:contributor present in this metadata format)
16. Do you want your records to be flagged as “Full Text”? If yes, IR records will be returned when the Full Text limiter is selected in EDS.
    * Your choice
17. Do you want your records to be flagged as “Peer Reviewed”? If yes, IR records will be returned when the Peer Reviewed limiter is selected in EDS.
    * Your choice
18. Do you have DOI numbers in your data? 
    * Choose applicable answer
    * 18a) `<edm:isShownAt>` or `<dcterms:identifier>`
19. Do you have ISBNs or ISSNs in your data? 
    * Choose applicable answer
20. If there is OCR text in your data (typically found in dc:description), do you want it to be displayed in the full record?
    * Your choice
21. Do you want OCR text to be searchable?
    * Your choice
22. For Dublin Core users only: EBSCO loads every Dublin Core metadata element into EBSCO Discovery Service by default. Please check off, if any, the metadata elements in your data you do NOT want loaded onto EDS:
    * Your choice
23. In which fields are the following found? [ANSWERS TBD]
    * Edition:
    * Volume: 
    * Issue: 
    * Pages: 
24. If your data is harvested via OAI, the <setName> in the sets.xml file will be used to construct the Collection Name. If your data does not contain sets, which metadata element contains the Collection Name? If there are no collection names, please indicate that here.
    * Not applicable (data does contain sets)
    * 24a) Leave blank
25. The lookup table they ask you to download and fill out has a red column, which is the column you will be editing.
    * In the header row, replace `<dc:type>` with `<edm:hasType>`
    * You will find all of the possible entries for this taxonomy in your Genre term list: `/admin/structure/taxonomy/manage/genre/overview`
    * Alternatively, if you want less-nuanced metadata mapping, you can use `<dcterms:type>`, which has a much shorter list of options (eg "text", "still image") from the Resource Types taxonomy (`/admin/structure/taxonomy/manage/resource_types/overview`).
    