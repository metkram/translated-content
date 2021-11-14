---
title: Initiation à la mise en forme du texte
slug: Learn/CSS/Styling_text/Fundamentals
tags:
  - Alignement
  - CSS
  - Débutant
  - Guide
  - Polices de caractères
  - Style
  - Texte
translation_of: Learn/CSS/Styling_text/Fundamentals
original_slug: Learn/CSS/Styling_text/initiation-mise-en-forme-du-texte
---
<div>{{LearnSidebar}}</div>

<div>{{NextMenu("Learn/CSS/Styling_text/Styling_lists", "Learn/CSS/Styling_text")}}</div>

<p>Dans cet article, nous allons commencer le voyage vers la maîtrise des styles du texte avec {{glossary("CSS")}}. Nous passerons en revue les principes de base de mise en forme du texte, y compris la graisse, la famille et le style de police, les codes d'abréviation, l'alignement du texte et autres effets, ainsi que l'espacement des lignes et des lettres.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Connaissances informatiques de base, les bases HTML (étudiées dans l'<a href="/fr/docs/Learn/HTML/Introduction_to_HTML">Introduction au HTML</a>), les bases CSS (étudiées dans <a href="/fr/docs/Learn/CSS/Introduction_to_CSS">Introduction à CSS</a>).</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Apprendre les techniques et propriétés fondamentales nécessaires pour composer du texte sur les pages web.</td>
  </tr>
 </tbody>
</table>

<h2 id="En_quoi_consiste_la_mise_en_forme_du_texte_avec_CSS">En quoi consiste la mise en forme du texte avec CSS ?</h2>

<p>Comme vous l'avez déjà vu dans votre apprentissage de HTML et CSS, le texte d'un élément est placé à l'intérieur de la boîte de contenu de cet élément. Il débute en haut à gauche de cette zone (ou en haut à droite, dans le cas des contenus en langues s'écrivant de droite à gauche) et se poursuit vers la fin de la ligne. Arrivé en bout de ligne, il descend à la ligne suivante et continue, puis va à la ligne suivante, jusqu'à ce que tout le contenu ait été placé. Les contenus textuels se comportent comme une suite d'éléments en ligne placés les uns à côté des autres. Aucun saut de ligne n'est créé avant que la fin de la ligne soit atteinte, sauf si vous forcez manuellement le saut de ligne avec l'élément {{htmlelement("br")}}.</p>

<div class="note">
<p><strong>Note :</strong> si le paragraphe ci‑dessus vous paraît confus,  pas de problème — revenez en arrière et revoyez l'article sur la théorie du <a href="/fr/Apprendre/CSS/Les_bases/Le_modèle_de_boîte">Modèle de boîte</a> avant de poursuivre.</p>
</div>

<p>Les propriétés CSS utilisées pour le style de texte appartiennent généralement à deux catégories, que nous verrons séparément dans cet article :</p>

<ul>
 <li><strong>Styles de la police de caractères </strong>: ces propriétés concernent la fonte appliquée au  texte, affectant sa police, sa taille, sa graisse, si elle est italique, etc.</li>
 <li><strong>Styles de composition du texte </strong>: ces propriétés influent sur les espacements et autres dispositions de mise en page du texte, permettant de modifier, par exemple, l'espacement entre lignes et entre caractères, et la manière de disposer le texte  dans la boîte de contenu.</li>
</ul>

<div class="note">
<p><strong>Note :</strong> Gardez à l'esprit que le texte à l'intérieur d'un élément est affecté comme une seule entité. Vous ne pouvez pas sélectionner et mettre en forme des sous-sections de texte, sauf si vous les enveloppez dans un élément approprié (tel que {{htmlelement ("span")}} ou {{htmlelement ("strong")}}, ou utilisez un texte pseudo-élément spécifique comme <a href="/fr/docs/Web/CSS/::first-letter">::first-letter</a> (sélectionne la première lettre du texte d'un élément), <a href="/fr/docs/Web/CSS/::first-line">::first-line</a> (sélectionne la première ligne du texte d'un élément) ou <a href="/fr/docs/Web/CSS/::selection">::selection</a> (sélectionne le texte actuellement mis en surbrillance par le curseur) .</p>
</div>

<h2 id="Fontes">Fontes</h2>

<p>Passons directement aux propriétés pour le style des polices. Dans cet exemple, nous allons appliquer différentes propriétés CSS au même exemple HTML, qui ressemble à ceci :</p>

<pre class="brush: html">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<div class="note">
<p><strong>Note :</strong> (NdT : Extrait et traduction <em>approximative</em> de la chanson <em>Tommy the Cat</em> du groupe <a href="https://fr.wikipedia.org/wiki/Primus_(groupe)">Primus)</a></p>
</div>

<p>Vous pouvez trouver l'<a href="https://mdn.github.io/learning-area/css/styling-text/fundamentals/">exemple (en) fini</a> sur Github (voir aussi <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/fundamentals/index.html">le code source</a>).</p>

<h3 id="Couleur">Couleur</h3>

<p>La propriété {{cssxref("color")}} définit la couleur du contenu d'avant‑plan des éléments sélectionnés (généralement du texte, mais peut être autre chose, comme un soulignement ou un surlignage créé avec la propriété {{cssxref("text-decoration")}}.</p>

<p><code>color</code> accepte toutes les <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Values_and_units#Couleurs">unités de couleur des CSS</a>, par exemple :</p>

<pre class="brush: css">p {
  color: red;
}</pre>

<p>Les paragraphes seront en rouge, au lieu d'être de couleur noire, couleur par défaut du navigateur standard :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<p>{{ EmbedLiveSample('Couleur', '100%', 220) }}</p>

<h3 id="Familles_de_fontes">Familles de fontes</h3>

<p>Pour définir une police de caractères différente pour le texte, utilisez la propriété {{cssxref("font-family")}} — cela vous permet de spécifier une police (ou une liste de polices) que le navigateur doit appliquer aux éléments sélectionnés. Le navigateur n'appliquera une police de caractères que si elle est disponible sur la machine sur laquelle le site est accessible, sinon, il utilisera une  {{anch("Default fonts", "police par défaut")}} . Un exemple simple pour voir cela :</p>

<pre class="brush: css">p {
  font-family: arial;
}</pre>

<p>Cette commande définit la police de caractères arial (qui existe sur tous les ordinateurs) pour tous les paragraphes de la page.</p>

<h4 id="Polices_web_sûres">Polices web sûres</h4>

<p>En parlant de la disponibilité des polices, il y a seulement un certain nombre de polices qui sont généralement disponibles sur tous les systèmes, et peuvent donc être utilisées sans trop de soucis. Ce sont les polices web dites sûres.</p>

<p>La plupart du temps, en tant que développeur web, nous voulons avoir un contrôle précis sur les polices utilisées pour afficher le contenu textuel. Le problème est de trouver un moyen de savoir quelle police est disponible sur l'ordinateur utilisé pour voir nos pages web. Il n'y a aucun moyen systématique de le savoir, mais les polices web sûres sont disponibles sur presque tous les systèmes d'exploitation les plus utilisés (Windows, Mac, les distributions Linux les plus courantes, Android et iOS).</p>

<p>La liste des polices web vraiment sûres changera à mesure que les systèmes d'exploitation évolueront, mais on peut considérer les polices suivantes comme sûres sur le web, du moins pour le moment (beaucoup ont été popularisées grâce aux polices <a href="https://fr.wikipedia.org/wiki/Core_fonts_for_the_Web">Microsoft Core</a> pour le web à la fin des années 90 et début des années 2000) :</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Nom</th>
   <th scope="col">Type générique</th>
   <th scope="col">Notes</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Arial</td>
   <td>sans-serif</td>
   <td>Il est de bonne pratique d'ajouter Helvetica en tant qu'alternative préférée d'Arial car, bien que leurs apparences soient presque identiques, Helvetica est considérée comme ayant une forme plus agréable, même si Arial est plus courante.</td>
  </tr>
  <tr>
   <td>Courier New</td>
   <td>monospace</td>
   <td>Certains systèmes d'exploitation ont une version alternative (peut-être plus ancienne) de la police <em>Courier New</em> appelée <em>Courier</em>. Il est recommandé d'utiliser les deux avec <em>Courier New</em> comme alternative préférée.</td>
  </tr>
  <tr>
   <td>Georgia</td>
   <td>serif</td>
   <td> </td>
  </tr>
  <tr>
   <td>Times New Roman</td>
   <td>serif</td>
   <td>Certains systèmes d'exploitation ont une version alternative (peut-être plus ancienne) de la police <em>Times New Roman</em> appelée <em>Times</em>. Il est recommandé d'utiliser les deux avec <em>Times New Roman</em> comme alternative préférée.</td>
  </tr>
  <tr>
   <td>Trebuchet MS</td>
   <td>sans-serif</td>
   <td>Vous devriez être prudent avec l'utilisation de cette police - elle n'est pas aussi largement disponible sur les systèmes d'exploitation des mobiles.</td>
  </tr>
  <tr>
   <td>Verdana</td>
   <td>sans-serif</td>
   <td> </td>
  </tr>
 </tbody>
</table>

<div class="note">
<p><strong>Note :</strong> Le site <a href="https://www.cssfontstack.com/">cssfontstack.com</a> met à votre disposition, entre autres ressources, une liste de polices web sûres disponibles sur les systèmes d'exploitation Windows et Mac OS. Elle peut faciliter votre prise de décision quant à ce que vous considérerez comme sûr pour votre usage.</p>
</div>

<div class="note">
<p><strong>Note :</strong> Il y a moyen de télécharger une police personnalisée avec une page Web ; cela permet une utilisation personnalisée de la police comme vous le souhaitez : <strong>les polices web</strong>. C'est un peu plus complexe, et nous en discuterons dans un article séparé plus loin dans le module.</p>
</div>

<h4 id="Polices_par_défaut">Polices par défaut</h4>

<p>CSS définit cinq noms génériques pour les polices : <code>serif</code>, <code>sans-serif</code>, <code>monospace</code>, <code>cursive</code> et <code>fantasy</code>. À cause de leur caractère générique la police de caractères exacte utilisée, lors de l'emploi de ces noms, dépend de chaque navigateur et peut varier pour chaque système d'exploitation sur lequel ils s'exécutent. Dans le pire des cas, le navigateur essaiera de trouver une police appropriée.<code>serif</code>, <code>sans-serif</code> et <code>monospace</code> sont tout à fait prévisibles et devraient donner quelque chose de raisonnable. Par contre, <code>cursive</code> et <code>fantasy</code> sont moins prévisibles et nous vous recommandons de les utiliser avec précaution, en les testant au fur et à mesure.</p>

<p>Les 5 noms sont définis comme suit :</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Terme</th>
   <th scope="col">Définition</th>
   <th scope="col">Exemple</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>serif</code></td>
   <td>Les polices qui ont des sérifs (fioritures et autres petits détails que vous voyez en extrémité de trait dans certaines polices)</td>
   <td>Mon grand éléphant rouge</td>
  </tr>
  <tr>
   <td><code>sans-serif</code></td>
   <td>Les polices qui n'ont pas d'empattements</td>
   <td>Mon grand éléphant rouge</td>
  </tr>
  <tr>
   <td><code>monospace</code></td>
   <td>Les polices dans lesquelles chaque caractère a la même largeur, généralement utilisées dans les listes de codes.</td>
   <td>Mon grand éléphant rouge</td>
  </tr>
  <tr>
   <td><code>cursive</code></td>
   <td>Les polices destinées à émuler l'écriture, avec des traits fluides et connectés.</td>
   <td>Mon grand éléphant rouge</td>
  </tr>
  <tr>
   <td><code>fantasy</code></td>
   <td>Les polices destinées à être décoratives.</td>
   <td>Mon grand éléphant rouge</td>
  </tr>
 </tbody>
</table>

<h4 id="Pile_de_polices">Pile de polices</h4>

<p>Comme la disponibilité des polices que vous souhaitez utiliser sur vos pages web n'est pas garantie (même une police web peut échouer pour une raison quelconque), vous pouvez indiquer une pile de polices afin que le navigateur ait à sa disposition plusieurs polices. Il convient simplement d'indiquer pour valeur de <code>font-family</code> plusieurs noms de polices séparés par des virgules, par exemple :</p>

<pre class="brush: css">p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}</pre>

<p>Dans ce cas, le navigateur débute la lecture de la liste et cherche à voir si cette police est disponible sur la machine. Si c'est le cas, il applique cette police aux éléments sélectionnés. Sinon, il passe à la police suivante et ainsi de suite.</p>

<p>Indiquer un nom de police générique approprié en fin de liste est une bonne idée : si aucune des polices listées n'est disponible, le navigateur peut au‑moins fournir quelque chose de convenable. Soulignons ce point : les paragraphes seront rendus avec la police serif par défaut du navigateur si aucune autre option n'est disponible — généralement Time New Roman — mais ce ne sera pas un bon substitut à une police sans-serif !</p>

<div class="note">
<p><strong>Note :</strong> Les noms de police comportant plus d'un mot — comme <code>Trebuchet MS</code> — doivent être entourés de guillemets, par exemple <code>"Trebuchet MS"</code>.</p>
</div>

<h4 id="Un_exemple_de_font-family">Un exemple de font-family</h4>

<p>Faisons un ajout à notre exemple précédent et donnons aux paragraphes une police sans-serif :</p>

<pre class="brush: css">p {
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}</pre>

<p>Cela donne le résultat suivant :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<p>{{ EmbedLiveSample('Un_exemple_de_font-family', '100%', 220) }}</p>

<h3 id="Taille_de_la_police_de_caractères">Taille de la police de caractères</h3>

<p>Dans l'article <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Values_and_units">Valeurs et unités CSS</a> de notre prédédent module, nous avons vu les <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Values_and_units#Longueur_et_taille">unités de longueur et taille</a>. La taille des polices de caractères (définie avec la propriété {{cssxref("font-size")}}) accepte la plupart des unités de valeur (et d'autres comme les <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Values_and_units#Pourcentages">pourcentages</a>). Toutefois, les unités les plus couramment utilisées pour dimensionner le texte sont :</p>

<ul>
 <li><code>px</code> (pixels) : le nombre de pixels souhaités pour la hauteur du texte. C'est une unité absolue — il en résulte une même valeur finale calculée de la police sur la page dans à peu près n'importe quelle situation.</li>
 <li><code>em</code> : 1 em est égal à la taille de la police définie sur l'élément parent de l'élément courant que nous composons (plus précisément, la largeur d'un « M » majuscule de l'élément parent). Cette valeur peut devenir difficile à déterminer si vous avez beaucoup d'imbrications avec diverses tailles de police, mais cela reste faisable, comme vous le verrez ci-dessous. Pourquoi s'embêter ? C'est assez naturel, une fois que vous y êtes habitué ; vous pouvez utiliser <code>em</code> pour tout dimensionner, pas seulement du texte. Vous pouvez avoir un site web entier dimensionné avec des <code>em</code>, la maintenance en sera facilitée.</li>
 <li><code>rem</code> : il fonctionne comme <code>em</code>, excepté que un <code>rem</code> est égal à la taille de la police sur l'élément racine du document (c'est-à-dire {{htmlelement("html")}}) et non le parent direct). Le calcul des tailles de police en est facilité, mais malheureusement les <code>rem</code> ne sont pas pris en charge dans Internet Explorer 8 et avant. Si vous devez prendre en charge des navigateurs plus anciens dans votre projet, vous devrez vous en tenir aux <code>em</code> ou aux <code>px</code>, soit utiliser une prothèse d'émulation ({{glossary ("polyfill")}}) telle que <a href="https://github.com/chuckcarpenter/REM-unit-polyfill">REM-unit-polyfill</a>.</li>
</ul>

<p>La propriété <code>font-size</code> d'un élément est héritée de son parent. Tout commence par l'élément racine de l'ensemble du document — {{htmlelement("html")}} — dont la propriété <code>font‑size</code> est normée à 16 px sur les navigateurs. Tout paragraphe (ou tout autre élément dont la taille n'a pas été définie différemment par le navigateur) à l'intérieur de l'élément racine aura une taille finale de 16 px. D'autres éléments peuvent avoir des tailles par défaut différentes, par exemple un élément {{htmlelement ("h1")}} a une taille de 2 <code>em</code> définie par défaut, donc aura une taille finale de 32 px.</p>

<p>Les choses deviennent plus difficiles lorsque vous commencez à modifier la taille de la police des éléments imbriqués. Par exemple, vous avez un élément {{htmlelement ("article")}} dans la page dont la taille de police est 1.5 <code>em</code> (24 px), puis, vous voulez que les paragraphes de l'<code>&lt;article&gt;</code> aient une taille de police calculée de 20 px, quelle valeur de <code>em</code> utiliseriez-vous ?</p>

<pre class="brush: html">&lt;!-- font-size vaut 16px pour la base du document --&gt;
&lt;article&gt; &lt;!-- Si font-size vaut 1.5em --&gt;
  &lt;p&gt;Mon paragraphe&lt;/p&gt; &lt;!-- Comment calculer une hauteur de fonte de 20px ? --&gt;
&lt;/article&gt;</pre>

<p>Vous devrez définir sa valeur <code>em</code> à 20/24 ou 0,83333333 <code>em</code>. Les mathématiques peuvent être compliquées, vous devez donc faire attention à la façon dont vous composez les choses. Il est préférable d'utiliser <code>rem</code> quand vous le pouvez, pour garder les choses simples et éviter d'avoir à définir la taille des polices des éléments du conteneur si possible.</p>

<h4 id="Un_simple_exemple_de_dimensionnement">Un simple exemple de dimensionnement</h4>

<p>Quand vous dimensionnez votre texte, c'est généralement une bonne idée de définir la <code>font‑size</code> de base du document à 10 px, de sorte que les maths sont beaucoup plus faciles à travailler — les valeurs requises (r) em sont alors la taille de la police en pixels divisée par 10, et non par 16. Après cela, vous pouvez facilement dimensionner les différents types de texte dans votre document à votre goût. C'est une bonne idée de lister tous les jeux de règles de <code>font‑size</code> dans une zone désignée de votre feuille de style, afin qu'ils soient faciles à trouver.</p>

<p>Notre nouveau résultat ressemble à :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<pre class="brush: css">html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}</pre>

<p>{{ EmbedLiveSample('Un_simple_exemple_de_dimensionnement', '100%', 220) }}</p>

<h3 id="Style_de_fonte_graisse_transformation_et_décoration_de_texte">Style de fonte, graisse, transformation et décoration de texte</h3>

<p>CSS fournit quatre propriétés communes pour modifier le poids et l'emphase visuelles du texte :</p>

<ul>
 <li>{{cssxref("font-style")}} : utilisé pour appliquer ou enlever le style italique. Les valeurs possibles sont les suivantes (vous ne l'utiliserez que rarement, sauf si vous souhaitez désactiver le style italique pour une raison quelconque) :
  <ul>
   <li><code>normal</code> : fige le texte en police normale (suppression du style italique existant).</li>
   <li><code>italic </code>: met le texte en  <em>version italique de la police</em> si elle est disponible ; si elle n'existe pas, le style italique sera émulé avec l'option oblique à la place.</li>
   <li><code>oblique</code> : force le texte à utiliser une version simulée de fonte italique, créée en <em>inclinant la version normale</em>.</li>
  </ul>
 </li>
 <li>{{cssxref("font-weight")}} : définit la graisse du texte. La propriété peut avoir de nombreuses valeurs s'il y a de nombreuses variantes de polices disponibles (comme <em>-light</em>, <em>-normal</em>, <em>-bold</em>, <em>-extrabold</em>, <em>-black</em>, etc.), mais en réalité, vous les utiliserez rarement en dehors de <code>normal</code> et <code>bold</code> (gras):
  <ul>
   <li><code>normal</code>, <code>bold</code> : graisse de la police, normale ou <strong>bold</strong>.</li>
   <li><code>lighter</code>, <code>bolder</code> : définit la graisse de l'élément courant de sorte qu'il soit un cran moins gras ou plus gras que son parent.</li>
   <li><code>100–900</code> : valeurs numériques du taux de graisse ; elles permettent un dosage plus fin que les mots-clés ci-dessus, si nécessaire.</li>
  </ul>
 </li>
 <li>{{cssxref("text-transform")}} : Vous permet de définir les transformations de votre police. Les valeurs comprennent :
  <ul>
   <li><code>none</code> : aucune transformation.</li>
   <li><code>uppercase</code> : met tout le texte en majuscules.</li>
   <li><code>lowercase</code> : met tout le texte en minuscules.</li>
   <li><code>capitalize</code> : transforme tous les mots en mettant leur première lettre en majuscules.</li>
   <li><code>full-width</code> : force l'écriture de tous les glyphes dans un carré de largeur fixe, similaire à une police à espacement fixe, permettant leur alignement, par ex. caractères latins avec des glyphes de langue asiatique (comme le chinois, le japonais, le coréen.)</li>
  </ul>
 </li>
 <li>{{cssxref("text-decoration")}} : active ou désactive les décorations de texte sur les polices (vous les utiliserez principalement pour désactiver le soulignement par défaut sur les liens lors de leur création). Les valeurs disponibles sont :
  <ul>
   <li><code>none</code>: désactive les décorations du texte déjà présentes.</li>
   <li><code>underline</code>: souligne le texte.</li>
   <li><code>overline</code>: trace une ligne au-dessus du texte.</li>
   <li><code>line-through</code>: barre le texte.</li>
  </ul>
  Vous devez noter que {{cssxref("text-decoration")}} peut accepter plusieurs valeurs à la fois, si vous voulez en ajouter plusieurs simultanément, par exemple <code>text-decoration: underline overline</code>. Notez aussi que {{cssxref("text-decoration")}} est la propriété raccourcie pour {{cssxref("text-decoration-line")}}, {{cssxref("text-decoration-style")}} et {{cssxref("text-decoration-color")}}. Vous pouvez utiliser des combinaisons de ces valeurs de propriété pour créer des effets intéressants, par exemple <code>text-decoration: line-through red wavy</code>.</li>
</ul>

<p>Regardons l'ajout de quelques-unes de ces propriétés à notre exemple.</p>

<p>Notre nouveau résultat ressemble à :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>
</div>

<pre class="brush: css hidden">html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
  text-transform: capitalize;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}</pre>

<p>{{ EmbedLiveSample('Style_de_fonte_graisse_transformation_et_décoration_de_texte', '100%', 220) }}</p>

<h3 id="Ombres_du_texte">Ombres du texte</h3>

<p>Vous pouvez ombrer votre texte avec la propriété {{cssxref("text-shadow")}}. Elle prend 4 valeurs, comme vous pouvez le voir dans l'exemple ci-dessous :</p>

<pre class="brush: css">text-shadow: 4px 4px 5px red;</pre>

<p>Les 4 propriétés sont les suivantes :</p>

<ol>
 <li>Le décalage horizontal de l'ombre par rapport au texte original — cette grandeur acepte la plupart des <a href="/fr/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size">unités de longueur et de taille</a> des CSS disponibles, mais vous utiliserez en règle générale le px. Cette valeur doit être précisée.</li>
 <li>Le décalage vertical de l'ombre par rapport au texte original — cette grandeur se comporte à la base comme la précédente, sauf que l'ombre est portée vers le haut ou vers le bas, et non vers la gauche ou la droite. Cette valeur doit être précisée.</li>
 <li>Le rayon de floutage — plus cette valeur est élevée, plus l'ombre est étalée largement. Si cette valeur n'est pas précisée, la valeur par défaut est 0, ce qui signifie pas de flou. Elle accepte toutes les <a href="/fr/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size">unités de longueur et de taille</a> des CSS.</li>
 <li>La couleur de l'ombre, qui peut prendre toute <a href="/fr/Learn/CSS/Introduction_to_CSS/Values_and_units#Colors">unité de couleur CSS</a>. Si elle n'est pas définie, c'est la couleur noire par défaut.</li>
</ol>

<div class="note">
<p><strong>Note :</strong> Les valeurs positives de décalage déplacent l'ombre à droite et en bas, mais vous pouvez aussi utiliser des valeurs négatives pour obtenir une ombre à gauche et en haut, par exemple <code>-1px -1px</code>.</p>
</div>

<h4 id="Ombres_multiples">Ombres multiples</h4>

<p>Vous pouvez appliquer plusieurs ombres à un même texte, en mettant plusieurs valeurs d'ombrage séparées par une virgule, par exemple :</p>

<pre class="brush: css">text-shadow: -1px -1px 1px #aaa,
             0px 4px 1px rgba(0,0,0,0.5),
             4px 4px 5px rgba(0,0,0,0.7),
             0px 0px 7px rgba(0,0,0,0.4);</pre>

<p>Si nous l'appliquons à l'élément {{htmlelement ("h1")}} de notre exemple Tommy le Chat, nous nous obtenons :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<pre class="brush: css hidden">html {
  font-size: 10px;
    }

h1 {
  font-size:26px;
  text-transform: capitalize;
  text-shadow: -1px -1px 1px #aaa,
               0px 2px 1px rgba(0,0,0,0.5),
               2px 2px 2px rgba(0,0,0,0.7),
               0px 0px 3px rgba(0,0,0,0.4);
   }

h1 + p {
  font-weight: bold;
       }

p {
  font-size:14px;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
  }
</pre>

<p>{{ EmbedLiveSample('Ombres_du_texte', '100%', 220) }}</p>

<div class="note">
<p><strong>Note :</strong> Vous pouvez voir plus d'exemples intéressants de <code>text-shadow</code> dans l'article de Sitepoint <a href="http://www.sitepoint.com/moonlighting-css-text-shadow/">Moonlighting with CSS text-shadow</a> (Clair de lune avec text-shadow).</p>
</div>

<h2 id="Mise_en_page_du_texte">Mise en page du texte</h2>

<p>Après les propriétés de base des polices, examinons maintenant celles permettant de modifier la disposition des textes.</p>

<h3 id="Alignement_du_texte">Alignement du texte</h3>

<p>La propriété {{cssxref("text-align")}} s'utilise pour contrôler la disposition du texte dans la zone de contenu. Les valeurs acceptées sont les suivantes. Elles fonctionnent à peu près de la même manière que dans un traitement de texte :</p>

<ul>
 <li><code>left</code>: le texte est aligné à gauche.</li>
 <li><code>right</code>: le texte est aligné à droite.</li>
 <li><code>center</code>: le texte est centré.</li>
 <li><code>justify</code>: étale le texte, en faisant varier les espaces entre les mots afin de donner la même largeur à toutes les lignes du texte. Vous devez l'utiliser avec discernement  —  il peut sembler parfait, surtout lorsqu'il est appliqué à un paragraphe avec beaucoup de longs mots. Si vous voulez l'utiliser, vous devriez aussi penser à utiliser quelque chose d'autre, comme {{cssxref ("hyphens")}}, pour couper certains des mots les plus longs entre les lignes.</li>
</ul>

<p>Si nous appliquons <code>text-align: center;</code> à l'élément {{htmlelement("h1")}} de notre exemple, nous aurons :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<pre class="brush: css">html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
  text-transform: capitalize;
  text-shadow: -1px -1px 1px #aaa,
               0px 2px 1px rgba(0,0,0,0.5),
               2px 2px 2px rgba(0,0,0,0.7),
               0px 0px 3px rgba(0,0,0,0.4);
  text-align: center;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}</pre>

<p>{{ EmbedLiveSample('Alignement_du_texte', '100%', 220) }}</p>

<h3 id="Hauteur_de_ligne">Hauteur de ligne</h3>

<p>La propriété {{cssxref ("line-height")}} définit la hauteur de chaque ligne de texte — elle peut prendre la plupart des <a href="/fr/Apprendre/CSS/Introduction_à_CSS/Values_and_units#Length_and_size">unités de longueur et de taille</a>, mais elle peut également prendre une valeur sans unité, qui agit comme un multiplicateur et est considérée habituellement comme la meilleure option — la valeur de {{cssxref ("font-size")}} est multipliée par ce facteur pour obtenir la valeur de <code>line-height</code>. Le corps de texte semble généralement plus agréable et est plus facile à lire lorsque les lignes sont espacées ; la hauteur de ligne recommandée est d'environ 1,5-2 (double interligne). Donc, pour définir une hauteur de ligne de texte égale à 1,5 fois la hauteur de la police, vous utiliserez ceci :</p>

<pre class="brush: css">line-height: 1.5;</pre>

<p>En appliquant cette règle à l'élément {{htmlelement("p")}}  de l'exemple, nous obtenons :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<pre class="brush: css hidden">html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
  text-transform: capitalize;
  text-shadow: -1px -1px 1px #aaa,
               0px 2px 1px rgba(0,0,0,0.5),
               2px 2px 2px rgba(0,0,0,0.7),
               0px 0px 3px rgba(0,0,0,0.4);
  text-align: center;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}</pre>

<p>{{ EmbedLiveSample('Hauteur_de_ligne', '100%', 250) }}</p>

<h3 id="Espacement_entre_les_lettres_et_les_mots">Espacement entre les lettres et les mots</h3>

<p>Les propriétés {{cssxref ("letter-spacing")}} et {{cssxref ("word-spacing")}} permettent de définir l'espacement entre les lettres et les mots de votre texte. Vous ne les utiliserez pas très souvent, mais vous pourriez les utiliser pour obtenir une certaine apparence ou pour améliorer la lisibilité d'une police particulièrement dense. Ils peuvent prendre la plupart des <a href="/fr/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size">unités de longueur et de taille</a>.</p>

<p>Si nous appliquons les paramètres suivants à la première ligne des éléments {{htmlelement("p")}} dans notre exemple :</p>

<pre class="brush: css">p::first-line {
  letter-spacing: 2px;
  word-spacing: 4px;
}</pre>

<p>Nous obtiendrons :</p>

<pre class="brush: html hidden">&lt;h1&gt;Tommy le Chat&lt;/h1&gt;

&lt;p&gt;Je m'en souviens comme mon dernier repas...&lt;/p&gt;

&lt;p&gt;Dit Tommy le Chat en jetant la tête en arrière pour dégager
ce corps étranger qui s'était niché au fond de sa redoutable gueule.
Beaucoup de rats bien gras trépassèrent dans la ruelle en regardant l'étoile
brillant au fond du canon de cet extraordinaire rôdeur en quête de proie.
Un véritable miracle de la nature ce prédateur urbain — Tommy le Chat
avait beaucoup d'histoires à raconter. Mais il ne le faisait qu'en de rares
occasions, comme maintenant.&lt;/p&gt;</pre>

<pre class="brush: css hidden">html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
  text-transform: capitalize;
  text-shadow: -1px -1px 1px #aaa,
               0px 2px 1px rgba(0,0,0,0.5),
               2px 2px 2px rgba(0,0,0,0.7),
               0px 0px 3px rgba(0,0,0,0.4);
  text-align: center;
}

h1 + p {
  font-weight: bold;
}

p::first-line {
  letter-spacing: 2px;
  word-spacing: 4px;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
  line-height: 1.5;
}</pre>

<p>{{ EmbedLiveSample('Espacement_entre_les_lettres_et_les_mots', '100%', 250) }}</p>

<h3 id="D'autres_propriétés_intéressantes">D'autres propriétés intéressantes</h3>

<p>Les propriétés ci-dessus donnent un début d'idée de la manière de composer un style pour un texte de page web, mais beaucoup d'autres propriétés peuvent être utilisées. Nous n'avons juste évoqué que les plus importantes. Une fois que vous serez un familier de l'utilisation de ce qui précède, explorez donc ce qui suit :</p>

<p>Styles de police de caractères :</p>

<ul>
 <li>{{cssxref("font-variant")}} : bascule entre petites majuscules et police normale, et réciproquement.</li>
 <li>{{cssxref("font-kerning")}} : active et désactive les options de crénage des polices.</li>
 <li>{{cssxref("font-feature-settings")}} : active et désactive les fonctionnalités des polices de caractères <a href="https://en.wikipedia.org/wiki/OpenType">OpenType</a>.</li>
 <li>{{cssxref("font-variant-alternates")}} : contrôle l'utilisation de glyphes alternatifs pour une apparence de police donnée.</li>
 <li>{{cssxref("font-variant-caps")}}: contrôle l'utilisation de glyphes alternatifs en capitales.</li>
 <li>{{cssxref("font-variant-east-asian")}} : contrôle l'utilisation de glyphes alternatifs pour les écritures des pays de l'est de l'Asie, comme le japonais ou le chinois.</li>
 <li>{{cssxref("font-variant-ligatures")}} : contrôle les ligatures et formes contextuelles utilisées dans le texte.</li>
 <li>{{cssxref("font-variant-numeric")}} : contrôle l'utilisation de glyphes alternatifs pour les nombres, les fractions et les marqueurs ordinaux.</li>
 <li>{{cssxref("font-variant-position")}} : contrôle l'utilisation de glyphes alternatifs de plus petites tailles positionnés en exposant ou en indice.</li>
 <li>{{cssxref("font-size-adjust")}} : ajuste la taille visuelle de la police indépendamment de sa taille réelle.</li>
 <li>{{cssxref("font-stretch")}} : bascule entre les versions étirées alternatives possibles d'une police donnée.</li>
 <li>{{cssxref("text-underline-position")}} : définit la position du soulignement avec la valeur <code>underline</code> pour la propriété <code>text-decoration-line</code>.</li>
 <li>{{cssxref("text-rendering")}} : essaye d'effectuer une optimisation du rendu du texte.</li>
</ul>

<p>styles de mise en page du texte</p>

<ul>
 <li>{{cssxref("text-indent")}} : indique le nombre d'espaces à ménager horizontalement avant le début de la première ligne de texte du contenu.</li>
 <li>{{cssxref("text-overflow")}} : définit la façon de signaler aux utilisateurs le contenu en débordement (et donc non affiché).</li>
 <li>{{cssxref("white-space")}} : définit comment les espaces blancs et les sauts de ligne associés dans l'élément sont gérés.</li>
 <li>{{cssxref("word-break")}} : spécifie s'il y a césure dans les mots.</li>
 <li>{{cssxref("direction")}} : définit la direction du texte (cela dépend de la langue et généralement, il vaut mieux laisser HTML la gérer car elle est liée au contenu du texte.)</li>
 <li>{{cssxref("hyphens")}} : active et désactive la césure pour les langues prises en charge.</li>
 <li>{{cssxref("line-break")}} : détend ou renforce la rupture de ligne pour les langues asiatiques.</li>
 <li>{{cssxref("text-align-last")}} : définit comment la dernière ligne d'un bloc ou d'une ligne, juste avant un saut de ligne forcé, est alignée.</li>
 <li>{{cssxref("text-orientation")}} : définit l'orientation du texte dans une ligne.</li>
 <li>{{cssxref("word-wrap")}} : indique si le navigateur peut replier une ligne en conservant l'ordre des mots pour empêcher un débordement.</li>
 <li>{{cssxref("writing-mode")}} : définit si les lignes de texte sont disposées horizontalement ou verticalement et la direction des lignes suivantes.</li>
</ul>

<h2 id="Abréviations_pour_propriétés_de_fontes">Abréviations pour propriétés de fontes</h2>

<p>De nombreuses propriétés des fontes peuvent être déclarées de manière abrégée avec {{cssxref("font")}}. Elles sont écrites dans l'ordre suivant : {{cssxref("font-style")}}, {{cssxref("font-variant")}}, {{cssxref("font-weight")}}, {{cssxref("font-stretch")}}, {{cssxref("font-size")}}, {{cssxref("line-height")}} et {{cssxref("font-family")}}.</p>

<p>Parmi toutes ces propriétés, seules <code>font-size</code> et <code>font-family</code> sont requises lorsque la propriété abrégée <code>font</code> est utilisée.</p>

<p>Une barre oblique doit être placée entre les propriétés {{cssxref("font-size")}} et {{cssxref("line-height")}}.</p>

<p>Un exemple complet ressemblerait à ceci :</p>

<pre class="brush: css">font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;</pre>

<h2 id="Apprentissage_actif_jouer_avec_les_styles_du_texte">Apprentissage actif : jouer avec les styles du texte</h2>

<p>Dans cette session d'apprentissage actif, nous n'avons pas d'exercice spécifique à vous proposer : nous voulons juste vous permettre de jouer avec certaines propriétés de police ou mise en page de texte et de voir ce que vous pouvez produire ! Vous pouvez le faire en utilisant des fichiers HTML / CSS hors ligne ou en entrant votre code dans l'exemple modifiable en direct ci-dessous.</p>

<p>Si vous faites une erreur, vous pouvez toujours <em>Réinitialiser</em> avec le bouton de même nom.</p>

<pre class="brush: html hidden">&lt;div class="body-wrapper" style="font-family: 'Open Sans Light',Helvetica,Arial,sans-serif;"&gt;
  &lt;h2&gt;Zone de saisie du HTML&lt;/h2&gt;
  &lt;textarea id="code" class="html-input" style="width: 90%;height: 10em;padding: 10px;border: 1px solid #0095dd;"&gt;
  &lt;p&gt;Un peu de texte pour vous délecter !&lt;/p&gt;&lt;/textarea&gt;

  &lt;h2&gt;Zone de saisie de la CSS&lt;/h2&gt;
  &lt;textarea id="code" class="css-input" style="width: 90%;height: 10em;padding: 10px;border: 1px solid #0095dd;"&gt;p {

  }&lt;/textarea&gt;

  &lt;h2&gt;Zone de rendu&lt;/h2&gt;
  &lt;div class="output" style="width: 90%;height: 10em;padding: 10px;border: 1px solid #0095dd;"&gt;&lt;/div&gt;
  &lt;div class="controls"&gt;
    &lt;input id="reset" type="button" value="Réinitialiser" style="margin: 10px 10px 0 0;"&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

<pre class="brush: js hidden">var htmlInput = document.querySelector(".html-input");
var cssInput = document.querySelector(".css-input");
var reset = document.getElementById("reset");
var htmlCode = htmlInput.value;
var cssCode = cssInput.value;
var output = document.querySelector(".output");

var styleElem = document.createElement('style');
var headElem = document.querySelector('head');
headElem.appendChild(styleElem);

function drawOutput() {
  output.innerHTML = htmlInput.value;
  styleElem.textContent = cssInput.value;
}

reset.addEventListener("click", function() {
  htmlInput.value = htmlCode;
  cssInput.value = cssCode;
  drawOutput();
});

htmlInput.addEventListener("input", drawOutput);
cssInput.addEventListener("input", drawOutput);
window.addEventListener("load", drawOutput);
</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_jouer_avec_les_styles_du_texte', 700, 800) }}</p>

<h2 id="Résumé">Résumé</h2>

<p>Nous espérons que vous avez aimé jouer avec le texte dans cet article ! Le prochain article vous donnera tout ce que vous devez savoir sur le style des listes HTML.</p>

<p>{{NextMenu("Learn/CSS/Styling_text/Styling_lists", "Learn/CSS/Styling_text")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/initiation-mise-en-forme-du-texte">Initiation à la mise en forme du texte</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Styling_lists">Style de listes</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Mise_en_forme_des_liens">Mise en forme des liens</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Web_fonts">Polices de caractères web</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Typesetting_a_homepage">Composition d'une page d'accueil d'une école communale</a></li>
</ul>