class: center, middle

# Les IHM et le langage Java
### Henri GARRETA & Cyril PAIN-BARRE & Sébastien NEDJAR 
![IUT](logo.png)
---

class: center, middle

# Cours 2: JavaFX

---
# Historique
- A l'origine du langage Java, les interfaces graphiques étaient créées
en utilisant **la bibliothèque AWT** (`java.awt`).

    - Composants "lourds" (heavyweight) basés sur ceux de la machine cible.
    - Difficulté de créer des applications réellement multiplateformes (write once, run anywhere), lourdeur.
    
- Rapidement, **la bibliothèque Swing** (`javax.swing`) est venue compléter (et partiellement remplacer) AWT.

    - Composants "légers" (lightweight) dessinés par la bibliothèque
    - Pluggable Look&Feel
    
- **JavaFX 1** a tenté – sans grand succès – de remplacer Swing.

    - Essentiellement basé sur un (nouveau) langage de script (JavaFX Script).
    - Vaine tentative pour concurrencer Flex (basé sur Flash et MXML).
---
# Historique
- Une refonte importante du *toolkit* a pris en compte les critiques formulées et a conduit à une nouvelle mouture : **JavaFX 2**

- Caractéristiques principales :

    - Abandon du langage de script *JavaFX Script*
    
    - Choix de deux modes : interfaces basées sur du code Java (API) et/ou sur un langage descriptif utilisant une syntaxe *XML*
    
    - Création d'un outil interactif **Scene Builder** pour créer graphiquement des interfaces et générer automatiquement du code FXML
    
    - Utilisation possible de feuilles de styles CSS pour adapter la présentation sans toucher au code (créer des thèmes, des skins, etc.)
    
    - Application du modèle de conception (design pattern) Builder avec un chaînage de méthodes (Fluent API)
 
---
# Historique
- Avec la sortie de Java 8, une nouvelle version baptisée JavaFX 8 a été
développée : 
    - Intégration dans la distribution de la plateforme Java SE. Plus de librairie externe à télécharger.
    
    - **Scene Builder 2** : nouvelle version de l'outil d'édition graphique de GUI (FXML)
    
    - Prise en compte des nouveaux concepts introduits en Java 8 et notamment les expressions lambda et les streams. 
    
    - Ajout de composants riches (`DatePicker`, `TreeTableView`, ...)
    
    - Gestion des écrans tactiles (`TouchEvent`, `GestureEvent`, ...)
    
    - Amélioration des librairies graphiques 2D et 3D
    
    - Ajout d'un outil de packaging
    
    - **JavaFX** devient le standard officiel pour le développement des interfaces des applications Java
 
---
# Potentiel de JavaFX
- **JavaFX** étant le résultat de développements récents, il bénéficie de concepts modernes qui en font un framework intéressant pour la réalisation d'applications dans des domaines très divers.

- **JavaFX** est très bien doté pour développer des interfaces riches en relation avec des données stockées dans des bases de données ou accessibles au travers de serveurs d'informations.

- Sa riche librairie graphique 2D et 3D lui donne également un intéressant potentiel dans des domaines variés :

    - Représentations graphiques
    
    - Animations graphiques
    
    - Modélisation (CAD, …)
    
    - Applications multimédia
    
    - Réalité virtuelle et augmentée
    
    - Jeux
 
---
# Potentiel de JavaFX
- La possibilité de découpler le design graphique (grâce à l'outil **Scene Builder** et à **FXML**) permet de déléguer la conception graphique de l'interface à un spécialiste (UI designer) qui n'a pas l'obligation de connaître et maîtriser le langage Java et ses librairies (API).

- L'application possible de feuilles de style CSS renforce encore cette séparation entre le design graphique et les traitements qui seront effectués à l'aide de code Java.

- Différents composants complexes sont disponibles et permettent, avec un minimum d'effort, de créer des applications riches :

    - Effets visuels (ombrages, transitions, animations, …)
    
    - Graphiques 2D (**charts**)
    
    - Navigateur web (**WebKit**)
    
    - Images, audio, vidéo (media player)
 
 
---
# Potentiel de JavaFX 
- Actuellement, de nombreuses applications sont des applications web, basées sur les technologies HTML5 + CSS + JavaScript (avec un grand nombre de frameworks disponibles) ou sur Flash/Flex ou Silverlight (les deux derniers cités étant clairement en perte de vitesse).

- Une comparaison détaillée entre ces technologies web et JavaFX sort du cadre de ce cours mais plusieurs billets de blog et documents décrivent les caractéristiques ainsi que les avantages et inconvénients de ces différentes approches technologiques, par exemple :

    - Introduction du livre Mastering JavaFX 8 Controls, Hendrik Ebbers, Oracle Press, 2014

    - Blog Code Makery : http://code.makery.ch/blog/javafx-vs-html5
---

# IHM déclaratives vs procédurales 
La plateforme JavaFX offre deux techniques complémentaires pour
créer les interfaces graphiques (IHM) des applications

**Manière déclarative :**
- En décrivant l'interface dans un fichier FXML (syntaxe XML)

- L'utilitaire graphique **Scene Builder** facilite la création des fichiers FXML

- L'interface peut être créée par un designer

- Séparation entre présentation et logique de l'application (MVC)

**Manière procédurale :**
- Utilisation d'API pour construire l'interface avec du code Java

- Création et manipulation dynamique des interfaces

- Création d'extensions et variantes (par héritage)

- Homogénéité des sources de l'application

---
# Déploiement
Une application JavaFX peut être déployée (mise à disposition des
utilisateurs) de différentes manières :

- **Installée localement** comme une application autonome (standalone/desktop application)
    - Semblable à une application native
    
    - La machine virtuelle Java peut être intégrée ou non dans l'exécutable (.exe ou .jar)
    
- **Installée sur un serveur** et intégrée dans une page web
    - Lancée depuis un navigateur, en cliquant sur un lien ou sur un autre élément actif de la page
    
    - Lancée automatiquement dès qu'une page est chargée
    
    - Utilise la technique **Java Web Start** (fichier JNLP + descripteur de déploiement XML)
    
    - Une fois téléchargée, l'application peut également être lancée hors-connexion (mise en cache local)
    
---
# Projets connexes
 
- JavaFX devrait, à terme, être totalement publié en open-source (ce n'est que partiellement le cas) dans le cadre du projet OpenJFX.

- De nombreux projets contribuent à enrichir l'écosystème JavaFX.

- Parmi les principaux (et les plus dynamiques) on peut mentionner :

    - **[ControlsFX](https://github.com/controlsfx/controlsfx)** : Projet open-source destiné à offrir des composants supplémentaires de qualité

    - **[JFXtras](http://jfxtras.org/)** : Projet open-source destiné à fournir aux développeurs des éléments utiles dans leur vie de tous les jours et qui manquent dans la version de base de JavaFX

    - **[DataFX](https://bitbucket.org/datafx/datafx/src/default/README.md)** : Projet open-source destiné à faciliter la collaboration entre une application JavaFX et un système de gestion des données (BD, …)

    - **[TestFX](https://github.com/TestFX)** : Librairie pour automatiser le test des applications JavaFX
    
---
# Références
Quelques références web utiles :
 - [Tutoriel officiel Oracle](http://docs.oracle.com/javase/8/javase-clienttechnologies.htm)
 
 - [FX-Experience](http://fxexperience.com) : Blog géré par des experts du domaine (news, demos, …)
 
 - Autre [blog dédié](http://guigarage.com) à différentes thématiques JavaFX
 
 - Communauté des développeurs du projet open-source [OpenFJX](https://openjfx.io/) (qui est un sous-projet de OpenJDK)
 
 - [API JavaFX (Javadoc)](https://openjfx.io/javadoc/11/)
---
# Références
Quelques livres :

- **Learn JavaFX 8 - Building User Experience and Interfaces with Java 8** - Kishori Sharan, Apress, 2015. ISBN: 978-1484211434

- **Pro JavaFX 8 - A Definitive Guide to Building Desktop, Mobile, and Embedded Java Clients** - James Weaver, Weiqi Gao, Stephen Chin, Dean Iverson,
Johan Vos, Adrian Chin, Apress, 2014. ISBN: 978-1430265740

- **JavaFX 8 - Introduction by Example** - Carl Dea et Mark Heckler, Apress, 2014. ISBN: 978-1430264606

- **Mastering JavaFX 8 Controls** - Hendrik Ebbers, McGraw-Hill Professional - Oracle Press, 2014. ISBN: 978-0071833776

---

class: center, middle

# Première immersion !

---
# Première application

- Comment se présente une application JavaFX ? (petite immersion avant de décrire plus en détail les concepts de base).

- L'application est codée en créant une sous-classe de `Application`.

- La fenêtre principale d'une application est représentée par un objet de type `Stage` qui est fourni par le système au lancement de l'application.

- L'interface est représentée par un objet de type `Scene` qu'il faut créer et associer à la fenêtre (`Stage`).

- La scène est composée des différents éléments de l'interface graphique(composants de l'interface graphique) qui sont des objets de type `Node`.

- La méthode `start()` construit et lance le tout.

---
# Métaphore de la salle de spectacle

Les éléments structurels principaux d'une application JavaFX se basent sur la métaphore de *la salle de spectacle*

Remarque : En français, on utilise le terme 'scène' pour parler de l'endroit où se passe le spectacle (l'estrade, les planches) mais également pour parler de ce qui s'y déroule (jouer ou tourner une scène) ce qui peut conduire à un peu de confusion avec cette métaphore.

- **Stage** : L'endroit où a lieu l'action, où se déroule la scène

- **Scene** : Tableau ou séquence faisant intervenir les acteurs

- **Nodes** : Acteurs, figurants, éléments du décor, … (éléments actifs/passifs) qui font partie de la scène en train d'être jouée.

---
# Hello World !
Une première application, le traditionnel Hello World !

```java
public class HelloWorld extends Application {

   @Override
   public void start(Stage primaryStage) {
      primaryStage.setTitle("My First JavaFX App");
      BorderPane root = new BorderPane();
      Button btnHello = new Button("Hello World");
      root.setCenter(btnHello);
      Scene scene = new Scene(root, 250, 100);
      primaryStage.setScene(scene);
      primaryStage.show();
   }

   public static void main(String[] args) {
      launch(args);
   }
}
```
---
# Hello World ! 
 - JavaFX étant intégré à la plateforme de base Java, aucune librairie externe n'est nécessaire au fonctionnement de l'exemple précédent.

 - Un certain nombre d'importations doivent cependant être effectuées (on y retrouve les classes principales `Application`, `Stage`,
`Scene` ainsi que les composants `BorderPane` et `Button`) :

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.BorderPane;
import javafx.stage.Stage;
```
- Dans cet exemple, la méthode `main()` lance uniquement la méthode statique `launch()` (qui est définie dans la classe `Application`).

- Dans une application un peu plus complexe, elle pourrait effectuer d'autres opérations d'initialisation avant l'invoquer `launch()`.

---
# Cycle de vie d'une application
- Le point d'entrée d'une application JavaFX est constitué d'une instance de la classe Application (généralement une sous-classe).

- Lors du lancement d'une application par la méthode statique `Application.launch()`, JavaFX effectue les opérations suivantes :

    1. Crée une instance de la classe qui hérite de `Application`
    
    2. Appelle la méthode `init()`
    
    3. Appelle la méthode `start()` et lui passe en paramètre une instance de `Stage` (qui représente la fenêtre principale)
    4. Attend ensuite que l'application se termine; cela se produit lorsque :
     - La dernière fenêtre de l'application a été fermée (et `Platform.isImplicitExit()` retourne `true`)
     - L'application appelle `Platform.exit()` (ne pas utiliser `System.Exit()`)
    5. Appelle la méthode `stop()` 
    
---
# Cycle de vie d'une application
- La méthode `launch()` est généralement lancée depuis la méthode `main()`. Elle est implicitement lancée s'il n'y a pas de méthode `main()` (ce qui est toléré depuis Java 8).

- D'éventuels paramètres de lancement peuvent être récupérés en invoquant la méthode `getParameters()` dans la méthode `init()` ou ultérieurement (par ex dans la méthode `start()`).

- Au lancement d'une application JavaFX, il est possible de passer des paramètres nommés (syntaxe `--name=value`) ou anonymes :
```sh
java -jar Hello.jar --steps=50 --mode=Debug 300 FR
```
- `getParameters()` retourne un objet de type `Parameters` dont on peut extraire les valeurs des paramètres à l'aide des méthodes :
    - `List<String> getRaw()` : Liste brute de tous les paramètres
    - `Map<String, String> getNamed()` : Liste des paramètres nommés
    - `List<String> getUnnamed()` : Liste des paramètres anonymes
    
---
# Cycle de vie d'une application

- La méthode `start()` est abstraite et doit donc être redéfinie. 

- Les méthodes `init()` et `stop()` ne doivent pas obligatoirement être
redéfinies (par défaut elle ne font rien).

- La méthode `start()` s'exécute dans le *JavaFX Application Thread*. C'est dans ce thread que doit être construite l'interface (notamment la création de l'objet `Scene`) et que doivent être exécutées toutes les opérations qui agissent sur des composants attachés à une scène placée dans une fenêtre (live components).

- La méthode `stop()` s'exécute aussi dans le *JavaFX Application Thread*.

- La méthode `init()` ainsi que le constructeur de la classe qui étend `Application` s'exécutent par contre dans le thread *JavaFX Launcher*. Il est possible d'y créer des composants et des conteneurs mais on ne peut pas les placer dans une scène active (live scene).

---
# Traiter une action de l'utilisateur

- Dans l'exemple **Hello World**, pour que le clic sur le bouton déclenche une action, il faut traiter l'événement associé.

- La méthode `setOnAction()` du bouton permet d'enregistrer un *Event Handler* (c'est une interface fonctionnelle possédant la méthode `handle(event)` qui définit l'action à effectuer).

```java
public void start(Stage primaryStage) {
   primaryStage.setTitle("My First JavaFX App");
   BorderPane root = new BorderPane();
   Button btnHello = new Button("Say Hello");
   
   btnHello.setOnAction( event -> System.out.println("Hello World !"));
   
   root.setCenter(btnHello);
   Scene scene = new Scene(root, 250, 100);
   primaryStage.setScene(scene);
   primaryStage.show();
}
```
---

class: center, middle

# Propriétés
---
# Notion de propriété
- La notion de "propriété" (property) est centrale dans JavaFX.

- Une **propriété** est un élément d'une classe que l'on peut manipuler à l'aide de *getters (lecture)* et de *setters (écriture)*.

- Les propriétés sont généralement représentées par des attributs de la classe mais elles pourraient aussi être stockées dans une base de données ou autre système d'information.

- En plus des méthodes `getXXX()` et `setXXX()`, les propriétés JavaFX possèdent une troisième méthode `XXXProperty()` qui retourne un objet qui implémente l'interface `Property` \[XXX : nom de la propriété \].

- Intérêt des propriétés :
    - Elles peuvent être liées entre-elles *(Binding)*, c.-à-d. que le changement d'une propriété entraîne automatiquement la mise à jour d'une autre.

    - Elles peuvent déclencher un événement lorsque leur valeur change et un gestionnaire d'événement *(Listener)* peut réagir en conséquence.
    
---
# Notion de propriété
Exemple d'une classe définissant la propriété balance (solde) pour
un compte bancaire :

```java
public class BankAccount {
   private DoubleProperty balance = new SimpleDoubleProperty();
   
   public final double getBalance() {
      return balance.get();
   }

   public final void setBalance(double amount) {
      balance.set(amount);
   }

   public final DoubleProperty balanceProperty() {
      return balance;
   }

}
```
---
# Notion de propriété
- La classe abstraite `DoubleProperty` permet d'emballer une valeur de type double et d'offrir des méthodes pour consulter et modifier la valeur mais également pour *"observer"* et *"lier"* les changements.

- `SimpleDoubleProperty` est une classe concrète prédéfinie.

- La plateforme Java offre des classes similaires pour la plupart des types primitifs, les chaînes de caractères, certaines collections ainsi que le type `Object` qui peut couvrir tous les autres types.

    - `IntegerProperty` / `SimpleIntegerProperty`
    
    - `StringProperty` / `SimpleStringProperty`
    
    - `ListProperty<E>` / `SimpleListProperty<E>`
    
    - `ObjectProperty<T>` / `SimpleObjectProperty<T>`
    
- Des classes existent également pour définir des propriétés read-only (`ReadOnlyIntegerWrapper`, `ReadOnlyIntegerProperty`, ...)

---
# Propriétés read-only

- Il existe des propriétés qui sont en lecture seule (*read-only property*).

- La création de telles propriétés nécessite l'utilisation de classes *wrappers*. Elle servent à isoler la partie de la propriété en lecture seule (visible de l'extérieur) de la partie qui permet de modifier la valeur de la propriété.

- La modification de la valeur de la propriété doit être possible uniquement dans le composant (*bean*) qui définit cette propriété.

- A l'intérieur du wrapper, la propriété en lecture seule est en réalité liée (*bound*) à une autre propriété interne qui est, elle, en lecture et écriture

---
# Propriétés read-only

Exemple d'une classe définissant la propriété balance (solde) pour
un compte bancaire en lecture seule (read-only).
```java
public class BankAccount {
   
   private ReadOnlyDoubleWrapper balance = new ReadOnlyDoubleWrapper();
   
   public final double getBalance() {
      return balance.get();
   }
   
   public final void addInterests(double interestsRate) {
      double newBalance = balance.get() * (1+interestsRate);
      balance.set(newBalance);
   }
   
   public final ReadOnlyDoubleProperty balanceProperty() {
      return balance.getReadOnlyProperty();
   }

}
```

---
# Observation des propriétés

- Toutes les classes de propriétés implémentent l'interface `Observable` et offrent de ce fait, la possibilité d'enregistrer des observateurs (`Listener`) qui seront avertis lorsque la valeur de la propriété change.

- Une instance de l'interface fonctionnelle `ChangeListener<T>` pourra ainsi être créée pour réagir à un tel changement. La méthode `changed()` sera alors invoquée et recevra en paramètre la valeur observée ainsi que l'ancienne et la nouvelle valeur de la propriété.

```java
DoubleProperty sum = account.balanceProperty();
sum.addListener( (ObservableValue<? extends Number> obsVal,
                  Number oldVal,
                  Number newVal ) ->
                  {
                     //--- ChangeListener code
                     System.out.println(oldVal+" becomes "+ newVal);
                     . . .
                  } );
```

*Ici une expression lambda est utilisée pour implémenter la méthode `changed()`. On pourrait également utiliser une classe anonyme ou créer l'instance d'une classe "ordinaire" qui implémente l'interface `ChangeListener<T>`.*

---
# Observation des propriétés
- L'interface fonctionnelle `InvalidationListener<T>` permet également de réagir aux changements des valeurs de propriétés dans les situations où les propriétés sont calculées à partir d'autres et que l'on veut éviter d'effectuer les calculs à chaque changement.

- Avec cette interface, c'est la méthode `invalidated(Observable o)` qui est invoquée lorsqu'un changement potentiel de la valeur de la propriété est intervenu.

- Cette méthode peut cependant être invoquée alors que le résultat observé n'a finalement pas changé (cela dépend des opérations effectuées)

- Les composants utilisés dans les interfaces graphiques (boutons, champs texte, cases à cocher, sliders, etc.) possèdent tous de nombreuses propriétés.

- Pour chacun des composants, la documentation (*Javadoc*) décrit dans une des rubriques (*Property Summary*) la liste des propriétés de la classe concernée ainsi que celles qui sont héritées.

---
# Lier des propriétés
- Un des avantages des propriétés JavaFX est la possibilité de pouvoir les lier entre-elles. Ce mécanisme, appelé **binding**, permet de mettre à jour automatiquement une propriété en fonction d'une autre.

- Dans les interfaces utilisateurs, on a fréquemment ce type de liens. Par exemple, lorsqu'on déplace le curseur d'un slider, la valeur d'un champ texte changera (ou la luminosité d'une image, la taille d'un graphique, le niveau sonore, etc.).

- Il est possible de lier deux propriétés **A** et **B** de manière

    - *Unidirectionnelle* : un changement de **A** entraînera un changement de **B** mais pas l'inverse (**B** non modifiable autrement).

    - *Bidirectionnelle* : un changement de **A** entraînera un changement de **B** et réciproquement (les deux sont modifiables).
    
---
# Lier des propriétés
- La méthode `bind()` permet de créer un lien unidirectionnel.

- La méthode doit être appelée sur la propriété qui sera *"soumise"* à l'autre (celle qui est passée en paramètre). 

```java
BankAccount account = new BankAccount();
Slider slider = new Slider();
slider.valueProperty().bind(account.balanceProperty());
```

- Dans cet exemple la position du curseur du slider est liée (asservie) à la valeur du solde du compte bancaire. 

- Si l'on tente de modifier la valeur de la propriété associée à la position du slider (qui deviendra non-éditable) d'une autre manière, une exception sera générée.

- Une liaison bidirectionnelle s'effectue de manière similaire, mais en utilisant la méthode `bindBidirectional()`.
---
# Lier des propriétés
- Une propriété ne peut être liée (asservie) qu'à une seule autre si le lien est unidirectionnel (`bind()`). Par contre, les liens bidirectionnels (`bindBidirectional()`) peuvent être multiples.

- Parfois, une propriété dépend d'une autre mais avec une relation plus complexe. Il est ainsi possible de créer des **propriétés calculées**.

- Deux techniques (dites de "haut-niveau") sont à disposition (elles peuvent être combinées) :

    - Utiliser la classe utilitaire `Bindings` qui possède de nombreuses méthodes statiques permettant d'effectuer des opérations.

    - Utiliser les méthodes disponibles dans les classes qui représentent les propriétés; ces méthodes peuvent être chaînées (Fluent API).

- Des opérations de conversions sont parfois nécessaires si le type des propriétés à lier n'est pas le même. Par exemple pour lier un champ texte (`StringProperty`) à un slider dont la valeur est numérique (`DoubleProperty`). 

---
# Lier des propriétés
Exemples de binding permettant de coupler la valeur d'un slider (`Area`) aux valeurs de deux autres (`Width` et `Height`)

En utilisant les méthodes statiques de la classe `Bindings` :
```java
Slider widthSlider = new Slider(); // Input
Slider heightSlider = new Slider(); // Input
Slider areaSlider = new Slider(); // Ouput
DoubleProperty widthPty = widthSlider.valueProperty();
DoubleProperty heightPty = heightSlider.valueProperty();
DoubleProperty areaPty = areaSlider.valueProperty();

areaPty.bind(Bindings.multiply(widthPty, heightPty));
```
Même exemple, en utilisant des méthodes chaînées (Fluent API) :
```java
Slider widthSlider = new Slider(); // Input
Slider heightSlider = new Slider(); // Input
Slider areaSlider = new Slider(); // Ouput
DoubleProperty widthPty = widthSlider.valueProperty();
DoubleProperty heightPty = heightSlider.valueProperty();
DoubleProperty areaPty = areaSlider.valueProperty();

areaPty.bind(widthPty.multiply(heightPty));
```
---
# Lier des propriétés

Un jeu d'opérations est disponible aussi bien avec la classe `Bindings` qu'avec les méthodes chaînables :
- `min()`, `max()`

- `equal()`, `notEqual()`, `lessThan()`, `lessThanOrEqual()`, …

- `isNull()`, `isNotNull()`, `isEmpty()`, `isNotEmpty()`, …

- `convert()`, `concat()`, `format()`, …

- `valueAt()`, `size()`, …

- `when(cond).then(val1).otherwise(val2)` 

- et beaucoup d'autres
---
# Lier des propriétés

Si les opérations disponibles dans les API, dites de haut-niveau, ne permettent pas d'exprimer la relation entre les propriétés, il est possible de définir une liaison de plus bas niveau (*low-level binding*) en redéfinissant la méthode abstraite `computeValue()` d'une des classes de binding (`DoubleBinding`, `BooleanBinding`, `StringBinding`, …).

```java
DoubleBinding complexBinding = new DoubleBinding() {
   { //--- Set listeners to 'in'-properties
      super.bind(aSlider.valueProperty(), bSlider.valueProperty());
   }
   
   @Override //--- Compute 'out' value
   protected double computeValue() {
      double w = aSlider.valueProperty().get();
      double h = bSlider.valueProperty().get();
      return Math.sqrt(h) * Math.pow(w, 3);
   }
};

outSlider.valueProperty().bind(complexBinding); // Do the binding
```
---
class: center, middle

# Structure d'une application JavaFX
---
# Graphe de scène
- Le graphe de scène (*scene graph*) est une notion importante qui représente la structure hiérarchique de l'interface graphique.

- Techniquement, c'est un graphe acyclique orienté (arbre orienté) avec :
    - une racine (*root*)
    
    - des nœuds (*nodes*)
    
    - des arcs qui représentent les relations parent-enfant
    
- Les nœuds (nodes) peuvent être de trois types :
    - Racine
    
    - Nœud intermédiaire
    
    - Feuille (*leaf*)
---
# Graphe de scène
- Les feuilles de l'arbre sont généralement constitués de composants visibles (boutons, champs texte, …) et les nœuds intermédiaires (y compris la racine) sont généralement des éléments de structuration, typiquement des conteneurs (`HBox`, `VBox`, `BorderPane`, …).

- Tous les éléments contenus dans un graphe de scène sont des objets qui ont pour classe parente la classe `Node`. Parmi les sous-classes de `Node` on distingue différentes familles :

     - Les formes primitives (*Shape*) 2D et 3D : `Line`, `Circle`, `Rectangle`, `Box`, `Cylinder`, …

     - Les conteneurs (*Layout-Pane*) qui se chargent de la disposition (*layout*) des composants enfants et qui ont comme classe parente `Pane` : `AnchorPane`, `BorderPane`, `GridPane`, `HBox`, `VBox`, …

     - Les composants standard (*Controls*) qui étendent la classe `Control` : `Label`, `Button`, `TextField`, `ComboBox`, …

     - Les composants spécialisés qui sont dédiés à un domaine particulier (par exemple : lecteur multimédia, navigateur web, etc.) : `MediaView`, `WebView`, `ImageView`, `Canvas`, `Chart`, …

---
# Les conteneurs

- Les conteneurs (*Layout-Pane*) représentent une famille importante parmi les sous-classes de `Node`. Ils ont pour classe parente `Pane` et `Region` qui possèdent de nombreuses propriétés et méthodes héritées par tous les conteneurs.

- La qualité d'une interface graphique repose sur de nombreux éléments mais la disposition des composants dans la fenêtre figure certainement parmi les plus importants.

- Dans la création des graphes de scène, les conteneurs (appelés *layout-panes* ou parfois simplement *layouts* ou *panes*) jouent donc un rôle important dans la structuration et la disposition des composants qui seront placés dans les interfaces.

- En fonction du design adopté (phase de conception de l'interface), il est important de réfléchir au choix des conteneurs qui permettront au mieux de réaliser la mise en page souhaitée.

---
# HBox
- Le layout `HBox` place les composants sur une ligne horizontale. Les composants sont ajoutés à la suite les uns des autres (de gauche à
droite).

- L'alignement des composants enfants est déterminé par la propriété `alignment`, par défaut `TOP_LEFT` (type énuméré `Pos`).

- L'espacement horizontal entre les composants est défini par la propriété `spacing` (`0` par défaut). La valeur de cette propriété peut
être passée en paramètre au constructeur (`new HBox(8)`).

- Si possible, le conteneur respecte la taille préférée des composants. Si le conteneur est trop petit pour afficher tous les composants à
leur taille préférée, il les réduit jusqu'à `minWidth`.

---
# HBox

- L'ajout des composants enfants dans le conteneur s'effectue en invoquant d'abord la méthode générale `getChildren()` qui retourne la liste des enfants du conteneur et en y ajoutant ensuite le composant considéré (méthodes `add()` ou `addAll()`) :

```java
HBox root = new HBox();
root.getChildren().add(btnA);
root.getChildren().addAll(btnOk, btnQuit);
```

- Des méthodes statiques de HBox peuvent être invoquées pour appliquer des contraintes de positionnement :
    - `hgrow()` : permet d'agrandir le composant passé en paramètre jusqu'à sa taille maximale selon la priorité (`Priority`) donnée
    
    - `margin()` : fixe une marge (objet de type `Insets`) autour du composant passé en paramètre (zéro par défaut `Insets.EMPTY`)
    
---
# HBox
<img src="slide43.png" style="position: absolute; left: 600px;  top: 10px;" >
Exemple (déclaration des composants et code de la méthode `start()`) :
```java
private HBox root;
private Button btnA = new Button("Alpha");
private Label lblB = new Label("Bravo");
private ComboBox<String> cbbC = new ComboBox<>();

@Override
public void start(Stage primaryStage) {
   primaryStage.setTitle("Test HBox");
   
   root = new HBox(10); // Horizontal Spacing : 10
   
   root.setAlignment(Pos.CENTER);
   root.getChildren().add(btnA);
   root.getChildren().add(lblB);
   
   cbbC.getItems().addAll("Charlie", "Delta");
   cbbC.getSelectionModel().select(0);
   
   root.getChildren().add(cbbC);
   
   primaryStage.setScene(new Scene(root, 300, 100));
   primaryStage.show();
}

```

---
# VBox
<img src="slide44.png" style="position: absolute; left: 700px;  top: 10px;" >
- Le layout `VBox` place les composants verticalement, sur une colonne. Les composants sont ainsi ajoutés à la suite les uns des autres.

- Toutes les propriétés et méthodes décrites pour le conteneur `HBox` s'appliquent également au conteneur `VBox` avec seulement quelques adaptations assez évidentes. 

- Exemple :

```java
private VBox root;
private Button btnA = new Button("Alpha");
private Label lblB = new Label("Bravo");
private ComboBox<String> cbbC = new ComboBox<>();

@Override
public void start(Stage primaryStage) {
   primaryStage.setTitle("Test VBox");
   VBox.setVgrow(btnA, Priority.ALWAYS);
   root = new VBox(10); // Vertical Spacing : 10

   // Initialisation et ajout des composants comme au transparent précédent

   primaryStage.setScene(new Scene(root, 100, 100));
   primaryStage.show();
}

```

---
# FlowPane 
- Le layout `FlowPane` place les composants sur une ligne horizontale ou verticale et passe à la ligne ou à la colonne suivante (*wrapping*) lorsqu'il n'y a plus assez de place disponible.

- Un des paramètres du constructeur (de type `Orientation`) détermine s'il s'agit d'un `FlowPane` horizontal (par défaut) ou vertical.

- L'ajout des composants enfants dans un conteneur `FlowPane` s'effectue en invoquant `getChildren().add(node)` ou `addAll(n, …)`

- Quelques propriétés importantes du conteneur `FlowPane` :
    - `hgap `: Espacement horizontal entre les composants ou colonnes
    - `vgap` : Espacement vertical entre les composants ou lignes
    - `padding` : Espacement autour du conteneur (marge)
    - `alignment` : Alignement global des composants dans le conteneur
    - `rowValignment` : Alignement vertical dans les lignes 
    - `columnHalignment` : Alignement horizontal dans les colonnes
    - `prefWrapLength` : Détermine la largeur préférée (si horizontal-pane) ou la hauteur préférée (si vertical-pane)
    - `orientation` : Orientation du `FlowPane`

---
# FlowPane 
- Exemple :

```java
private FlowPane root;
private Button btnA = new Button("__Alpha__");
private Label lblB = new Label("__Bravo__");
private Button btnC = new Button("__Charlie__");
private Label lblD = new Label("__Delta__");
private Button btnE = new Button("__Echo__");
private Label lblF = new Label("__Foxtrot__");
private Button btnG = new Button("__Golf__");

@Override
public void start(Stage primaryStage) {
   // Voir diapo suivante
}
```
---
# FlowPane
<img src="slide47.png" style="position: absolute; left: 600px;  top: 50px;" >
- Exemple :

```java
@Override
public void start(Stage primaryStage) {
   primaryStage.setTitle("FlowPane (horizontal)");
   root = new FlowPane();

   root.getChildren().add(btnA); // Ajout
   root.getChildren().add(lblB); // des
   root.getChildren().add(btnC); // composants
   root.getChildren().add(lblD);
   root.getChildren().add(btnE);
   root.getChildren().add(lblF);
   root.getChildren().add(btnG);
   
   root.setPadding(new Insets(5)); // Marge extérieure
   root.setHgap(10); // Espacement horiz. entre composants
   root.setVgap(15); // Espacement vertical entre lignes
   root.setPrefWrapLength(250); // Largeur préférée du conteneur
   root.setRowValignment(VPos.BOTTOM); // Alignement vertical dans lignes
   
   primaryStage.setScene(new Scene(root));
   primaryStage.show();
}
```
---
# TilePane
- Le layout `TilePane` place les composants dans une grille alimentée soit horizontalement (par ligne, de gauche à droite) soit verticalement (par colonne, de haut en bas).

- Un des paramètres du constructeur (de type Orientation) détermine s'il s'agit d'un `TilePane` horizontal (par défaut) ou vertical.

- On définit pour la grille un certain nombre de colonnes (propriété `prefColumns`) si l'orientation est horizontale ou un certain nombre de lignes (propriété `prefRows`) si l'orientation est verticale.

- Toutes les cellules de cette grille (les tuiles) ont la même taille qui correspond à la plus grande largeur préférée et à la plus grande hauteur préférée parmi les composants placés dans ce conteneur.

- Le conteneur `TilePane` est très proche du conteneur `FlowPane`. La différence principale réside dans le fait que toutes les cellules ont obligatoirement la même taille (ce qui n'est pas le cas pour `FlowPane`).

---
# BorderPane
<img src="slide49.png" style="position: absolute; left: 650px;  top: 7px;" >
- Le conteneur `BorderPane` permet de placer les composants enfants dans cinq zones : `Top`, `Bottom`, `Left`, `Right` et `Center`.

- Un seul objet `Node` (composant, conteneur, …) peut être placé dans chacun de ces emplacements.

- Les composants placés dans les zones `Top` et `Bottom` :
    - Gardent leur hauteur préférée
    - Sont éventuellement agrandis horizontalement jusqu'à leur largeur maximale ou réduit à leur taille minimale en fonction de la largeur du conteneur.

- Les composants placés dans les zones `Left` et `Right` :
    - Gardent leur largeur préférée
    - Sont éventuellement agrandis verticalement jusqu'à leur hauteur maximale ou réduit à leur taille minimale en fonction de la hauteur restante entre les (éventuelles) zones `Top` et `Bottom` du conteneur.

- Le composant placé dans la zone `Center` :
    - Est éventuellement agrandi ou réduit dans les deux directions.
---
# BorderPane
- Le conteneur `BorderPane` est fréquemment utilisé comme conteneur racine du graphe de scène car il correspond à une division assez classique de la fenêtre principale d'une application (barre de titre, barre d'état, zone d'options, zone principale, etc.).

- Pour placer plusieurs composants dans les zones du `BorderPane`, il faut y ajouter des nœuds de type conteneur et ajouter ensuite les
composants dans ces conteneurs imbriqués.

- Il est donc très fréquent d'imbriquer plusieurs conteneurs pour obtenir la disposition désirée des composants de l'interface.

- Le graphe de scène représente donc un arbre d'imbrication dont la hauteur (nombre de niveaux) dépend du nombre de composants et de la complexité de la structure de l'interface graphique

---
# GridPane
- Le conteneur `GridPane` permet de disposer les composants enfants dans une grille flexible (arrangement en lignes et en colonnes), un peu à la manière d'une table HTML.

- La grille peut être irrégulière, la hauteur des lignes et la largeur des colonnes de la grille ne sont pas nécessairement uniformes.

- La zone occupée par un composant peut s'étendre (span) sur plusieurs lignes et/ou sur plusieurs colonnes.

- Le nombre de lignes et de colonnes de la grille est déterminé automatiquement par les endroits où sont placés les composants.

- Par défaut, la hauteur de chaque ligne est déterminée par la hauteur préférée du composant le plus haut qui s'y trouve.

- Par défaut, la largeur de chaque colonne est déterminée par la largeur préférée du composant le plus large qui s'y trouve.

---
# Conclusion (temporaire)
- La librairie JavaFX offre un ensemble de composants (kit de développement) pour créer les interfaces utilisateurs graphiques.

- Les différents conteneurs permettent de créer des interfaces graphiques aussi complexes que nécessaires. La diversité des layouts permet au concepteur de prévoir l'adaptation des composants dans toutes les situations.

- Il nous manque maintenant à décrire les *composants*.  Ce sont les éléments qui servent à afficher des informations ou
permettre à l'utilisateur d'interagir avec l'application : Libellés, icônes, boutons, champs-texte, menus, cases à cocher, etc.

- Bien qu'ils constituent les deux des nœuds (node) du graphe de scène, les composants sont à distinguer des conteneurs (layoutpanes) qui servent à disposer les composants et qui ne sont pas directement visibles dans l'interface (les bordures et les couleurs d'arrière-plan permettent cependant de révéler leur présence). 


