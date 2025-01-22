In this tutorial, we’ll enhance our ‘Services’ custom post type by adding custom taxonomies and fields using the Secure Custom Fields (SCF) plugin. This will allow us to categorize services effectively and add specific metadata to each category.

Part 1: Creating Custom Taxonomies

Custom taxonomies help organize your content beyond the default categories and tags. We’ll create two taxonomies: ‘Service Categories’ and ‘Service Areas’.
	1.	Register ‘Service Categories’ Taxonomy:
	•	In your WordPress dashboard, navigate to SCF > Taxonomies.
	•	Click on Add New.
	•	Set the following details:
	•	Taxonomy Key: service_categories
	•	Plural Label: Service Categories
	•	Singular Label: Service Category
	•	Associate this taxonomy with the ‘Services’ post type.
	•	Configure additional settings as needed, such as making it hierarchical if you want parent-child relationships.
	•	Click Save to register the taxonomy.
	2.	Register ‘Service Areas’ Taxonomy:
	•	Repeat the above steps with the following details:
	•	Taxonomy Key: service_areas
	•	Plural Label: Service Areas
	•	Singular Label: Service Area
	•	Associate this taxonomy with the ‘Services’ post type and save the settings.

Part 2: Adding Custom Fields to Taxonomies

Adding custom fields to taxonomies allows you to store additional information about each term. For instance, you might want to add a description or an image to each ‘Service Category’.
	1.	Create a Field Group for ‘Service Categories’:
	•	Navigate to SCF > Field Groups.
	•	Click on Add New to create a new field group.
	•	Name the group ‘Service Category Details’.
	2.	Add Fields to the Group:
	•	Within the ‘Service Category Details’ group, add fields as needed.
	•	For example, to add an image field:
	•	Field Label: Category Image
	•	Field Name: category_image
	•	Field Type: Image
	3.	Set Location Rules:
	•	Under ‘Location’, set the rule to display this field group if Taxonomy is equal to Service Categories.
	4.	Publish the Field Group:
	•	Click Publish to save the field group.

Part 3: Displaying Custom Taxonomy Fields in Templates

To display the custom fields added to your taxonomies on the front end, you’ll need to modify your theme’s template files.
	1.	Edit the Taxonomy Template:
	•	In your child theme directory, locate or create the template file for your taxonomy.
	•	For ‘Service Categories’, the file should be named taxonomy-service_categories.php.
	2.	Retrieve and Display Custom Fields:
	•	Within the template file, add the following code to display the custom field:

<?php
// Get the current taxonomy term
$term = get_queried_object();

// Get the custom field value
$category_image = get_field('category_image', $term);

// Display the custom field
if ($category_image) {
    echo '<img src="' . esc_url($category_image['url']) . '" alt="' . esc_attr($category_image['alt']) . '">';
}
?>


	•	This code retrieves the ‘Category Image’ field for the current term and displays it.

By following these steps, you’ve enhanced your ‘Services’ post type with custom taxonomies and fields, allowing for better organization and richer metadata. In the next tutorial, we’ll cover how to display these custom fields on the front end and style them appropriately.