2. Adding Custom Fields to the Services Post Type

In this article, we’ll create custom fields for the “Services” post type using Secure Custom Fields (SCF) to add structured data such as pricing, duration, and a detailed description.

Step 1: Create a Field Group
	1.	In your WordPress admin, navigate to SCF > Field Groups.
	2.	Click Add New.
	3.	Set the Field Group Name to Service Details.
	4.	Set the Location rule to:
	•	Post Type is equal to Services.
	5.	Click Save.

Step 2: Add Custom Fields
	1.	Open the newly created Service Details field group.
	2.	Add the following fields:
	•	Field Name: service_description
	•	Field Label: Description
	•	Field Type: Textarea
	•	Field Name: pricing
	•	Field Label: Pricing
	•	Field Type: Text
	•	Field Name: duration
	•	Field Label: Duration
	•	Field Type: Text
	3.	Save the field group.

Step 3: Display Custom Fields in Single Template

To display the custom fields on the front end, create or edit the single-services.php template file in your child theme.

<?php
get_header();

if (have_posts()) :
    while (have_posts()) : the_post(); ?>
        <h1><?php the_title(); ?></h1>
        <p><strong>Description:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'service_description', true)); ?></p>
        <p><strong>Pricing:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'pricing', true)); ?></p>
        <p><strong>Duration:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'duration', true)); ?></p>
    <?php endwhile;
endif;

get_footer();

Next Steps

In the next article, we’ll create an archive page for the “Services” post type and show how to list all services dynamically.