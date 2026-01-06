# Collection Search configuration

The DGI Search module provides a Collection Search option, where users can choose to search within individual collections rather than the whole repository.

To configure the DGI Search module, go to `/admin/config/search/dgi_search`, or Configuration -> Search and metadata -> DGI Search Settings.

## Required Configurations

Collection Search works by default, but if you make any changes, you will need to update fields in the Result Header Block settings:

- Card: `page_3`
- Grid: `page_1`
- List: `page_2`

Without these values in those required fields, the form will reject your changes.

## Collection Search Settings

Collection Search is turned on by default, but if you don't want it enabled, you can toggle it off here.

You can choose to sort the list of Collections in the dropdown by weight or by title, ascending or descending, but the main configuration here is the **Enable Search Within Models** section.

By default, Collection Search will only search the members of items with the **Collection** model. Here you can choose other types of parents -- for example, Newspapers.

Because only Newspapers and Collections (and potentially Serials, if you are using that model) are likely to contain a significant number of useful members, we recommend only selecting those two items. Otherwise your users will be overwhelmed with options that may not serve them well.