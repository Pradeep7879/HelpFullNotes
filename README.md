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
      
5.    Regular Hooks used in twig list.

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
      
6.    What is content entites and configuration entites?

                  Content entities (users, nodes, taxonomy terms, ...)
                  Configuration entities (content types, fields, views, all configuration settings)
