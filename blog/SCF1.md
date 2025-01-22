1. Introduction to Secure Custom Fields (SCF)

In this article, we’ll cover the basics of Secure Custom Fields (SCF) and how to use it to create and manage custom post types, taxonomies, and fields in WordPress. This setup is essential for tailoring WordPress to meet business needs.

Step 1: Install Secure Custom Fields Plugin
	1.	Log in to your WordPress admin panel.
	2.	Go to Plugins > Add New.
	3.	Search for “Secure Custom Fields.”
	4.	Click Install Now and then Activate.

Step 2: Register a Custom Post Type

Create a “Services” custom post type for showcasing business offerings.
	1.	In the WordPress admin panel, navigate to SCF > Post Types.
	2.	Click Add New.
	3.	Configure the fields:
	•	Post Type Key: services
	•	Plural Label: Services
	•	Singular Label: Service
	4.	Save the post type.

Code snippet for reference (if registering programmatically):

function register_services_cpt() {
    $args = [
        'public' => true,
        'label'  => 'Services',
        'supports' => ['title', 'editor', 'thumbnail'],
    ];
    register_post_type('services', $args);
}
add_action('init', 'register_services_cpt');

Step 3: Add Custom Taxonomies

Organize services with “Service Categories” and “Service Areas.”
	1.	Navigate to SCF > Taxonomies.
	2.	Click Add New.
	3.	For Service Categories:
	•	Taxonomy Key: service_categories
	•	Associated Post Type: services
	4.	Repeat for Service Areas:
	•	Taxonomy Key: service_areas
	•	Associated Post Type: services
	5.	Save each taxonomy.

Code snippet for reference:

function register_service_taxonomies() {
    // Register Service Categories
    register_taxonomy('service_categories', 'services', [
        'label' => 'Service Categories',
        'hierarchical' => true,
    ]);
    // Register Service Areas
    register_taxonomy('service_areas', 'services', [
        'label' => 'Service Areas',
        'hierarchical' => false,
    ]);
}
add_action('init', 'register_service_taxonomies');

Next Steps

In the next article, we’ll add custom fields to the “Services” post type and display them dynamically on the front end.