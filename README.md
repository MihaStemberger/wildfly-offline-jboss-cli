Can also be done with wildfly-maven-plugin: https://docs.wildfly.org/wildfly-maven-plugin/execute-commands-example.html#Execute-offline-embedded-CLI-scripts

Offline jboss cli example.

Run `mvn clean package`
 - First, `maven-dependency-plugin` unzips the Wildfly distribution dependency into the target directory(see `target/dependecy`).
 - Then `exec-maven-plugin` executes `cli-runner.sh`, which pipes the `cli-script` to `jboss-cli.sh` found in the unzipped wildfly bin directory

Result is a change of `<socket-binding name="management-http" interface="management" port="${jboss.management.http.port:9990}"/>` inside `standalone.xml`,
 to `<socket-binding name="management-http" interface="management" port="9992"/>`


See more about offline cli at:
https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.0/html/management_cli_guide/running_embedded_server



Tested with:
 - Apache Maven 3.8.6 (Red Hat 3.8.6-4)
 - Java version: 17.0.7
