# Contributor Guidelines

These guidelines provide the general process for maintaining source code that builds the 
Rackspace Cloud Identity developer documentation. 


<!-- Provide as little or as much information about architecture as needed to help 
contributors figure out which file to update.-->

This project is developed and built using the 
[Python Sphinx documentation generator](http://sphinx-doc.org/). Content is 
written in [reStructuredText](http://sphinx-doc.org/rest.html), the markup syntax and 
parser component of [Python Docutils](http://docutils.sourceforge.net/index.html).

Source files for the Sphinx documentation project are in the ``api-docs`` directory. 
Here are key files that define project and content architecture: 

Content | File
--- | ---
|Index page for the main content structure| [index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/index.rst)
|About the API index| [overview/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/overview/index.rst)
|Quickstart Guide| [quickstart-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/quickstart-guide.rst)
|Developer Guide introduction|[developer-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/developer-guide.rst)
|Concepts section| [concepts.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/concepts.rst)
|General API information index|[general-api-info/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/general-api-info/index.rst)
|Authentication section index| [[authentication-info/index.rst](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/authentication-info)
|API Reference introduction|[api-reference.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-reference.rst)
|API Reference index|[api-operations/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-operations/index.rst)
|API operations methods, including code samples|[api-operations/methods](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/api-operations/methods) 
|Sphinx documentation configuration file| [conf.py](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/conf.py) (Typically, this file does not require changes.)
|Linux and OS X build script|``Makefile``|
|Windows build script|``make.bat``|
|Requirements file to support local builds| ``requirements.txt`` 


* Update the source files by using the GitHub editor or any plain text editor.
* Format source files with 
  [reStructuredText syntax](http://www.sphinx-doc.org/en/stable/rest.html).  
* For quick syntax checking, try the 
[Online reStructuredText editor](http://rst.ninjs.org/).

## Edit or add content

* Follow the [GitHub workflow](GITHUBING.md) for this repository to work 
with the source files. 
* Update the source files by using the GitHub editor or any plain text editor.
* Format source files with 
  [reStructuredText syntax](http://www.sphinx-doc.org/en/stable/rest.html).  
* For quick syntax checking, try the 
[Online reStructuredText editor](http://rst.ninjs.org/). 


**Optional:** Preview your changes before submitting a 
pull request by [building from source](#building-from-source).

### Following style guidelines

When you add or update content, use the following general style guidelines, which are 
described in detail in [Style guidelines for technical content](https://github.com/rackerlabs/docs-rackspace/tree/master/style-guide):

- Use sentence-style capitalization for titles and headings
- Use consistent text formatting
- Write clear and consistent code examples
- Use active voice
- Use present tense
- Write to the user by using second person and imperative mood
- Write clear and consistent step text
- Clarify pronouns such as *it*, *this*, *there*, and *that*
- Clarify gerunds and participles
- Use consistent terminology

<!-- Adding build from source guidelines until we can provide a link to automated gh-pages 
output, or to the staging URL that Ash is working on. 
--> 

### Merging content

All pull requests must be reviewed before merging. For minor updates and corrections,  
get a peer review to ensure content is error-free and doesn't introduce other issues.
For more complex changes or additions, the content requires both technical and editorial 
review before it can be merged. 

**Technical review**

*Quality team to add info here.*


**Editorial review** 

*Quality team to add info here.*




## Preview your changes

To preview changes, build the documentation locally using either of the 
following options:
- Install and run the [Sphinx documentation generator](http://sphinx-doc.org/) to build 
  the project locally with the [Read the Docs theme](http://docs.readthedocs.org/en/latest/theme.html).
- Install and run the [deconst client](https://github.com/deconst/client) to build the 
  project with the Rackspace-branded theme. This build creates content that looks the 
  same as the content delivered on developer.rackspace.com
  [instructions for building with the client](https://github.com/rackerlabs/docs-migration/blob/master/docs/migration-instructions.rst#building-your-project-with-the-local-deconst-client).
 

### Building with Sphinx

**Prerequisites**

- Python 2.7 or later
- Mac OSx: Install [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/) or [pyenv](https://github.com/yyuu/pyenv)
- Windows: 
[Install Python, pip, and virtualenv with PowerShell](http://www.tylerbutler.com/2012/05/how-to-install-python-pip-and-virtualenv-on-windows-with-powershell/)).


#### Set up your build environment

1. Run the following command to activate your virtual environment:

   ```
    bin activate env-name
    
   ```   

2. In the root directory for the project, run the following commands to install Sphinx 
   and other required packages::

    ```
    pip install -r requirements.txt
    
    ```
    
#### Build the project

To build the documentation project, run the following commands:

    cd api-docs
    make clean singlehtml

These commands generate a single page html document with a navigation bar on the right.

#### View the HTML build results

To open the generated project, run the following command: 

    open _build/html/index.html
    
