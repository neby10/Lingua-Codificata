Hugo Notes

Installation: brew install hugo
New Site: hugo new site sitename

Create Git Initialization and Add Theme:
cd foldername
git init
git submodule add theme

Serve: hugo server

New File Based on Archetype: hugo new postname

Build Site Command: hugo
This will take all items and combine into one single finished website within the public folder that can be published to the server for your website. 
Delete public folder before each build. Files would get overwritten anyway but if you have a file you deleted it would remain in the public folder since it would not be overwritten because the file is deleted and there is not file to overwrite it. 

Hugo Functions: https://gohugo.io/functions/
{{ funcName param1 param2 }}
{{ truncate 10 “this is a really long string” }}

Data: 
Data folder for storing data files. 
Can be stored with .json, .yaml, .toml
{{ range .Site.Data.fileName }}
	{{ .name }}
{{ end }}

IMPORTANT:
For each theme, view demo or docs to get started the quickest!

Taxonomies: Tags, Categories, Create your own… Add to config.toml under [taxonomies] to list desired taxonomies for your site.

Adding Shortcodes: {{< shortcode-name param1 >}}
	Example: {{< youtube TWTfhyvzTx0 >}}  - - the youtube shortcode requires video id from url (not entire url unless you would like to but must include quotations)


Folder / Directory Structure Explained
https://gohugo.io/getting-started/directory-structure/

Configuration File for Entire Site
https://gohugo.io/getting-started/configuration/


Front Matter Formats
TOML
identified by opening and closing +++.
YAML
identified by opening and closing ---.
JSON
a single JSON object surrounded by ‘{’ and ‘}’, followed by a new line.

dateformat = “2006-01-02” # will only work with this specific date
Front Matter Variables
https://gohugo.io/content-management/front-matter/
