<!-- ### 3.2.1 Serious problems -->

#### Migrate JBoss login modules

This rule points at the elements `<security-domain>` contained in the jboss-web.xml file and the elements `<login-config>` contained in the web.xml  file to let you know that you have to configure the security for the application.

To protect the application you can add users and groups that you need into the predetermined users register and assign them roles. In Liberty, the users registry can be configured by defining an element basicRegistry in the server.xml file.
As an alternative, a file based registry can be configured, an LDAP registry or a personalised registry. Moreover, security settings can be configured for your working environment by creating security domains.

The application can use JAAS login modules. If a login module is being used, the name of the class is defined in the jboss-web.xml file by an element `<valve>` inside an element `<security-domain>` or in the conf/login-config.xml file by an element called `<login-config>`. If a JBoss Application Server login module or a specific APIs are being used, the WAS Application server modules should be replaced and configured again.

#### Do not use JBoss specific packages

Packages like org.jboss contain specific JBoss APIs. When your application uses classes contained in these packages, the code must be changed to use the APIs provided by the Java Development Kit (JDK), the APIs provided by WebSphere (R) Application Server, or the open source APIs.

Although it is not prohibited for package names in your code to start with org.jboss, these declarations are also flagged. Refactor these names so that they do not interfere with JBoss server API flags.

##### Solution

Evaluate your code using the specific JBoss API and change it to a non-proprietary API or a WebSphere Application Server API.

#### Do not use JBoss specific name search strings

This rule marks the usage of a series of names searches of JBOSS owners who starts by the name of `java`. This also includes `java:jboss, java:jdbcy, java: or java:/` given that the following content Jboss specific values.

For example look at the following lines:

* ds = (DataSource) ctx.lookup("java:" + getLookupName());
* ds = (DataSource) ctx.lookup("java:jboss/Test");
* ds = (DataSource) ctx.lookup("java:global");

The rule marks `java:" and "java:jboss/Test", except for "java:global"`. Even though the rule marks the `java` serie, we might not need to migrate it. In the example above let's check
#### Use WebSphere extensions to define the context root of the web module

For stand-alone web module files, the application context root can be specified in the JBoss deployment descriptor, `jboss-web.xml`. This rule detects the presence of the `<context-root>` element in the `jboss-web.xml` file. In source explorer, the quick fix applies this value to the Liberty or traditional WebSphere extension file.

Looking at the business applications archives, the context root's information of the deployment descriptor `application.xml` for the EAR archive is preferred to the context root of the deployment descriptor for the web module.
This quick solution copies the context root's information although its value it is not used.

<!-- En el caso de los archivos de aplicación empresarial, la información de la raíz de contexto del descriptor de despliegue application.xml para el archivo EAR tiene preferencia sobre la raíz de contexto del descriptor de despliegue para el módulo web. Este arreglo rápido copia la información de la raíz de contexto aunque el valor no se utilice debido a la presencia de un archivo application.xml.  -->
