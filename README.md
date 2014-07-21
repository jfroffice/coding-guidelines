Coding Guidelines
=================

Les Espaces
-----------

Ne jamais mélanger les espaces et les tabulations

Préférer des identations avec 4 espaces

    .bloc {
        box-sizing: border-box;
        display: block;
        background: #f00;
    }

Les Commentaires
----------------

les commentaires sont facultatifs car ils ne sont pas forcément à jour
si vous jugez nécessaire d'ajouter un commentaire qu'il soit utile
créer un nouveau fichier plutôt que de rajouter une section

    /* commentaire simple */

    /**
     * commentaire multiline
     * TODO: 
     */

    /* ==========================================================================
       Section commentaires du bloc
       ========================================================================== */

    /* Sous-section commentaires du bloc
       ========================================================================== */

Formatage
---------
Exemple:

    .selector-1,
    .selector-2 {
        box-sizing: border-box;
        display: block;
        font-family: helvetica, arial, sans-serif;
        color: #333;
        background: 0 0 #666 no-repeat url("../img/bg_img.png");
    }

    .selector-a,
    .selector-b {
        padding: 10px;
    }


- un sélecteur par ligne
- un espace entre le sélecteur et la première accolage
- un espace entre la propriété et la valeur après :
- toujours rajouter des ; après une déclaration
- toujours utiliser les doubles quotes
- ne pas spécifier d'unité si la valeur est 0
- séparer chaque règle par un espace
- utiliser des minuscules
- utiliser des déclarations courtes pour les valeurs hexa (ex: #fff)


Exception: si la déclaration est courte, elle peut être écrite sur une seule ligne

    .selector-1 { width: 10%; }
    .selector-2 { width: 20%; }
    .selector-3 { width: 30%; }

Selecteurs
----------

ne JAMAIS utiliser d'identifiant (cela diminue la portabilité)

    #header {

    }

pas d'identifiant de tag inutile

    ul#navigation,
    ul.menu {
        border: 1px solid gray;
    }

pas d'ancètres (garder des sélecteurs courts)

    html div tr td {
        text-align: center;
    }

utiliser une classe spécifique (gain de performance)

    .text-center {
        text-align: center;
    }

pas de selecteur universelle

    * {
        display: block;
    }

pas de sélecteur sans limite

    [class^="icon-"] {
        display: block;
    }

éviter d'utiliser "!important" (préférer revoir le DOM et créer une nouvelle classe)

Exception

        .error { color: red !important; }

pas de sélecteur chainé ou joint (créer plutôt une nouvelle classe)

    .toto.titi {
        width: 30px;
    }

Convention de nommage (BEM)
---------------------------

les sélecteurs doivent être nommés en minuscule avec un trait d'union pour décrire une dépendance hiérarchique

    .widget
    .widget-headin

pour la définition d'un état vous pouvez une classe d'état

    .is-enable
    .is-disable
    .is-hidden

utiliser si possible la notation BEM (block element modifieur)

    .block {
        
    }

    .block__element {
        
    }

    .block--modifieur {
        
    }

.block représente le niveau supérieur d'une abstraction ou d'un composant.
.block__element représente un descendant de .bloc puisqu'il contribue à former .bloc dans son ensemble.
.block--modifieur représente un état ou une version différente de .block.

La notation BEM est verbeuse mais elle permet de mieux connaitre les dépendances entre les déclarations utilisées et le DOM 

Localisation
------------

utiliser l'anglais d'une façon générale.

utiliser les paramètres régionaux de la langue que vous utilisez pour le code spéfique

Ordre de déclaration des sélecteurs
-----------------------------------

du plus général au plus spécifique

    car la surcharge en CSS se fait 
        dans l'ordre de déclaration du fichier 
        et non dans l'ordre d'utilisation

indenter les elements enfants en correspondance avec le DOM

    .widget{
        padding: 10px;
        border: 1px solid #bbb;
        background-color: #cff;
        -webkit-border-radius: 4px;
           -moz-border-radius: 4px;
                border-radius: 4px;
    }
        .widget-heading{
            font-size: 1.5rem;
            line-height: 1;
            font-weight: bold;
            color: #333;
            margin-right: -10px;
            margin-left: -10px;
            padding: 0.25em;
        }

Shame.css
---------

rassembler les régles qui sont honteuses dans un fichier shame.css

cela sera pour vous l'occasion de les revoir et pourquoi pas de les supprimer plutard

Surcharge html
--------------

pas de style en inline

pas de code html de style 

    <i> <b> <strong>

Ordre des règles CSS
--------------------

    .selector {
        /* Positioning */
        position: absolute;
        z-index: 10;

        /* Display & Box Model */
        display: inline-block;
        overflow: hidden;
        box-sizing: border-box;
        width: 100px;
        height: 100px;
        padding: 10px;
        border: 10px solid #333;
        margin: 10px;

        /* Visual styles */
        background: #000;
        color: #fff;
        font-family: sans-serif;
        font-size: 16px;
        text-align: right;

        /* Vendor prefixed styles */
        -webkit-user-select: none;
    }

utiliser un outil (ex: csscomb) pour préserver l'ordre des CSS afin de garantir une meilleure réutilisabilité et maintenabilité du code

Mise en page
------------

La mise en page doit être définit pas des classes spécifiques

    .header--dark {
        background: #c6c8c8;
    }

    /* ... Layout section */

    .span-3 {
        width: 33.333%
    }

    <header class="header--dark span-3"></header>



OOCSS
-----

L'objectif de OOCSS est d'avoir une approche objet.

En découpant un objet en structure (objet) et rendu (extensions)

    .room { }

    .room--kitchen { }
    .room--bedroom { }
    .room--bathroom { }

SCSS (Sweet CSS)
----------------

permet de mettre en application OOCSS en évitant la duplication de code et en permettant l'héritage de class

Remarque: Ne pas descendre à plus de 3 niveaux

Outils
------

- [CSS Explain](http://josh.github.io/css-explain/)
- [autoprefixer](https://github.com/ai/autoprefixer)
- [csscomb](https://github.com/csscomb/csscomb.js)
- [recess](https://github.com/twitter/recess)
- [SASS](http://sass-lang.com)
- Utiliser __Audit__ de DevTools pour trouver les classes CSS inutilisés

TODO
----
Ecritures de règles CSS est un métier de designer
(cf SMACSS (reset, elements, ....))

références
----------
- https://github.com/topcoat/topcoat/wiki/Coding-Guidelines
- https://speakerdeck.com/jonrohan/githubs-css-performance
- https://github.com/csswizardry/CSS-Guidelines
