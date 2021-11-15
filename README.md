# HelpFullNotes

**Interview Questions**

1.    How many files are required for Views?

->    Each view uses a minimum of two templates:

      The first template is "views-view.html.twig". 
          This template is used for all views and contains the layout for the view. (view content, header, footer, exposed form and attachments)

      The second template is the style template. 
          The default used template will vary based on the applied view style (grid, table, html list or unformatted).
              Grid: views-view-grid.html.twig
              Table: views-view-table.html.twig
              HTML List: views-view-list.html.twig
              Unformatted: views-view-unformatted.html.twig

      The third template is "views-view-fields.html.twig". 
          This template is used only if the view row style is set to "Fields". This template is responsible for looping through available fields and print fields wrappers, labels, and markup.

      The fourth template is "views-view-field.html.twig". 
          This template is used only if the view row style is set to "Fields". This is the last template and is responsible for printing each field markup.
             
2.    How to reduce the Page Load Time?

->    Using CDN(content delivery networks)

3.    Name the symfony component?

            symfony/routing
            symfony/serializer
            symfony/validator
            symfony/yaml
            symfony/dependency-injection
            symfony/error-handler
            symfony/http-foundation
            symfony/event-dispatcher
            symfony/translation
            symfony/console
            symfony/filesystem
            symfony/finder
            symfony/process
      
4.    What is Drupal console?

->    Drupal Console is a suite of tools run from a command line interface (CLI) to generate boilerplate code and interact with a Drupal 8 or Drupal 9 installation. 
      It's an essential tool for anyone writing code for Drupal.
      
5.    What is composer?

->    Composer is used to manage or download the dependencies of modlues.      
      
6.    Regular Hooks used in twig list.

->    HOOKS used in Theme:-

            hook_form_system_theme_settings_alter(&$form, FormStateInterface $form_state)
            hook_preprocess_node(&$variables)
            hook_preprocess_field(&$variables, $hook)
            hook_preprocess_HOOK(&$vars)
                              kirby_preprocess_page_title
            hook_preprocess_html(&$vars)
            template_preprocess_paragraph(&$variables)
            hook_preprocess_page(&$variables)
            hook_form_system_theme_settings_alter(&$form, FormStateInterface $form_state)
            
->    HOOKS used in Module:-
      
      hook_form_alter(&$form, FormStateInterface $form_state, $form_id)
      hook_form_FORMID_alter(&$form, $form_state)
      Implements hook_ENTITY_TYPE_view_alter(array &$build, EntityInterface $node, EntityViewDisplayInterface $display) for node entities.
      
7.    What is content entites and configuration entites?

                  Content entities (users, nodes, taxonomy terms, ...)
                  Configuration entities (content types, fields, views, all configuration settings)
                  
8.    What is migration, and required modules?

            Core Migrate modules:-
               1.   Migrate
               2.   Migrate Drupal (Provides the capabilities needed to migrate configuration and content from a Drupal source site to Drupal 8.)
               3.   Migrate Drupal UI(Provides an user interface (at /upgrade) for performing an upgrade from Drupal 6 or Drupal 7 to Drupal 8.)

            Contributed Migrate modules

            1.    Migrate Upgrade(Provides the migrate-upgrade Drush command for generating the migrations from a Drupal source site.)
            2.    Migrate Tools(Provides Drush commands and tools such as migrate-status, migrate-import, migrate-rollback, migrate-stop, migrate-reset-status,                       migrate-messages, migrate-fields-source.)
            3.    Migrate Plus(Provides APIs for grouping migrations as well as a facility to manipulate incoming source data in migrations as well as code examples                   to build custom migrations.)


9.    What is Cache in drupal 8?
      
            Cacheability metadata consists of 3 properties:

            cache tags
            For dependencies on data managed by Drupal, like entities & configuration

            cache contexts
            For variations, i.e. dependencies on the request context

            cache max-age
            For time-sensitive caching, i.e. time dependencies


10.   What is namespace?

            ->    Namespace can be use a make different method for making our code unique. 
                  and uses PHP classes instead of simple functions. Two classes can have the same name
                  as they have a different namespace and also namespace as the path to the file.
                  
            
 11.  How to Disabling Aggregation for specific CSS or JS?
 
             ->    By default, multiple local files will be aggregated where possible. 
                   To disable this for a file, set its 'preprocess' flag to false.
                   
                   cuddly-slider:
                    version: 1.x
                    js:
                      js/cuddly-slider.js: {preprocess: false}
                    dependencies:
                      - core/jquery
                      - core/drupalSettings
                     
          -------------> CDN / externally hosted libraries
                        
                              To improve page loading speed.
                              This can be done by declaring the library to be "external".
                              
                              angular.angularjs:
                                remote: https://github.com/angular/angular.js
                                version: 1.4.4
                                license:
                                  name: MIT
                                  url: https://github.com/angular/angular.js/blob/master/LICENSE
                                  gpl-compatible: true
                                js:
                                  https://ajax.googleapis.com/ajax/libs/angularjs/1.4.4/angular.min.js: { type: external, minified: true }
           
           
 12.      What is the difference between composer.json and composer.lock..?
            
                  composer.json is updated to show that Drupal is now a dependency of your project
                  composer.lock is created/updated to reflect the current versions of all Composer managed libraries
                 
 13.      What is the difference between composer update and composer install..?
 
                  Developers should also always run composer.install anytime they switch Git branches, such as between a production and a staging branch.
                  The composer update command should only be used to update to new versions of libraries, and the composer.lock file should always be
                  committed after running composer update
                  
              Finally, any time a developer adds a new dependency to the project, they need to commit both the composer.json file and the composer.lock file to Git.
