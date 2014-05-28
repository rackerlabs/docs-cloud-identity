This repo contains source material for two kinds of documents, intended for two kinds of readers:

- public-facing (Client API) documents are published at http://docs.rackspace.com/api/.
- RAX-internal (Admin API) documents are published at http://docs-internal.rackspace.com/api/.

Within /src/docbkx/, each file is the source for one book. Elements included within books, such as figures, code samples, and sections used in multiple books, are in subdirectories such as /figures/, /samples/ and /chapters/.
To talk about these documents, contact their caretaker: margaret.ekere@rackspace.com


Here's a brief explanation of some of the files you'll find here:

.sh files

These are scripts for publishing to various internal and external sites using common content that draws from other github repos using submodules.

pom.xml

  This is a build file. We use the clouddocs-maven-plugin to build the output. Maven is an Apache project used for building and managing dependencies. Maven uses the Project Object Model (POM) file to describe the project and to specify what the goals of a build should be. The POM file is pom.xml and resides in the project directory above the src directory.

  You use Maven (MVN) to build documents with commands like:
  
  ::
      mvn clean
      mvn generate-sources

  You can also combine the goals with a single command:

  ::
      mvn clean generate-sources

  You can customize the pom.xml file to specify build tasks specified as ''<goals>''.  

Currently, the pom.xml file has been configured to generate web-help (HTML format) and PDF.

src d
In the src directory you find DocBook .xml files, WADL files named .wadl, and various other source files like images, figures, sample .json or .xml requests and responses and so on.
shared files

The shared directory contains information that's common to more than one deliverable such as common concepts or authorization how-to information that's identical across products.

To edit these files, submit a pull request to be reviewed by the document owner.

To build, install Maven (http://maven.apache.org/).

On a Mac, if you have Homebrew (http://brew.sh/) installed, run the brew install command for Maven:

brew install maven 

Or, download the binary zip and follow instructions on the Apache Maven website.

To install Maven 3 for Ubuntu 12.04 and later,and Debian wheezy and later:

::
    apt-get install maven

On Fedora 15 and later:

yum install maven3

You can find much more detailed information in the Writer's Guide.

