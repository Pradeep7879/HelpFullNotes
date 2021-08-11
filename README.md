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

->    symfony/routing
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
