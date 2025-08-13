## Dépendences fréquemment utilisées

???+ info "Disponibles lors de la génération du projet"
    - Developer Tools
        - Lombok (Création plus rapide des classes)
        - Spring Configuration Processor (Donne l'auto complétion lors de la configuration des propriétés)
    - Web
        - Spring Web (Apporte les fonctionalités nécessires aux application web)
    - SQL
        - Sring Data JPA (ORM, permet une gestion "code first" de la base de données)
        - MySQL Driver (Permet la connexion à une BD MySQL)
    -Security
        - Spring Security (Dépendance de base pour la sécurité) 
        - OAuth2 Resource Server (Fonctionalités pratiques pour la gestion des API et des mécanismes d'authetification à l'aide de jetons (tokens))

??? info "Pour utiliser les pages JSP"
    - Serveur pour les pages JSP
    ```xml
    <dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-jasper</artifactId>
        <scope>provided</scope>
    </dependency>
    ```
    - Balises JSTL (taglib)
    ```xml
    <dependency>
            <groupId>org.eclipse.jetty</groupId>
            <artifactId>apache-jstl</artifactId>
            <version>11.0.0</version>
        </dependency>
    ```

??? info "Pour utiliser SQLite"
    - Driver pour SQLite
    ```xml
    <dependency>
        <groupId>org.xerial</groupId>
        <artifactId>sqlite-jdbc</artifactId>
    </dependency>
    ```
    - Dialecte pour le connecteur
    ```xml
    <dependency>
        <groupId>org.hibernate.orm</groupId>
        <artifactId>hibernate-community-dialects</artifactId>
    </dependency>
    ```