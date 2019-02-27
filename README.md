Spring Security 5.1 Reactive by Example
------------------

This repo consists of four [Spring Boot WebFlux](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html) applications that are secured using [Spring Security](https://docs.spring.io/spring-security/site/docs/current/reference/htmlsingle/) and [OAuth 2.0](https://oauth.net/2/).

For the application to work, please take the following steps after cloning to your local machine:

1. Modify your /etc/hosts file

    The demo code points to the endpoint `idp:9999` for the Identity Provider. So, your machine can resolve this
    hostname on its own by adding the following to `/etc/hosts`:

    ```bash
    127.0.0.1   idp
    ```

    You may need `sudo` privileges to edit the file.

2. Start the keycloak docker container

    These demos work with a pre-configured Authorization Server, which you can start up with the following command:

    ```bash
    docker run -d  --name=keycloak -p 9999:8080 jzheaux/keycloak-spring-security-reactive-demo
    ```

    Thereafter, you can stop this server with:

    ```bash
    docker stop keycloak
    ```

    And start it with:

    ```bash
    docker start keycloak
    ```

3. Start the servers

    There are four servers, `message`, `user`, `inbox`, `gateway`.
    To start each one, you can simply run from the command line from each directory:

    ```bash
    ../mvnw spring-boot:run
    ```

4. Use the application:

    When you navigate to http://localhost:8080, you'll be invited to authenticate. You can do:

    * rob / password
    * joe / password
    * josh / password

Also, take a look at [the Java to HTTP mappings](https://gist.github.com/rwinch/cd1b459d6e04d30d72edb7e6919b3cbb) for the Spring Security-powered OAuth 2.0 handshakes.