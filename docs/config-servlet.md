## Les servlet

Pour configurer un servlet Java, il nous suffit simplement de créer une classe qui hérite de la classe `HttpServlet`. En plus des différentes méthodes HTTP, il est aussi possible de définir les méthodes `init()` et `destroy` qui sont appelées lors de l'initialisation et de le destruction du servlet respectivement.

Pour que la configuration automatique du servlet puisse se faire, on ajoutera l'annotation `@WebServlet` tout en spécifiant les valeurs des attributs `name` et `value`.

```Java
@WebServlet(name = "HelloServlet", value = "/hello")
public class HelloServlet extends HttpServlet {

    private String message;

    public void init() {
        message = "Hello World!";
    }

}
```

--- 
## Méthodes HTTP

Il suffit maintenant de configurer les différentes méthodes HTTP pour permettre de répondre aux requêtes. Chacune des méthodes HTTP (doGet, doPost, etc.) recevra deux (2) paramètres, soît la requête et la réponse de type `HttpServletRequest` et `HttpServletResponse` respectivement.

### Écrire la réponse

Il est possible d'écrire nous même la réponse d'une méthode HTTP. Pour faire cela, il faudra tout d'abord indiquer le type de contenu que nous retournerons, puis de récupérer le flux de sortie de la réponse et d'y écrire le code HTML.

Voici un exemple de la méthode `doGet` du servlet configuré préalablement ci-dessus.

```Java
public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        // Indiquer le typer de contenu
        response.setContentType("text/html");

        // Récupérer le flux de sortie et y écrire le HTML
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>" + message + "</h1>");
        out.println("</body></html>");
    }
```

Bien entendu cet exemple est relativement simple. Nous pourrions également accéder à l'objet `request` afin de récupérer de l'information sur la requête entrante.

Écrire tout le code d'une page HTML via le flux de sortie comme ci-dessus peut rapidement devenir très lourd et plutôt difficile à écrire. Pour tirer avantage des outils que nous avons à notre disposition, nous utiliserons plutôt les pages JSP.

La technologie JSP (Java Server Pages) nous permet d'écrire du code Java dans nos pages HTML, un peu comme les pages Razor (C#) ou Blade (PHP).

Pour demander à un m.thode de servlet de rediriger vers une page JSP, il faudra récupérer le `requestDispatcher`, lui indiquer la page qu'on veut utiliser, puis transférer la requête et la réponse vers cette page.

```Java
public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        request.getRequestDispatcher("/index.jsp").forward(request, response);
    }
```

De cette façon, on redirigerait vers la page `index.jsp`.

!!! info Notez bien
    Notez qu'on pourra passer des informations vers la page en les ajoutant dans l'objet `request`. Les pages JSP ont un accès facile à plusieurs variables dont celle-ci. La section sur les pages JSP contient plus d'informations à cet effet.