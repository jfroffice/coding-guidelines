Coding Guidelines
=================

(orienté performance)

espace
------



    .btn {
        background: #fff;
    }

commentaires
------------

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

Remarques:
    les commentaires sont facultatifs car probablement pas à jour
    créer un nouveau fichier plutôt que de rajouter une section

formattage
----------
- un sélecteur par ligne
- un espace entre le sélecteur et la première accolage
- un espace entre la propriété et la valeur après :
- toujours rajouter des ; après une déclaration
- toujours utiliser les doubles quotes
- ne pas spécifier d'unité si la valeur est 0
- séparer chaque règle par un espace
- utiliser des minuscules et des déclarations courtes valeurs hexa (ex: #fff)

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

exception: si la déclaration est courte, elle peut se faire sur une seule ligne

    .selector-1 { width: 10%; }
    .selector-2 { width: 20%; }
    .selector-3 { width: 30%; }


selecteurs
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

éviter d'utiliser "!important"

    
    préférer revoir le DOM et créer une nouvelle classe

    exception

        .error { color: red !important; }

pas de sélecteur chainé ou joins

    .toto.titi {
        width: 30px;
    }

    => créer une nouvelle classe

convention de nommage
---------------------

les sélecteurs doivent être nommés en minuscule avec un trait d'union pour décrire une dépendance hiérarchique

    .widget
    .widget-heading

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

localisation
------------

utiliser l'anglais d'une façon générale.

utiliser les paramètres régionaux de la langue que vous utilisez pour le code spéfique

ordre de déclaration des sélecteurs
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

rassembler les régles qui vont paresses honteuses dans un fichier shame.css
ce sera pour vous l'occasion de les revoir et pourquoi pas de les supprimer plutard

ordre des CSS
-------------

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

mise en page
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


surcharge html
--------------

pas de style en inline

pas de code html de style (ex: <i> <b> <strong>)


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

permet de mettre en application OOCSS en évitant la duplication de code

et en permettant l'héritage de class



Rq: Ne pas descendre à plus de 3 niveaux


Outils
------

- CSS Explain
- https://github.com/ai/autoprefixer
- csscomb
- recess
- sass
- Utiliser <<Audit>> de DevTools pour trouver les classes CSS inutilisés


TODO
----
Ecritures de règles CSS est un métier de designer
(cf SMACSS (reset, elements, ....))


références
----------
- https://github.com/topcoat/topcoat/wiki/Coding-Guidelines
- https://speakerdeck.com/jonrohan/githubs-css-performance
- gihttps://github.com/csswizardry/CSS-Guidelines
