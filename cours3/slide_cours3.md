class: center, middle

# Les IHM et le langage Java
### Henri GARRETA & Cyril PAIN-BARRE & Sébastien NEDJAR 
![IUT](logo.png)
---

class: center, middle

# Cours 3: JavaFX
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
# Composants – Controls
- La librairie JavaFX offre un **ensemble de composants** (kit de développement) pour créer les interfaces utilisateurs graphiques.

- Ces *composants d'interface* sont fréquemment nommés **controls** dans la documentation en anglais (parfois **widgets**).

- Dans ce cours, nous utiliserons généralement le terme composant pour parler des éléments qui servent à afficher des informations ou permettre à l'utilisateur d'interagir avec l'application.

- Bien qu'ils constituent les deux des nœuds (`Node`) du graphe de scène, les composants sont à distinguer des 
conteneurs (layoutpanes) qui servent à disposer les composants et qui ne sont pas directement visibles dans l'interface 
(les bordures et les couleurs d'arrière-plan permettent cependant de révéler leur présence). 

- Les composants ont tous pour classe parente `Control` qui est une sous-classe de `Node`.

---
# Composants – Controls

- Certains composants comme `ScrollPane` ou `SplitPane` jouent, en partie, un rôle de conteneur mais, formellement, ils 
ne font pas partie de cette famille (ils héritent de `Control` et non de `Pane`).

- On fait parfois la distinction entre composants simples (labels, champs texte, boutons, …) et composants complexes (tables, arbres,
media-player, navigateur, …).

- Dans ce chapitre, nous présenterons quelques composants simples et décrirons la manière de les créer et de les utiliser.

- Une fois que l'on a compris le principe de fonctionnement, il est plus facile de consulter la documentation officielle 
et de découvrir les propriétés et les comportements des composants offerts par la librairie JavaFX (les mêmes principes 
de base sont appliqués partout).

- Le cours ne décrira donc pas en détail l'ensemble des composants. Le support de cours ne constitue pas un manuel de 
référence et il faut, en complément, consulter la documentation disponible.

---
# Composants avec libellés 
- De nombreux composants affichent et gèrent des textes (libellés, boutons, cases à cocher, etc.).

- Les comportements communs de ces composants sont gérés par la classe parente `Labeled`.

- Les textes de ces composants peuvent être accompagnés d'un autre composant, généralement un graphique, une image ou une icône.

- Quelques propriétés communes aux composants `Labeled` :
  * `text` :  Texte affiché (`String`).
  
  * `font` : Police de caractères (famille, style, taille, …), type `Font`.
  
  * `textFill` : Couleur du texte, uniforme ou avec gradient (type `Paint`).
  
  * `underline` : Indique si le texte doit être souligné (type `Boolean`).
  
  * `alignment` : Alignement général du texte (et du graphique éventuel) dans la zone (type `Pos`). Valable seulement 
  si texte sur une seule ligne.

---
# Composants avec libellés 
- Quelques propriétés communes aux composants `Labeled` :
  
  * `wrapText` : Booléen qui définit si le texte passe à la ligne suivante lorsqu'il atteint la limite de la zone. 
  Le caractère '\n' peut également être inséré pour forcer un retour à la ligne (inconditionnel).

  * `textAlignment` : Alignement des lignes si le texte est multiligne.
Type énuméré `TextAlignment` (`LEFT`, `RIGHT`, `CENTER`, `JUSTIFY`).

  * `lineSpacing` : Espacement des lignes pour les textes multilignes. Type `Double`.

  * `graphic` : Autre composant (type `Node`) qui accompagne le texte. Généralement un graphique, une image ou une icône.

  * `contentDisplay` : Position du composant additionnel (graphic) par rapport au texte. Type énuméré `ContentDisplay` 
  (`LEFT`, `RIGHT`, `TOP`, `BOTTOM`, `TEXT_ONLY`, `GRAPHIC_ONLY`).

---
# Composants avec libellés 
- Quelques propriétés communes aux composants `Labeled` :

  * `graphicTextGap` : Espacement entre le texte et le composant additionnel (graphic). Type `Double`.

  * `mnemonicParsing` : Active le parsing des mnémoniques dans le texte (le caractère qui suit le caractère '_'). Type `Boolean`.

  * `textOverrun` : Comportement si le texte est trop long pour être affiché. Type énuméré `OverrunStyle` (`ELLISPSIS`, `CLIP`, …).

  * `labelPadding` : Définit l'espace autour du texte (et du graphique éventuel). Type `Insets`.

  * `ellipsisString` : Chaîne de caractères utilisée lorsque le texte est tronqué (ellipsis). Par défaut : "…"

---
# Label
- Le composant Label représente un libellé (= un texte non éditable).

- Les constructeurs permettent de définir le contenu du texte et de l'éventuel composant additionnel (graphic).

   * `new Label("Hello");`

   * `new Label("Warning", warningIcon);`

- L'essentiel des fonctionnalités sont héritées de `Labeled`. Une seule propriété additionnelle se trouve dans Label :

   * `setLabelFor` : Permet de définir un (autre) composant (`Node`) auquel le libellé est associé (utile pour définir un mnémonique).

- **Remarque** : Les objets de type `Text` possèdent certaines similitudes avec les composants de type Label mais `Text` 
n'est pas une sous-classe de `Control`. Cette classe fait partie de la famille des graphiques (sous-classe de `Shape`) 
et possède donc des propriétés et des fonctionnalités un peu différentes. 

---
# Label
<img src="slide12.png" style="position: absolute; left: 600px;  top: 30px;" >
```java
private HBox root = new HBox(20);
private Label lblA = new Label("Hello");
private Label lblB = new Label("Big and colored");
private Label lblC = new Label("A Multiline\nText\nLabel");

@Override
public void start(Stage primaryStage) throws Exception {
   
   root.setAlignment(Pos.CENTER);
   root.setPadding(new Insets(10));
   root.getChildren().add(lblA);
   
   lblB.setFont(Font.font("SansSerif", FontWeight.BOLD, 20));
   lblB.setTextFill(Color.rgb(180, 50, 50));
   lblB.setGraphic(new Rectangle(50, 5, Color.ORANGE));
   lblB.setContentDisplay(ContentDisplay.BOTTOM);
   
   root.getChildren().add(lblB);
   root.getChildren().add(lblC);
   
   primaryStage.setScene(new Scene(root));
   primaryStage.setTitle("Label Test");
   primaryStage.show();
}
```

---
# Button
- Le composant `Button` représente un bouton permettant à l'utilisateur de déclencher une action.

- La classe parente `ButtonBase` rassemble les propriétés communes à différents composants qui se comportent comme des boutons :
`Button`, `CheckBox`, `Hyperlink`, `MenuButton`, `ToggleButton`.

- Les constructeurs permettent de définir le contenu du texte et de l'éventuel composant additionnel (graphic).
  * `new Button("Ok");`
  
  * `new Button("Save", saveIcon);`
  
- Par héritage, toutes les propriétés qui ont été mentionnées pour les composants avec libellés (sous-classes de `Labeled`) 
sont naturellement applicables pour le composant `Button`.

---
# Button
Quelques propriétés du composant `Button` :

- `armed` : Booléen qui indique si le bouton est "armé" et prêt à déclencher une action (par exemple souris placée sur 
le bouton et touche gauche pressée).

- `onAction` : Détermine l'événement à générer lorsque l'action du bouton est déclenchée (par ex. lorsque la touche de 
la souris a été relâchée). Type `EventHandler<ActionEvent>`.

- `cancelButton` :  Booléen qui indique si le bouton est un bouton Cancel c'est-à-dire que l'action du bouton doit être 
déclenchée lorsque l'utilisateur presse sur la touche Escape (`VK_ESC`). Cette propriété ne doit être appliquée qu'à un 
seul bouton de l'interface.

- `defaultButton` : Booléen qui indique si le bouton est un bouton par défaut c'est-à-dire que l'action du bouton doit 
être déclenchée lorsque l'utilisateur presse sur la touche Enter (`VK_ENTER`). Cette propriété ne doit être appliquée 
qu'à un seul bouton de l'interface.

---
# Button

- La manière de traiter l'événement généré par le bouton sera expliquée dans le TP consacré à la gestion des événements 
et à l'écriture de contrôleurs qui se chargeront d'exécuter du code associé aux différents éléments actifs de l'interface.

- Pour ajouter une image à un bouton (où à n'importe quel autre composant de type `Labeled`), on peut utiliser la classe 
`ImageView` qui permet de représenter une image stockée dans une ressource locale (fichier de type gif, jpeg, png, …) ou en donnant l'URL d'une image sur un serveur web.

- La classe `ImageView` permet également de redimensionner les images et d'en afficher qu'une partie (viewport).

- Dans l'exemple qui suit, un des boutons (`btnLogin`) est affiché en associant une image au texte du libellé. 

---
# Button
```java
private static final String LOGO = "logo.jpg";
private VBox root = new VBox(10);
private Button btnOk = new Button("OK");
private Button btnLogin = new Button("Login");
private Button btnSave = new Button("Save");
private Button btnMulti = new Button("A Multiline\nRight-Justified\nText");

@Override
public void start(Stage primaryStage) throws Exception {
   ...
   root.setAlignment(Pos.CENTER);
   root.setPadding(new Insets(20));
   root.getChildren().add(btnOk);

   btnLogin.setTextFill(Color.BLUE);
   btnLogin.setFont(Font.font(null, FontWeight.BOLD, 14));
   btnLogin.setGraphic(new ImageView(LOGO));
   btnLogin.setContentDisplay(ContentDisplay.TOP);

   root.getChildren().add(btnLogin);

   btnSave.setDefaultButton(true);
   root.getChildren().add(btnSave);
   
   btnMulti.setTextAlignment(TextAlignment.RIGHT);
   root.getChildren().add(btnMulti);
   ...
}

```
<img src="slide16.png" style="position: absolute; left: 750px;  top: 300px;" >
---
# Saisie de textes

- La classe abstraite `TextInputControl` est la classe parente de différents composants qui permettent à l'utilisateur de saisir des
textes. Il s'agit notamment des composants d'interface `TextField`, `PasswordField` et `TextArea`

- La classe `TextInputControl` définit les propriétés de base et les fonctionnalités communes aux composants qui offrent une saisie
de texte et notamment :

  * La sélection de texte

  * L'édition de texte

  * La gestion du curseur à l'intérieur du texte (caret)

  * Le formatage du texte
  
---
# Saisie de textes

Quelques propriétés de la classe `TextInputControl` :

- `text` : Le texte contenu dans le composant (`String`).

- `editable` : Le texte peut être édité par l'utilisateur (`Boolean`).

- `font` : Police de caractères du texte (`Font`).

- `length` : Longueur du texte (`Integer`).

- `caretPosition` : Position courante du curseur / point d'insertion (caret).

- `promptText` : Texte affiché si aucun texte n'a été défini ou saisi par l'utilisateur (`String`). Ce texte n'est pas 
affiché lorsque le composant possède le focus (avec le curseur qui clignote dans le champ). Ce texte peut éventuellement 
remplacer un libellé ou une bulle d'aide pour le champ texte.

---
# Saisie de textes

Quelques propriétés de la classe `TextInputControl` :

- `textFormatter` : Formateur de texte associé au composant (`TextFormatter<?>`).

- `selectedText` : Texte sélectionné (`String`).

- `selection` : Indices (de...à) de la zone sélectionnée (`IndexRange`).

- `anchor` : Point d'ancrage (début) de la sélection (`Integer`).

---
# Saisie de textes

Quelques méthodes de la classe `TextInputControl` :

- `clear()` : Efface le texte (vide le champ).

- `copy/cut/paste()` : Transfert du texte dans ou depuis le clipboard.

- `positionCaret()` : Positionne le curseur à une position donnée.

- `forward/backward()` : Déplace d'un caractère le curseur (caret).

- `nextWord()` : Déplace le curseur (caret) au début du prochain mot.

- `insertText()` : Insère une chaîne de caractères dans le texte.

---
# Saisie de textes

Quelques méthodes de la classe `TextInputControl` :

- `appendText()` : Ajoute une chaîne de caractères à la fin du texte.

- `deleteText()` : Supprime une partie du texte (de...à).

- `deleteNextChar()` : Efface le prochain caractère.

- `replaceText()` : Remplace une partie du texte par un autre.

- `selectAll()` : Sélectionne l'ensemble du texte.

- `deselect()` : Annule la sélection courante du texte.

---
# TextField

- Le composant `TextField` représente un champ texte d'une seule ligne qui est éditable par défaut mais qui peut également 
être utilisé pour afficher du texte.
- Le composant n'intègre pas de libellé. Il faut utiliser un composant de type `Label` si l'on veut lui associer un libellé.
- En plus des propriétés héritées (notamment de `TextInputControl`), le composant `TextField` possède les propriétés suivantes :
  * `alignment` : Alignement du texte dans le champ (`Pos`).
  
  * `prefColumnCount` : Nombre de colonnes du champ texte; permet de déterminer la largeur préférée du composant. La 
  valeur par défaut est définie par la constante `DEFAULT_PREF_COLUMN_COUNT` (12).
  
  * `onAction` : Détermine l'événement à générer lorsque l'action du champ texte est déclenchée, en général lorsque 
  l'utilisateur presse sur la touche Enter (EventHandler<ActionEvent>).
---
# TextField
```java
private HBox root = new HBox(5);
private Label lblName = new Label("Name");
private Label lblMobile = new Label("Mobile");
private TextField tfdName = new TextField();
private TextField tfdMobile = new TextField();

@Override
public void start(Stage primaryStage) throws Exception {
   root.setAlignment(Pos.CENTER);
   root.getChildren().add(lblName);

   tfdName.setPrefColumnCount(12);
   tfdName.setPromptText("First and Last-Name");

   root.getChildren().add(tfdName);
   root.getChildren().add(lblMobile);

   HBox.setMargin(lblMobile, new Insets(0,0,0,10));

   tfdMobile.setPrefColumnCount(8);
   tfdMobile.setPromptText("Mobile Tel Nr");
   root.getChildren().add(tfdMobile);

   root.setPadding(new Insets(10));

   primaryStage.setScene(new Scene(root));
   primaryStage.setTitle("TextField Test");
   primaryStage.show();
}

```
<img src="slide23.png" style="position: absolute; left: 500px;  top: 50px;" >

---
# TextFormatter

- On peut associer un formateur de texte à tous les composants qui héritent de `TextInputControl` (propriété `TextFormatter`).

- Ce formateur est un composant de type `TextFormatter<V>` qui permet de définir :
  * Un convertisseur permettant de convertir le texte du composant en une valeur d'un autre type (par exemple un type 
  numérique, int, double, …).
  * Un filtre permettant d'intercepter et de modifier les caractères saisis par l'utilisateur pendant l'édition du 
  texte (n'accepter que les chiffres par ex.).

- Le formateur peut définir un filtre ou un convertisseur ou les deux.

- Le filtre et le convertisseur sont transmis dans le constructeur du formateur qui possède les surcharges suivantes :
```java
TextFormatter(StringConverter<V> valueConverter)
TextFormatter(StringConverter<V> valueConverter, V defaultValue)
TextFormatter(UnaryOperator<TextFormatter.Change> filter)
TextFormatter(StringConverter<V> valueConverter, V defaultValue,
UnaryOperator<TextFormatter.Change> filter)
```

---
# TextFormatter

- Le paramètre générique `V` du formateur (`TextFormatter<V>`) définit le type de la propriété value. On ne peut 
utiliser cette propriété que si l'on a défini un convertisseur dans le formateur.

- Le convertisseur est un objet de type `StringConverter<V>` qui doit implémenter les méthodes de conversions entre les propriétés `text` (String) et `value` (V) :

  * `fromString()` : `text` -> `value`
  
  * `toString()` : `value` -> `text`
- Il existe des implémentations prédéfinies de convertisseurs pour certains types courants :

  * `BooleanStringConverter`, `DoubleStringConverter`, `IntegerStringConverter`, `NumberStringConverter`, `DateTimeStringConverter`, ...

- Si l'on souhaite gérer le format d'affichage et/ou traiter certaines erreurs, il est préférable de redéfinir les méthodes de conversion.
---
# TextFormatter
<img src="slide26.png" style="position: absolute; left: 720px;  top: 50px;" >

- Exemple de convertisseur associé à un champ texte :

```java
TextFormatter<Double> formatter = new TextFormatter<Double>(
       new StringConverter<Double>() {
           @Override //--- Convert text (String) to Double 
           public Double fromString(String text) {
               try {
                   return Double.parseDouble(text);
               }
               catch (NumberFormatException e) {
                   return Double.NaN;
               }
           }
           @Override //--- Convert Double to String and format 
           public String toString(Double value) {
               return String.format("%.2f", value);
           }
       }
);

TextField textField = new TextField();
textField.setTextFormatter(formatter);

primaryStage.setScene(new Scene(new FlowPane(textField), 200, 100));
primaryStage.show();
```

---
#TextFormatter
- Le filtre que l'on peut greffer à un formateur est un objet de type `UnaryOperator<TextFormatter.Change>` :
  * `UnaryOperator<T>` : interface fonctionnelle avec la méthode abstraite `Change apply(Change c)`

  * `Change` : classe interne de `TextFormatter` représentant l'état des changements effectués

- La classe contient de nombreuses méthodes permettant de réagir aux changements effectués dans le texte lors de
  
  * L'ajout de texte (`isAdded()`)
  
  * Le remplacement de texte (`isReplaced()`)
  
  * La suppression de texte (`isDeleted()`)
  
- Les opérations disponibles sont des opérations de bas niveau qui permettent d'intervenir lors de la frappe des caractères dans le
champ mais qui nécessitent plus de travail pour créer des filtres plus complexes (adresse e-mail ou numéro de téléphone valide, etc.) .

---
# TextFormatter
- Exemple de filtre qui n'accepte que des chiffres ou '.' ou '-'. Une expression régulière (regex) est utilisée pour rejeter les autres caractères

```java
TextFormatter<String> tFmtNb = new TextFormatter<String>(change -> {
       change.setText(change.getText().replaceAll("[^0-9.-]", ""));
       return change;
   });
   
tfdTemperature.setTextFormatter(tFmtNb);
```

- Filtre qui n'accepte que 4 caractères (sans espaces)

```java
TextFormatter<String> tFmt4 = new TextFormatter<String>(change -> {
      String content = change.getControlNewText();
      if (content.length()>4 || change.getText().equals(' '))
         change.setText("");
      return change;
   });
   
tfdCode.setTextFormatter(tFmt4);
```
---
# Label - TextField - Button
- L'exemple qui suit illustre une utilisation des composants `Label`, `TextField` et `Button` qui sont assemblés pour 
créer un panneau de login simple.

- La propriété `disable` (héritée de `Node`) permet d'activer ou de désactiver un composant de l'interface. Un composant désactivé
reste visible mais n'est plus actif (il est généralement 'grisé').

- Une liaison (`binding`) est effectuée entre la propriété `text` (contenu du champ texte) et la propriété `disable` en utilisant des opérations
intermédiaires (`isEmpty()` et `or()`).

- De cette manière, le champ `Password` est désactivé tant que le champ `Username` est vide. D'autre part, le bouton n'est activé que
si les deux champs texte sont remplis.

- Une manière simple et élégante de gérer l'interaction et d'éviter des traitements d'erreurs.

---
# Label - TextField - Button

```java
    private GridPane root = new GridPane();
    private Label userLabel = new Label("Username:");
    private Label passwordLabel = new Label("Password:");
    private TextField userField = new TextField();
    private PasswordField passwordField = new PasswordField();
    private Button loginButton = new Button("Login");

    public void start(Stage primaryStage) {
        passwordField.disableProperty().bind(userField.textProperty().isEmpty());
        loginButton.disableProperty().bind(userField.textProperty().isEmpty()
                .or(passwordField.textProperty().isEmpty()));

        root.setHgap(6);
        root.setVgap(12);
        root.setPadding(new Insets(15));
```
---
# Label - TextField - Button
```java
        root.add(userLabel, 0, 0);
        root.add(userField, 1, 0);
        root.add(passwordLabel, 0, 1);
        root.add(passwordField, 1, 1);
        root.add(loginButton, 0, 2, 2, 1);

        GridPane.setHalignment(loginButton, HPos.CENTER);
        GridPane.setMargin(loginButton, new Insets(10, 0, 0, 0));

        loginButton.setOnAction(event -> System.out.println("Login: "
                + userField.getText()
                + " / " + passwordField.getText()));

        primaryStage.setScene(new Scene(root));
        primaryStage.setTitle("Login Panel");
        primaryStage.show();
    }

```
<img src="slide31.png" style="position: absolute; left: 600px;  top: 30px;" >
---
class: center, middle

# FXML
---

#IHM procédurales vs déclaratives
- Avec JavaFX, les interfaces peuvent être créées de deux manières :

  * Procédurale : en écrivant du code Java qui fait appel aux API de la plateforme et qui utilise les composants/conteneurs à
disposition (classes et interfaces)

  * Déclarative : en décrivant l'interface dans un fichier au format FXML qui sera ensuite chargé dynamiquement dans l'application
- Les premiers cours ont décrit les bases de la technique procédurale (programmatique) permettant de créer des interfaces.

- Le présent chapitre abordera la deuxième possibilité de créer les interfaces (les vues) en utilisant notamment l'outil 
*SceneBuilder* qui permet, de manière interactive, de créer les fichiers FXML.

- *SceneBuilder* est une application qui doit être installée et n'est plus contenue directement dans le JDK.
---

# Fichiers FXML
- Au centre de l'approche déclarative, se trouvent les fichiers FXML.

- Un fichier FXML est un fichier au format XML dont la syntaxe est conçue pour décrire l'interface (la vue) avec ses composants, ses
conteneurs, sa disposition, …

  * Le fichier FXML décrit le "quoi" mais pas le "comment"

- A l'exécution, le fichier FXML sera chargé par l'application (classe `FXMLLoader`) et un objet Java sera créé 
(généralement la racine est un conteneur) avec les éléments que le fichier décrit (les composants, conteneurs, graphiques, …).
  
  * Un fichier FXML constitue une forme particulière de sérialisation d'objets, utilisée spécifiquement pour décrire les interfaces

- Il est possible de créer les fichiers FXML avec un éditeur de texte mais, plus généralement, on utilise un outil graphique (*SceneBuilder*)
qui permet de concevoir l'interface de manière conviviale et de générer automatiquement le fichier FXML correspondant.

---

# Fichiers FXML

- Les objets créés par le chargement de fichiers FXML peuvent être assignés à la racine d'un graphe de scène ou 
représenter un des nœuds dans un graphe de scène créé de manière procédurale.

- Une fois chargés, les nœuds issus de fichiers FXML sont totalement équivalents à ceux créés de manière procédurale. Les mêmes
opérations et manipulations peuvent leur être appliquées.

- Le langage FXML n'est pas associé à un schéma XML mais la structure de sa syntaxe correspond à celle des API JavaFX :
  * Les classes JavaFX (conteneurs, composants) peuvent être utilisées comme éléments dans la syntaxe XML

  * Les propriétés des composants correspondent à leurs attributs

- Même si certaines possibilités existent (en lien notamment avec du code JavaScript) on conseille généralement d'utiliser 
les fichiers FXML exclusivement pour décrire les interfaces, et d'effectuer tous les traitements (activité des contrôleurs) d
ans le code Java.

---
# SceneBuilder

- L'outil graphique **SceneBuilder** permet de concevoir l'interface de manière interactive (WYSIWYG) en assemblant 
les conteneurs et les composants et en définissant leurs propriétés.

- Le mode de fonctionnement de cet utilitaire est assez classique avec une zone d'édition centrale, entourée d'un 
certain nombre d'outils : palettes de conteneurs, de composants, de menus, de graphiques, vue de la structure 
hiérarchique de l'interface, inspecteurs de propriétés, de layout, etc.

- L'emploi de cet outil n'est pas décrit en détail dans ce support de cours, il faut se référer à la documentation 
disponible. Son utilisation est cependant assez intuitive, pour autant que les éléments affichés soient connus (notamment 
les caractéristiques et propriétés principales des conteneurs et des composants).

- Malgré l'outil graphique, on n'échappe donc pas à une compréhension minimale des API (composants, conteneurs, propriétés, …).

---
# Interprétation des fichiers FXML 

- Lors du chargement du fichier FXML, son contenu est interprété et des objets Java correspondants sont créés.

Par exemple, l'élément :

```xml
<BorderPane prefHeight="80.0" prefWidth="250.0" . . .>
```
sera interprété comme :

```java
BorderPane rootPane = new BorderPane();
rootPane.setPrefHeight(80.0);
rootPane.setPrefWidth(250.0);
```

Quand un attribut commence par le nom d'une classe suivi d'un point et d'un identificateur, par exemple :

```xml
<TextField GridPane.columnIndex="3" . . . >
```

l'attribut sera interprété comme une invocation de méthode statique :

```java
TextField tfd = new TextField();
GridPane.setColumnIndex(tfd, 3);
```

---
# Interprétation des fichiers FXML

- Pour les propriétés qui ne peuvent pas facilement être représentées par une chaîne de caractères, un élément est 
imbriqué (plutôt que de déclarer des attributs).

- Par exemple, si l'on considère l'élément
```xml
<Label id="title" fx:id="title" text="Titre" textFill="#0022cc"
BorderPane.alignment="CENTER">
<font>
<Font name="SansSerif Bold" size="20.0" />
</font>
</Label>
```

- On constate que la propriété `Font` est codée comme un élément imbriqué dans l'élément Label.

- Pour les propriétés de type liste (par exemple `children`), les éléments de la liste sont simplement imbriqués et 
répétés dans l'élément représentant la liste (par exemple, les composants enfants seront listés entre les balises `<children>` et `</children>`).
---
# Liens FXML <-> programme 
- Le lien entre les composants décrits dans le fichier FXML et le programme est établi par les attributs `fx:id` :

```xml
<Label id="title" fx:id="title" text="Titre" textFill="#0022cc" ...>
```

- L'attribut `fx:id` fonctionne en lien avec l'annotation `@FXML` que l'on peut utiliser dans les contrôleurs, et qui 
va indiquer au système que le composant avec le nom `fx:id` pourra être injecté dans l'objet correspondant de la classe contrôleur.

```java
public class SayHelloController {
   @FXML
   private Button btnHello;
   @FXML // fx:id="title"
   private Label title; // Object injected by FXMLLoader
```

---
# Liens FXML <-> programme 

- La classe qui joue le rôle de contrôleur pour une interface déclarée en FXML doit être annoncée dans l'élément racine, 
en utilisant l'attribut `fx:controller` :
```xml
<BorderPane prefHeight="80.0" prefWidth="250.0"
style="-fx-background-color: #FFFCAA;"
xmlns=http://javafx.com/javafx/8
xmlns:fx=http://javafx.com/fxml/1
fx:controller="SayHelloController">
...
```

- **Attention** : Les attributs qui définissent les namespaces `xmlns=…` ainsi que `xmlns:fx=…` sont utilisés par 
l'environnement JavaFX (FXMLLoader, SceneBuilder, etc.). Ils ne doivent donc pas être modifiés !

---
# Liens FXML <-> programme 

- Pour les composants actifs déclarés dans une interface en FXML, on peut indiquer la méthode du contrôleur qui doit être invoquée en
utilisant l'attribut `fx:onEvent="#methodName"` :

```xml
<Button fx:id="btnHello" onAction="#handleButtonAction" 
      text="Say Hello" BorderPane.alignment="CENTER" />
```

- Dans la classe contrôleur, ces méthodes devront (comme les composants associés) être annotées avec `@FXML`.

```java
@FXML
private void handleButtonAction(ActionEvent event) {
   title.setText("Hello !");
   title.setTextFill(Color.FUCHSIA);
}
```

---
# Liens FXML <-> programme 
- Dans les classes qui agissent comme "contrôleurs", on peut définir une méthode `initialize()` (qui doit être annotée 
avec `@FXML`) pour effectuer certaines initialisations.

- Cette méthode est automatiquement invoquée après le chargement du fichier FXML.

- Elle peut être utile pour initialiser certains composants, en faisant par exemple appel au modèle.

```java
@FXML
private void initialize() {
   cbbCountry.getItems().addAll("Allemagne", "Angleterre", "Belgique",
         "Espagne", "France", "Italie",
         "Pays-Bas", "Portugal", "Suisse");
   lstProducts.getItems().addAll(model.getProducts());
. . .
}
```
---
# Liens FXML <-> programme 
- L'attribut `id` ne doit pas être confondu avec l'attribut `fx:id` :

```xml
<Label id="title" fx:id="title" text="Titre" textFill="#0022cc" ...>
```

- L'attribut `id` définit un sélecteur CSS de type Id qui permet d'associer des règles de style aux composants 
portant cet Id.

  * Exemple dans un fichier CSS :

      ```css
      #title {
           -fx-font-size: 24pt;
      }
      ```

- Dans le fichier FXML, une feuille de style (fichier CSS) peut être associé à un composant avec l'attribut `stylesheets="@CSS_File"`

```xml
<BorderPane stylesheets="@SayHello.css" . . . >
```

- L'éditeur *SceneBuilder* permet (dans l'inspecteur de propriétés) de créer l'attribut `id` et de définir le fichier CSS associé (Stylesheets).
---
# Liens FXML <-> programme 
- Il est possible d'accéder au contrôleur associé au fichier FXML en
créant un chargeur (loader) pour ce fichier (plutôt que d'utiliser la
méthode statique `FXMLLoader.load()`) .

- Cela peut être utile pour avoir accès au contrôleur, par exemple pour
lui communiquer la référence du modèle de l'application 

   ```java
   public void start(Stage primaryStage) throws Exception {
         //--- Chargement du fichier FXML et recherche du contrôleur associé
         FXMLLoader loader = new FXMLLoader(getClass().getResource("SayHello.fxml"));
         BorderPane root = loader.load();
         SayHelloController ctrl = loader.getController();
         ctrl.setModel(model);
         Scene scene = new Scene(root);
   ```

- Dans ce cas, on utilisera la méthode d'instance `load()` pour charger
le fichier FXML et obtenir la référence de la racine du graphe de scène.

---
# Liens FXML <-> programme

- Si le contrôleur d'une interface déclarée avec FXML ne possède pas de constructeur par défaut, il faut créer le 
contrôleur et l'associer dans le code du programme, avant le chargement du fichier FXML.

- Le code suivant illustre la manière de le faire :
      ```java
      public void start(Stage primaryStage) throws Exception {
            //--- Chargement du fichier FXML et association du contrôleur
            FXMLLoader loader = new FXMLLoader(getClass().getResource("SayHello.fxml"));
            loader.setController(new SayHelloController("a param"));
            BorderPane root = loader.load();
      ```
- Dans ce cas, il n'est pas nécessaire de déclarer le contrôleur dans le
fichier FXML (`fx:controller="..."`).

