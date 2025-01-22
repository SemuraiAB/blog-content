Cheat Code: Programmatic Setup for “Services”

This cheat code combines all the steps from the first three articles into a single programmatic implementation. Add the following code to your child theme’s functions.php file to set up everything without manually navigating through the WordPress admin.

Step 1: Register the Custom Post Type

function register_services_cpt() {
    $args = [
        'public' => true,
        'label'  => 'Services',
        'supports' => ['title', 'editor', 'thumbnail'],
        'has_archive' => true,
        'rewrite' => ['slug' => 'services'],
    ];
    register_post_type('services', $args);
}
add_action('init', 'register_services_cpt');

Step 2: Register Custom Taxonomies

function register_service_taxonomies() {
    // Service Categories (hierarchical)
    register_taxonomy('service_categories', 'services', [
        'label' => 'Service Categories',
        'hierarchical' => true,
        'rewrite' => ['slug' => 'service-categories'],
    ]);

    // Service Areas (non-hierarchical)
    register_taxonomy('service_areas', 'services', [
        'label' => 'Service Areas',
        'hierarchical' => false,
        'rewrite' => ['slug' => 'service-areas'],
    ]);
}
add_action('init', 'register_service_taxonomies');

Step 3: Add Custom Fields

Using register_post_meta, define and display custom fields programmatically.

function add_service_custom_fields() {
    // Service Description
    register_post_meta('services', 'service_description', [
        'show_in_rest' => true,
        'single' => true,
        'type' => 'string',
    ]);

    // Pricing
    register_post_meta('services', 'pricing', [
        'show_in_rest' => true,
        'single' => true,
        'type' => 'string',
    ]);

    // Duration
    register_post_meta('services', 'duration', [
        'show_in_rest' => true,
        'single' => true,
        'type' => 'string',
    ]);
}
add_action('init', 'add_service_custom_fields');

Step 4: Create Templates

Single Template (single-services.php):

<?php
get_header();

if (have_posts()) :
    while (have_posts()) : the_post(); ?>
        <h1><?php the_title(); ?></h1>
        <p><strong>Description:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'service_description', true)); ?></p>
        <p><strong>Pricing:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'pricing', true)); ?></p>
        <p><strong>Duration:</strong> <?php echo esc_html(get_post_meta(get_the_ID(), 'duration', true)); ?></p>
        <p><strong>Categories:</strong> <?php the_terms(get_the_ID(), 'service_categories', '', ', '); ?></p>
        <p><strong>Service Areas:</strong> <?php the_terms(get_the_ID(), 'service_areas', '', ', '); ?></p>
    <?php endwhile;
endif;

get_footer();

Archive Template (archive-services.php):

<?php
get_header();

if (have_posts()) : ?>
    <h1>Our Services</h1>
    <div class="services-archive">
        <?php while (have_posts()) : the_post(); ?>
            <div class="service-item">
                <h2><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
                <p><?php the_excerpt(); ?></p>
            </div>
        <?php endwhile; ?>
    </div>
    <?php the_posts_pagination();
else :
    echo '<p>No services found.</p>';
endif;

get_footer();

Step 5: Flush Permalinks

Visit Settings > Permalinks in your WordPress admin and click Save Changes to flush the rewrite rules.

One-Time Action

Copy-paste this code into your child theme’s functions.php file. It will automatically set up:
	1.	The “Services” custom post type.
	2.	Two custom taxonomies: “Service Categories” and “Service Areas.”
	3.	Custom fields for Description, Pricing, and Duration.
	4.	The single and archive templates to display all custom data.

This eliminates the need for extensive WordPress admin setup, making the process efficient and developer-friendly!