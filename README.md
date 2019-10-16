[![Build Status](https://travis-ci.com/Asperato/userdocs.svg?branch=master)](https://travis-ci.com/Asperato/userdocs)

# Asperato user documentation

Here lives the source for the Asperato user documentation, available at https://asperato.github.io/userdocs/. Unless you want to contribute to this documentation, you probably want to go there to [view it](https://asperato.github.io/userdocs/).

## Running the documentation locally
The documentation is based on [docusaurus](https://docusaurus.io/). To clone and run locally:

 - Install node: https://nodejs.org/en/download/
 - Install yarn: https://yarnpkg.com/en/docs/install#windows-stable
 - Clone the repo: `git clone https://github.com/Asperato/userdocs.git`
 - Navigate into the website directory: `cd website`
 - Install dependencies: `npm install`
 - Start the server: `yarn start`
 
 The server will run on port 3000. A livereload server will also start so changes should show up immediately.
 
 ## Editing the documentation
 Each page is a separate markdown file in the `docs/` folder. These can be edited as normal markdown files to make changes.
 
 ## Adding a new page
You can add a new page by creating a separate markdown file in the `docs/` folder. If you need it to show up on the sidebar, you will also need to add its ID as an entry in the `website/sidebars.json` file. Note that changes to the sidebars file need a restart of docusaurus to show.
