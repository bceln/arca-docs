# Customizations by individual sites

Some Arca partners have created unique customizations. These are collected here, with instructions for replicating them.

If you would like to add your own customizations to this list, you can either propose an edit (click the pencil icon on this page) or send your information with appropriate details to the Arca Office.

## Replace the Collection Representative Image with a solid colour, and add a custom thumbnail

Uses a solid colour background in the Collection title header, instead of a cropped image.

- Site: BCRDH
- Use case: Uniformity, branding
- Modules: Asset Injector / CSS Injector

Process:

1. Add a CSS class to the "Collection: Representative Object" view so you can style it:
    - Edit the Representative Object view at `/admin/structure/views/view/collection_representative_object/edit/block_1`
    - In the "Advanced" section on the right, under "Other", find the "CSS Class" option and add a new class name: `rep-obj-display`
2. Create a CSS Injector rule to add a solid background colour to Collection header:
    - Go to `/admin/config/development/asset-injector/css` and create a new Rule with a title like "Collection Header Background"
    - Add the following rule that styles the CSS class you just created:
    ```
    .rep-obj-display{
    	background-color: #8CCDB0;
	}
    ```
3. Remove the Representative Image from collection items:
    - For each collection, go to the Edit screen
    - In the metadata form, find the Representative Image section and click Remove
4. Add a custom Thumbnail:
    - Edit the collection and click the Media tab
    - Add new Media, of type Image
    - Upload the image of your choice. For the Media Use field, select `Thumbnail`.

## Optimize thumbnail sizing to fill the card in Collection display and Search results

- Site: JIBC
- Use case: Aesthetics
- Modules: None

Search results and collection display use responsive images to generate their thumbnails, so there is no perfect thumbnail size that will fill out the boxes and eliminate the grey borders. 

You can get close by sizing your thumbnails to the ratio 216x124, or 1.74.
 
For example, with a height of 298 pixels, that would scale to a width of about 519 pixels.

To implement, create your custom thumbnail in Photoshop or other image editing software.

Navigate to your Repository Item, click the Media tab, and edit the Thumbnail image. Replace the file with your custom file.
