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
      hook_ENTITY_TYPE_view_alter(array &$build, EntityInterface $node, EntityViewDisplayInterface $display) for node entities.
      hook_preprocess_block(&$variables)
      
      example for Cache:-
                        /** * Implements hook_preprocess_block(). */ 
                        function mymodule_preprocess_block(&$variables) { 
                          if ($variables['elements']['#id'] == 'search_promo') { 
                            // Unique cache per search query string. 
                            $variables['#cache']['contexts'] = ['url.query_args:search']; // Depends on content from a node entity. 
                            $node = Node::load($variables['promo_nid']); 
                            $variables['#cache']['tags'] = [$node->getCacheTags(]; 
                          } 
                        }
      
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
            For dependencies on data managed by Drupal, like entities & configuration.
            A cache will be invalidated when a cache tag is matched. 
            example:-   user:10 (invalidates the cache when User entity 10 changes)
                        node:8 (invalidates the cache when Node entity 8 changes)


            cache contexts
            For variations, i.e. dependencies on the request context.
            Cache contexts are represented in sets of strings.
            example:-   user.roles (vary by user’s role)
                        url (vary by the entire url)
                        url.path.is_front (vary by the front page)

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

14.      What is the USE statement in drupal 8 or 9..?
      
                  The technique for providing access to other classes/interfaces in Drupal 8 (and PHP in general) is the “use” statement. 
                  It allows you to specify what namespace should be used to load a specific class.
                  Any dependencies registered in methods that you are extending/defining
                  
                  Any class that you are extending
                  Any interface that you are implementing
                  Any class you are instantiating directly in code
                  
15.     What is Namespace in Drupal 8 or 9..?

                  Namespaces are a useful feature of object oriented programming (OOP) that allow you to isolate 
                  identical class names within different contexts using a syntax that looks a lot like folder hierarchy.
                  
16.   Rest API Response Codes

                  200 – OK                  201 – Created                  202 – Accepted
                  307 – Temporary Redirect                  308 – Permanent Redirect                  
                  400 – Bad Request      401 – Unauthorised      402 – Payment Required     403 – Forbidden   404 – Not Found     405 – Method Not Allowed
                  500 – Internal Server Error     501 – Not Implemented      502 – Bad Gateway       503 – Service Unavailable     504 – Gateway Timeout

17.   Different Type Of REST Requests (each and every method of REST API along with the collections).

                  Method	      Description
                  
                  GET	      Fetch status line, Response body, Header etc.
                  HEAD	      Same as GET, but only fetch status line and header section
                  POST	      Perform request using request payload mostly in creating a record at the server
                  PUT	      Useful in manipulating/updating the resource using Request payload
                  DELETE	      Deletes information relating to the target resource.
                  OPTIONS	      Describe the communication options for the target resource
                  PATCH	      Very much similar to put but it is more like a minor manipulation of resource content


18.   How to create Multi-sites..?

            1.    Firstly copy the sites/example.sites.php and overwrite sites/sites.php
                  sites/sites.php look like 
                                          $sites['uat.hotair.com.au'] = 'hotair.com.au';
                                          $sites['uat.hot-air.cn'] = 'hot-air.cn';
                                          $sites['uat.hotair.kr'] = 'hotair.kr';
                                          $sites['uat.hot-air.jp'] = 'hot-air.jp';
                                       
            2.    Create the folder, for each multi-sites separately and each folder have settings.php, 
                  settings.local.php, services.yml and modules(optional) folder. if you want to separate 
                  the configuration, create the files folder and mention path in settings.php.


19.   Usefull sites to learn Drupal..?

                  https://www.specbee.com/blogs/improving-drupal-9-performance-modules-best-coding-practices-and-right-server-configuration

20. how to secure site, clickjacking, CSS and other via appropriate HTTP-response-header?


          **Content-Security-Policy (CSP)**
            • Purpose: Helps prevent a variety of attacks such as Cross-Site Scripting (XSS) and data injection attacks.

          **Strict-Transport-Security (HSTS)**
            • Purpose: Ensures that the browser only communicates with the server over HTTPS, preventing man-in-the-middle attacks.

          **Content-Type (This header is included default by drupal)**
            • Purpose: Specifies the media type (MIME type) of the resource, ensuring that the content is interpreted correctly by the browser.

          **X-Content-Type-Options (This header is included default by drupal)**
            • Purpose: Prevents the browser from MIME-sniffing a response away from the declared content-type, which can help prevent certain types of attacks.

          **Cache-Control (This header is included default by drupal)**
            • Purpose: Controls how, and for how long, the browser and other caches store the response.
