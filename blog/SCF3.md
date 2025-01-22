3. Creating an Archive Page for the Services Post Type

In this article, we’ll create an archive page to list all “Services” posts dynamically. This allows users to see an organized display of all your services in one place.

Step 1: Enable Archive Support

Ensure the “Services” post type has archive support enabled. If you created the post type through SCF, check that “Has Archive” is set to True in the post type settings.

If you’re registering the post type via code, ensure the has_archive parameter is set to true:

function register_services_cpt() {
    $args = [
        'public' => true,
        'label'  => 'Services',
        'supports' => ['title', 'editor', 'thumbnail'],
        'has_archive' => true,
    ];
    register_post_type('services', $args);
}
add_action('init', 'register_services_cpt');

Step 2: Create an Archive Template
	1.	In your child theme, create a file named archive-services.php.
	2.	Add the following code to display the archive of services:

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

Step 3: Add Permalinks for the Archive
	1.	Go to Settings > Permalinks in your WordPress admin.
	2.	Click Save Changes (no need to change settings) to flush rewrite rules and ensure the new archive page works.

Next Steps

In the next article, we’ll enhance the archive page by displaying taxonomies (Service Categories and Areas) and allow filtering based on them.