<!-- Do not edit this derived file! Rather edit the master file gatein-portal-quickstarts-parent/src/main/readme/jsf2-rf4-hello-world-portlet/README.md.ftl -->

jsf2-rf4-hello-world-portlet: JSF2+RF4 Hello World Portlet
============================
Author: Peter Palaga, Brian Leathem, Ken Finnigan  
Level: Beginner  
Technologies: RF4, JSF2, Portlet Bridge  
Summary: A simple portlet using JavaServer Faces 2.1 and RichFaces 4.2.  
Target Product: 3.4

What is it?
-----------

This project demonstrates how to create a simplest portlet using JavaServer Faces 2.1 and RichFaces 4.2.

Known Issues
------------

[https://issues.jboss.org/browse/GTNPORTAL-2581](GTNPORTAL-2581): When adding this portlet to a page for the first time, 
there comes an alert saying "RichFaces is not defined". The alert can be ignored. Just close it and refresh the page with F5.
A fix is underway for GateIn 3.5.0.Beta01.

<!-- The following content is included from gatein-portal-quickstarts-parent/src/main/readme/include/portlet-general.md.ftl -->

System requirements
-------------------

All you need to build this example project is Java 6.0 (Java SDK 1.6) or newer and Maven 3.0 or newer.

The portlet application this project produces is designed to be deployed on GateIn Portal 3.4 running on either
JBoss AS or JBoss EAP. There is no support for JBoss Enterprise Portal Platform (EPP) yet, but this example projects will evolve
to support the coming EPP version 6.


Configure Maven
---------------

You do not need to touch you settings.xml because of this quickstart. All necessary artifacts are available in public
repositories.


Start the Portal
----------------

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat


Build and Deploy the Quickstart
-------------------------------

1. Make sure you have started the Portal as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean package jboss-as:deploy

   To deploy to other than default localhost:9999 JBoss instance, copy the following configuration 
   just after `<version>${jboss.as.plugin.version}</version>` in the pom.xml file and adjust it to suit your needs.
   `username` and `password` elements can be omitted sometimes, depending on your JBoss security settings.
                 
        <configuration>
            <hostname>127.0.0.1</hostname>
            <port>9999</port>
            <username>admin</username>
            <password>secret</password>
        </configuration>

   This will deploy `target/jsf2-rf4-hello-world-portlet.war` to the running instance of the portal.


Access the deployed Portlet
---------------------------

To ensure that the example portlet has been deployed successfully do the following: 
* Point your web browser at the base URL of your portal (URL of a default local GateIn Portal installation is
[http://127.0.0.1:8080/portal/classic](http://127.0.0.1:8080/portal/classic)).
* Sign in as root or other user with manager:/platform/administrators permissions.
* Go to Top Menu > Group > Administration > Application Registry and hit Import Applications. After that, you should
see the newly imported JSF2+RF4 Hello World Portlet under the jsf2-rf4-hello-world-portlet Category.
* Then you can add the example portlet to a page of your choice: either (a) to a new page or (b) to an existing page.
  * If you have chosen (a) to add the portlet to a new page:
    * Go to Top Menu > Group Editor > Add New Page
    * In the Page Creation Wizard, fill in:
      * Node Name: jsf2-rf4-hello-world-portlet
      * Display Name: JSF2+RF4 Hello World Portlet
    * Click Next
    * Leave Empty Layout as it is and hit Mext
    * Drag-and-Drop Simplest Hello World Portlet from the Page Editor dialog to the middle of the Page Creation Wizard
    * Click the Diskette-like Finish button in the header of the Page Editor dialog and see the newly added portlet in action.
  * If you have chosen (b) to add the portlet to an existing page:
    * Navigate to the page where you want to add the portlet and go to Top Menu > Group Editor > Edit Page
    * Drag-and-Drop Simplest Hello World Portlet from the Page Editor dialog to a place of your choice within the page.
    * Click the Diskette-like Finish button in the header of the Page Editor dialog and see the newly added portlet in action.


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn jboss-as:undeploy


Use JBoss Developer Studio or Eclipse to Run this Quickstart
------------------------------------------------------------
You can also deploy the quickstarts from Eclipse using JBoss tools. For more information on how to set up Maven and the JBoss 
tools, refer to the 
[JBoss Enterprise Application Platform 6 Development Guide](https://access.redhat.com/knowledge/docs/JBoss_Enterprise_Application_Platform/) 
or [Get Started Developing Applications](http://www.jboss.org/jdf/quickstarts/jboss-as-quickstart/guide/Introduction/ "Get Started Developing Applications").


Debug the Application
---------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following 
commands to pull them into your local repository. The IDE should then detect them.

        mvn dependency:sources
        mvn dependency:resolve -Dclassifier=javadoc
