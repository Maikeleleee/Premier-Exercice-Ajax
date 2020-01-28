Consignes :

- Lancer exercice.html dans le navigateur, ouvrir la console de debug, et cliquez sur l'onglet réseau
- Cliquer sur le bouton présent sur la page pour executer votre premiere requete ajax
- Votre requete ajax va être présente dans l'onglet réseau

- Créer un script php qui echo le texte de votre choix, uploadez sur votre hebergement
- Modifiez la fonction js lançant la requete ajax pour qu'elle effectue une requête vers ce script php au lieu du fichier
data.txt
- Testez => Ca ne fonctionne pas !
- Pourquoi ? : Il n'est pas possible d'éxécuter une requête ajax vers un domaine différent du domaine où est éxécuté
votre javascript pour des raisons de sécurité

- Uploadez tout les fichiers du projet sur webhost puis testez en ligne => Ca marche !






 Théorie :

 Lorsque vous lancez une page web , vous entrez son adresse : monsite.extension/page.extension , du code est éxécuté puis
retourné au visiteur, si le visiteur souhaite visiter une autre page, il clique sur un lien etc...

Ajax est une technologie qui permet de s'affranchir de ce fonctionnement.

Avec Ajax, le visiteur se rends sur une page définie monsite.extension/page.extension, le click sur un lien déclenche alors
une requete ajax qui va récuperer les informations souhaitées puis mettre à jour la page existante, il deviens alors inutile
 pour le visiteur de recharger l'ensemble de la page.

Un bon exemple est le service Gmail de Google, c'est ce qu'on appelle une "one page app"


  Ajax permet donc de :

  - Récuperer des informations depuis un serveur et mettre à jour la page sans la recharger
  - Envoyer des informations au serveur de façon silencieuse ( le visiteur n'a pas d'indications visuelles )

  Voici comment écrire une requete Ajax en Javascript :

    // new XMLHttpRequest() est la méthode qui crée la requête ajax, c'est une instance, cela nous permet d'envoyer
    plusieurs requêtes ajax en même temps
    var xhttp = new XMLHttpRequest();


    // onreadystate change est un événement, nous écoutons cet événement qui éxécute une fonction anonyme pendant l'envoie
    de la reqûete ajax
    xhttp.onreadystatechange = function() {

      // La requete ajax renvoie deux propriétés : readyState et status
      // readyState a différentes valeurs pendant l'envoie de la requete, 4 signifie que la requête est complétée
      // status est le code http renvoyé, 200 signifie que tout s'est bien passé
            if (this.readyState == 4 && this.status == 200) {

                // responseTexte est une propriété renvoyée par la requête ajax, c'est le contenu retourné par la requête
                console.log(this.responseText);
      }
    };


    // La commande open permet de spécifier le protocole utilisé ( GET ou POST ) , l'adresse du script ou du fichier à
    executer, le troisieme parametre détermine si l requête va être envoyée de maniére asynchrone ou synchrone, vous devriez
    toujours laissé ce parametre sur "true" car si la requête est synchrone, tant que la requête ne sera pas terminée,
    le programme javascript sera mis en "pause"
    xhttp.open("GET", "ajax_info.txt", true);

    // la commande send permet d'envoyer la requete
    xhttp.send();



    Note : Une alternative à XMLHttpRequest() existe, fetch() celle ci étant encore experimentale,
    elle ne sera pas utilisée pour le moment.
