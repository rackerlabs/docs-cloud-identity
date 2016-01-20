# Rackspace Cloud Identity API documentation

**Build Status:** [Strider](http://ci.deconst.horse/) (http://ci.deconst.horse/rackerlabs/docs-cloud-identity-2.0/)

## Purpose

This github repository contains the source files for the following Rackspace Identity API documentation:

* [Cloud Identity Developer Guide](https://developer.rackspace.com/docs/cloud-identity/v2/developer-guide/)
* [Cloud Identity Admin Guide - Rackspace internal](http://docs-internal.rackspace.com/auth/api/v2.0/auth-admin-devguide/content/QuickStart-000.html/)

## Contributing

Contributions are welcome! 

* To suggest changes or report a problem, submit an [issue](https://github.com/rackerlabs/docs-cloud-identity/issues). 

* To make changes to a project, create your own fork of the repository. Then, submit a [pull 
request](https://github.com/rackerlabs/docs-cloud-identity/compare?expand=1) to have your changes reviewed 
and merged into the master branch as appropriate.

To build the project, you need to install Sphinx and virtualenv.  However to contribute content, all you need is an editor and a 
basic understanding of the project layout and [Restructured Text](http://sphinx-doc.org/rest.html) syntax.

You can use the Github editor or any text editor to work with documentation source files. For quick syntax checking, try the 
[Online Restructured text editor](http://rst.ninjs.org/). 

## Source format

The Rackspace developer documentation is developed and built using the [Python Sphinx documentation generator](http://sphinx-doc.org/). Content is 
written in [reStructuredText](http://sphinx-doc.org/rest.html), the markup syntax and parser component of 
[Python Docutils](http://docutils.sourceforge.net/index.html).

The repository includes the documentation source files, 
Sphinx configuration and build files, as well any required Sphinx 
extensions and build tools. 

## Structure

Source files for the Sphinx documentation project are in the ``api-docs`` directory. Here are the key files that define 
the Sphinx project and content architecture for the documentation. 

* [conf.py](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/conf.py) Sphinx documentation configuration file (Typically, this file does not require changes.)
* [index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/index.rst): Index page for the main content structure
* [quickstart-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/quickstart-guide.rst): Source for the Identity QuickStart Guide
* [authentication-info/index.rst](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/authentication-info): Top-level index for the Authentication section
* [general-api-inf/index.rst](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/general-api-info): Top-level topic index for the General API Information section
* [api-reference.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-reference.rst): Introduction to API reference
* [api-operations/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-operations/index.rst): Index for API Reference
* [api-operations/methods](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/api-operations/methods): 
Individual files for each API operations method, includes code samples (converted from WADL)
* [developer-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/developer-guide.rst): Introduction to Developer Guide
* [overview/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/overview/index.rst): Index for the Overview section
* **make.bat**: windows build script
* **Makefile**: linux/osx build

### Building from Source

These instructions are for local builds using the default Sphinx templates. If you want to build locally using the Rackspace 
documentation templates, use the [Deconst client](https://github.com/deconst/client).

**Prerequisites**

- Python 2.7 or later
- Mac OSx: Install [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/) or [pyenv](https://github.com/yyuu/pyenv)
- Windows: Install Python, pip, and virtualenv (See [How to install Python, pip, and virtualenv with PowerShell](http://www.tylerbutler.com/2012/05/how-to-install-python-pip-and-virtualenv-on-windows-with-powershell/).

To set up your build environment:

1. Run the following commands to Activate your virtual environment:
   ```
    bin activate env-name
   ```   

2. Run the following commands to install Sphinx and other required packages::

    ```
    pip install -r requirements.txt
    
    ```
    
To build the documentation, run the following commands:

    cd api-docs
    make clean singlehtml

To view the HTML build results in the target directory (``_build/html/``), run the following command:

    open _build/html/index.html


### Support and Feedback

If you find a problem, open a Github [issue](https://github.com/rackerlabs/docs-cloud-identity/issues).

If you need additional assistance, drop us a note at 
[devdoc@rackspace.com](mailto:devdoc@rackspace.com).
