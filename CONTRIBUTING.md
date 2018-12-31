# Contributor guidelines

These guidelines provide the general process for maintaining source code that
builds the Rackspace Identity developer documentation.

- [Project description](#project-description)
- [Updating and adding content](#updating-and-adding-content)
- [General style guidelines](#general-style-guidelines)
- [Updating and adding content](#updating-and-adding-content)
- [Submitting your content](#submitting-changes)
- [Reviewing and testing your changes locally](#reviewing-and-testing-your-changes-locally)
- [Previewing changes](#previewing-changes)

##Project description
<!-- Provide as little or as much information about architecture as needed to help
contributors figure out which file to update.-->

This project is developed and built by using the
[Python Sphinx documentation generator](http://sphinx-doc.org/). Content is
written in [reStructuredText](http://sphinx-doc.org/rest.html), which is the
markup syntax and parser component of
[Python Docutils](http://docutils.sourceforge.net/index.html).

Source files for the Sphinx documentation project are in the ``api-docs``
directory. Following are the key files that define project and content
architecture:

Content | File
--- | ---
|Index page for the main content structure| [index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/index.rst)
|About the API index| [overview/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/overview/index.rst)
|Quickstart Guide| [quickstart-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/quickstart-guide.rst)
|Developer Guide introduction|[developer-guide.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/developer-guide.rst)
|Concepts section| [concepts.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/concepts.rst)
|General API information index|[general-api-info/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/general-api-info/index.rst)
|Authentication section index| [authentication-info/index.rst](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/authentication-info)
|API Reference introduction|[api-reference.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-reference.rst)
|API Reference index|[api-operations/index.rst](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/api-operations/index.rst)
|API operations methods, including code samples|[api-operations/methods](https://github.com/rackerlabs/docs-cloud-identity/tree/master/api-docs/api-operations/methods)
|Sphinx documentation configuration file| [conf.py](https://github.com/rackerlabs/docs-cloud-identity/blob/master/api-docs/conf.py) (Typically, this file does not require changes.)
|Linux and OS X build script|``Makefile``|
|Windows build script|``make.bat``|
|Requirements file to support local builds| ``requirements.txt``

## Updating and adding content

Contributions are submitted, reviewed, and accepted by using GitHub pull
requests, following the [GitHub workflow](GITHUBING.md) for this repository.

To update existing source files or add new ones, follow the [GitHub workflow](GITHUBING.md) for this repository.

* Update source files by using the GitHub editor or any plain text editor.
* Format source files with
  [reStructuredText syntax](http://www.sphinx-doc.org/en/stable/rest.html).  
* For quick syntax checking, try the
[Online reStructuredText editor](http://rst.ninjs.org/).


## General style guidelines

When you add or update content, use the following general style guidelines, which are
described in detail in [Style guidelines for technical content](https://github.com/rackerlabs/docs-rackspace/tree/master/style-guide):

- Use [sentence-style capitalization](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/a-l-style-guidelines.md#cap-sentence-style) for titles and headings
- Use consistent [text formatting](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/m-z-style-guidelines.md#text-formatting)
- Write clear and consistent [code examples](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/a-l-style-guidelines.md#code-examples)
- Use [active voice](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#use-active-voice)
- Use [present tense](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#use-present-tense)
- Write to the user by using [second person and imperative mood](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#write-to-user)
- Write clear and consistent [step text](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/m-z-style-guidelines.md#tasks-steps)
- Clarify [pronouns](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#clarify-pronouns) such as *it*, *this*, *there*, and *that*
- Clarify [gerunds and participles](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#clarify-gerunds-and-participles)
- Use [consistent terminology](https://github.com/rackerlabs/docs-rackspace/blob/master/style-guide/basic-writing-guidelines.md#use-consistent-terminology)


## Reviewing and testing your changes locally

Before you submit a PR, build locally to review your changes and
check for syntax, links, spelling, and build errors. You can run tests and
builds by using the Python tox tool (recommended) or the Sphinx
documentation tool.

### Build using tox

Install the [Python tox tool](https://tox.readthedocs.io/en/latest/) to enable a local build environment:

```
$ sudo pip install tox
```

After tox is installed, use the following commands to run tests and build
the handbook.

Commands | Task
--- | ---
| ``$ tox``| Run all checks and builds the docs in a virtualenv (recommended)
|``$ tox -e checkbuild``| Builds the docs without syntax checks (slightly faster):
|``$ tox -e checksyntax``| Check restStructuredText syntax
|``$ tox -e checklinks``| Check restStructuredText syntax
|``$ tox -e checklinks``| Check for broken hyperlinks
|``$ tox -e checkspelling``| Check spelling

For addtional information about using tox, see the
[Rackspace Documentation Guide](http://rackerlabs.github.io/docs-rackspace/tools/rpc-workflow.html#using-tox).


### Build with the Python Sphinx documentation generator

Tox builds the documentation by running the Python documentation generator
``make html`` command.

If you prefer, you can build and troubleshoot errors using the native
Sphinx documentation tool. However, you
need a local installation of the tool and its dependencies. Run the following
command to install everything you need.

```
   $ sudo pip install -r requirements.txt
```

After everything is installed, run the following commands from the root
directory to build the documentation:

```
   $ cd <$root-dir>/docs
   $ make html
```

Run the following command to view the HTML output in the target
directory, ``_build/html/``:

```
   $ open _build/html/index.html
```

## Submitting changes

When you've completed your changes, submit a pull request. Someone on the
Information Development team will review your PR.
- Minor updates and corrections get a quick review to ensure that content is
  error-free and doesn't introduce other issues.
- More complex changes or additions require both technical and editorial
  review.

Depending on the review feedback, you might be asked to make additional
changes.

After content has been reviewed and approved, the updates can be merged to
the master branch. The merge triggers the build and deploy process. Typically,
new content is available on developer.rackspace.com within a minute or two
after it is merged. Larger updates might take a bit longer.

## Previewing changes

When you submit a pull request, the Strider build process creates a preview
of your changes using the templates and layout on developer.rackspace.com.

After the build process completes, the following message displays in the pull
request comments with a link to the content:
``Your content preview is now ready.``
