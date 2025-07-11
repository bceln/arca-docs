# Post-Migration Tasks

## Local Admin Tasks
The Arca Office is working with Discoverygarden to create a theme, a base configuration, infrastructure, and migrate content, but there will be numerous post-migration tasks for local admins once your site is up, content is migrated, and your account has been created.

### Revise About page
The Arca Office will create a stub About page for you to customize, and add it to the header menu. You can edit this page to add details such as contact information and context for your site.

### Identify your Scholars and create a View
If you had a Scholars collection in your previous repository, you will need to find those persons in your new site, and edit them to mark them as Scholars.

#### Mark your Scholars:

Scholars are entities in the Person taxonomy that you have identified specially as pertinent to your institution. There is a special metadata field that allows you to mark them as such, so they can be included in your views of your scholars.

1. Open the Person taxonomy at `Structure -> Taxonomy -> Person`, or the path `/admin/structure/taxonomy/manage/person/overview`
2. Find the Person you want to mark as a Scholar, and click Edit
3. On the Edit screen, find the "Include in Scholars list" toggle and turn it on.
4. Save

#### Create your Scholars view:

Since Scholars are not Repository Items, you need to configure a special View to display them. These instructions provide a very basic view; you may need additional CSS work to style it appropriately.

1. Create a new view at `Structure -> Views -> Add View`
2. Set up your view:
    - View name: Your choice; "Scholars" for this example
    - View settings: 
        - Show: `Taxonomy Terms`
        - Of type: `Person`
    - Page settings: `Create a Page`
        - Set the title and path you prefer. If your path is `scholars`, the URL to the page will be `yoursite.arcabc.ca/scholars`.
        - Page display settings: `Grid` or `Unformatted list` of `fields`
    - Items to display: However many you want to appear per page.
    - Create a menu link and RSS feed if you want to.
    - Save and edit
3. Configure your view:
    - Format: Defines how the results will display, and what elements you can include in the display.
        - Format: Your choice; `Grid`, `Bootstrap Grid`, `Responsive Grid`, etc.
            - `Responsive Grid` recommended
        - Show: `Fields`
    - Fields: Defines which fields from the Person metadata are displayed in this view.
        - `Taxonomy term: Name`
        - `Photograph`
            - Formatter: `Thumbnail`
            - Image style: Your choice; `Medium (220x220)` or `Thumbnail (100x100)` recommended.
        - Any other fields you want to display in this view
    - Filter Criteria: Filters the list of results to the specific criteria you set.
         - (Leave the existing filters as-is)
         - Add: `Include in Scholars List`
             - Operator: `Is equal to` > `True`
         - You may also choose to include other filters on other metadata, such as affiliation, title, etc.
             
    - Sort Criteria:
         - Choose the field you want to sort by.


### Apply access controls

Because of the complexity of XACML policies and embargoes, we are unable to automatically migrate access restrictions on your objects. Instead, these will have to be applied manually after the data is migrated, but before your new site becomes publicly accessible.

Access restrictions in the new platform will primarily be based on the [Embargo module](https://github.com/discoverygarden/embargo). Some sites with special requirements might also use Groups. Training on Embargo, IP Embargo, and Groups will be provided.

Process:

- Before migration, the Arca Office will provide you with a spreadsheet of all Islandora 7 objects from your repository with existing access restrictions, including titles and PIDs.
- After your migration, the Arca Office will provide Islandora training, including training on Embargoes and other access control methods.
- In your new site, with the list provided to you by the Arca Office, you will apply the appropriate restrictions to your objects.
  - The Arca Office will be available to support you as required with this process.

### Add Embed Code to migrated Remote Media objects

If your repository contains objects with the Islandora Remote Media content model, you may need to do some extra post-migration work in order to complete these objects.

For items whose media is hosted on oEmbed-compatible sites like Vimeo and YouTube, if your content has a URL in the MODS field `<identifier displayLabel="remote media URL">`, and you have tested that URL in the [Sandbox](https://bceln.i8.dgicloud.com/), then no work is required for that object.

If your media does not work with an oEmbed link, you will need to migrate the Embed Code manually.

Process:

- Before migration, the Arca Office will provide you with a zip file containing all the OBJ datastreams for your Remote Media objects. These datastreams are text files that contain the embed code you will need to migrate.
- After migration, search the PIDs from the filenames to find your Remote Media objects in the new repository.
- For each Remote Media object:
  - Click the Media tab
  - Click the `+ Add Media` button
  - Click `Embed Code`
  - Set a relevant Name
  - Paste your code directly from the exported file into the `Insert Embed Code` field, without modification, including all HTML tags
  - Under `Media Use`, select "Service File"
  
When viewing your object, the embedded media should display normally.

### Add TRANSCRIPT datastreams back to video and audio content

TRANSCRIPT datastreams, which would have provided subtitles/closed captioning on your video objects, will not be migrated automatically. They need to be re-added after the migration is complete.

Process:

- Before migration, the Arca Office will provide you with a zip file containing all the TRANSCRIPT datastreams for your objects.
- Ensure that your TRANSCRIPT files are in the VTT format. Convert if necessary.
- After migration, search the PIDs from the filenames to find the corresponding objects in the new repository.
- For each object:
  - Click the Media tab
  - Find the video or audio media, and click Edit
  - Under the "Track" section, upload your transcript file.

!!! warning
  You must add the VTT to the `Service File` derivative. This is the version of your video that the system displays in the viewer, **not** the Original File. If you create **new** audio or video objects in the future and add captions to the Original File at time of ingest, the VTT will automatically carry over to the Service File that gets generated.

### Create and review users, roles, and permissions

Before migration, you should already have reviewed and pruned your users list so that only users you want to migrate will appear in your new repository.

Users should be migrated automatically, but you should review them to make sure that (a) all appropriate users are present, (b) no unwanted users have been migrated, and (c) each user has the appropriate Role.

You will also want to review permissions for each role to make sure that they are set appropriately.

### Set up mediated submission

If you want a mediated process for self-submission, follow the [self-submission setup instructions](/arca-docs/how-to/processes/self-submission/).

### Configure Pathauto

If you want to set up custom URLs for your objects, you will need to [configure the Pathauto module](/arca-docs/how-to/display/pathauto/).

This configuration happens after objects are migrated. Once you have configured it in the way you want it, we will run a script to apply the new paths to all migrated objects.

### Theme customizations

Customize your theming as you see fit. You can modify colours, logos, etc. via the Appearance menu at `/admin/appearance/settings/dgi_i8_base`.

You can take more advanced theming steps (block placement, etc.) following the [Theming Customizations guide](/arca-docs/how-to/theming/customizations/).

## Arca Office Tasks

### Pathauto paths

Define paths for URL aliases, in consultation with Arca Admins.

### User Accounts
Create user accounts for primary migration contacts with the roles of site administrator and repository administrator. 

### About Page
Create stub About page with boilerplate text about Arca.

### Communicate Migration Completion
Communicate the completion of the migration to the local admin and direct them to begin Post-Migration Tasks above.

### Migration Stubs
Remove "parent" references to migration stubs for all top-level collections.

### Cleanup
Perform backend migration cleanup.

### Matomo Configuration
Configure analytics for each migrated site once ready to port over to new URL.