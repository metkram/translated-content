---
title: Commencer avec le HTML
slug: Learn/HTML/Introduction_to_HTML/Getting_started
tags:
  - Attributs
  - Codage
  - Commentaires
  - Débutant
  - Elements
  - Entités
  - Guide
  - HTML
  - espace
translation_of: Learn/HTML/Introduction_to_HTML/Getting_started
original_slug: Apprendre/HTML/Introduction_à_HTML/Getting_started
---
<div>{{LearnSidebar}}</div>

<div>{{NextMenu("Apprendre/HTML/Introduction_à_HTML/The_head_metadata_in_HTML", "Apprendre/HTML/Introduction_à_HTML")}}</div>

<p>Cet article porte sur les fondements du HTML, pour prendre un bon départ — nous définissons les éléments, les attributs et tout autre terme important que vous avez peut‑être entendu, ainsi que leur emplacement adéquat dans le langage. Nous montrons comment un élément HTML est structuré, comment une page HTML classique est structurée et expliquons les autres importants traits de base du langage. Dans ce parcours, nous jouons avec certains HTML pour exciter votre intérêt.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Notions sur le fonctionnement d'un ordinateur, avoir installé les <a href="/fr/docs/Learn/Getting_started_with_the_web/Installing_basic_software">logiciels de base</a> et savoir <a href="/fr/Apprendre/Commencer_avec_le_web/G%C3%A9rer_les_fichiers">gérer les fichiers</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Se familiariser avec le langage HTML et acquérir de la pratique en écrivant quelques éléments HTML.</td>
  </tr>
 </tbody>
</table>

<h2 id="Qu'est_ce_que_le_HTML">Qu'est ce que le HTML ?</h2>

<p>{{glossary("HTML")}} (<strong>H</strong>yper<strong>T</strong>ext <strong>M</strong>arkup <strong>L</strong>anguage) n'est pas un langage de programmation : c'est un <em>langage de balisage</em> qui sert à indiquer au navigateur comment structurer les pages web visitées. Il peut être aussi compliqué ou aussi simple que le développeur web souhaite qu'il soit. Le HTML se compose d'une série d'{{glossary("Elément", "éléments")}} avec lesquels vous pouvez encadrer, envelopper ou <em>baliser</em> différentes parties du contenu pour les faire apparaître ou agir d'une certaine manière. Des {{glossary("balise", "balises")}} encadrantes peuvent transformer une petite partie de contenu en un lien vers une autre page sur le Web, mettre des mots en italique, etc. Par exemple, prenons la phrase suivante :</p>

<pre>Mon chat est très grincheux</pre>

<p>Si nous voulons que cette ligne reste en l'état, nous pouvons dire qu'il s'agit d'un paragraphe en l'enveloppant d'un élément paragraphe ({{htmlelement("p")}}) :</p>

<pre class="brush: html">&lt;p&gt;Mon chat est très grincheux&lt;/p&gt;</pre>

<div class="note">
<p><strong>Note :</strong> Les éléments en HTML sont insensibles à la casse, c'est-à-dire qu'ils peuvent être écrits en majuscules ou en minuscules. Par exemple, un élément {{htmlelement("title")}}} peut être écrit &lt;title&gt;, &lt;TITLE&gt;, &lt;Title&gt;, &lt;TiTlE&gt;, etc. et il fonctionnera parfaitement. La meilleure pratique, cependant, est d'écrire tous les éléments en minuscules pour des raisons de cohérence, de lisibilité et autres.</p>
</div>

<h2 id="Anatomie_d'un_élément_HTML">Anatomie d'un élément HTML</h2>

<p>Regardons notre élément paragraphe d'un peu plus près :</p>

<p><img alt="" src="chat-grincheuxl.png"></p>

<p>Les principales parties de notre élément sont :</p>

<ol>
 <li><strong>La balise ouvrante :</strong> il s'agit du nom de l'élément (dans ce cas, p), encadré par un <strong>chevron ouvrant (&lt;) </strong>et un <strong>chevron fermant (&gt;)</strong>. Elle indique où l'élément commence ou commence à prendre effet — dans ce cas où commence le paragraphe ;</li>
 <li><strong>La balise fermante :</strong> c'est la même que la balise ouvrante, sauf qu'elle comprend une <strong>barre oblique (/)</strong> avant le nom de l'élément. Elle indique la fin de l'élément — dans ce cas, la fin du paragraphe. Ne pas inclure une balise de fermeture est une erreur fréquente chez les débutants, et peut amener des résultats étranges ;</li>
 <li><strong>Le contenu :</strong> il s'agit du contenu de l'élément. Dans notre cas, c'est simplement du texte ;</li>
 <li><strong>L'élément :</strong> l'ensemble balise ouvrante, balise fermante et contenu constituent l'élément.</li>
</ol>

<h3 id="Apprentissage_actif_créer_votre_premier_élément_HTML">Apprentissage actif : créer votre premier élément HTML</h3>

<p>Modifiez la ligne ci-dessous dans la <em>Zone de saisie</em> en la mettant entre les balises<code> &lt;em&gt;</code> et <code>&lt;/em&gt;</code> (<code>mettez &lt;em&gt; </code> avant pour <em>ouvrir l'élément</em> et <code>&lt;/em&gt;</code> après pour <em>fermer l'élément</em>) — cette opération doit mettre en relief la ligne en l'écrivant en italiques. Vous devriez constater la mise à jour de la modification directement dans la <em>Zone de rendu</em>.</p>

<p>Si vous faites une erreur, vous pouvez toujours réinitialiser avec le bouton <em>Réinitialiser</em>. Si vous êtes vraiment coincé, appuyez sur le bouton <em>Voir la solution</em> pour la réponse.</p>

<pre class="brush: html hidden">&lt;h2&gt;Zone de rendu&lt;/h2&gt;
&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la Zone de saisie (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="playable-code" style="min-height: 100px;width: 95%"&gt;
  Ceci est mon texte.
&lt;/textarea&gt;

&lt;div class="controls"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser" /&gt;
  &lt;input id="solution" type="button" value="Voir la solution" /&gt;
&lt;/div&gt;
</pre>

<pre class="brush: css hidden">html {
  font-family: 'Open Sans Light',Helvetica,Arial,sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}
</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;em&gt;Ceci est mon texte.&lt;/em&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// stop tab key tabbing out of textarea and
// make it write a tab at the caret position instead

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Update the saved userCode every time the user updates the text area code

textarea.onkeyup = function(){
  // We only want to save the state when the user code is being shown,
  // not the solution, so that solution is not saved over the user code
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_créer_votre_premier_élément_HTML', 700, 400, "", "","hide-codepen-jsfiddle")}}</p>

<h3 id="Eléments_imbriqués">Eléments imbriqués</h3>

<p>Vous pouvez mettre des éléments à l'intérieur d'autres éléments — cela s'appelle l'<strong>imbrication</strong>. Si vous voulez affirmer que votre chat est <strong>très</strong> grincheux, vous pouvez mettre le mot « très » dans l'élément {{htmlelement("strong")}}, pour qu'il soit fortement mis en valeur :</p>

<pre class="brush: html">&lt;p&gt;Mon chat est &lt;strong&gt;très&lt;/strong&gt; grincheux.&lt;/p&gt;</pre>

<p>Vous devez toutefois vous assurer que vos éléments sont correctement imbriqués : dans l'exemple ci-dessus, nous avons ouvert l'élément <code>p</code> en premier, puis l'élément <code>strong</code>, donc nous devons fermer l'élément <code>strong</code> d'abord, puis l'élément <code>p</code>. Ce qui suit est incorrect :</p>

<pre class="example-bad brush: html">&lt;p&gt;Mon chat est &lt;strong&gt;très grincheux.&lt;/p&gt;&lt;/strong&gt;</pre>

<p>Les éléments doivent être ouverts et fermés correctement afin d'être clairement à l'intérieur ou à l'extérieur l'un de l'autre. Si les balises se chevauchent comme dans l'exemple ci-dessus, votre navigateur web essaiera de deviner ce que vous vouliez dire, et vous pourrez obtenir des résultats inattendus. Autant éviter !</p>

<h3 id="Éléments_bloc_vs_en_ligne">Éléments bloc vs en ligne</h3>

<p>Il existe deux catégories importantes d'éléments en HTML que vous devez connaître : les éléments de niveau bloc et les éléments en ligne.</p>

<ul>
 <li>Les éléments de niveau <strong>bloc</strong> forment <strong>un bloc visible sur une page</strong> — ils apparaissent sur une nouvelle ligne quel que soit le contenu précédant et tout contenu qui les suit apparaît également sur une nouvelle ligne. Les éléments de niveau de bloc sont souvent des éléments structurels de la page et représentent, par exemple, des paragraphes, des listes, des menus de navigation, des pieds de page, etc. Un élément de niveau bloc ne peut pas être imbriqué dans un élément en ligne, mais il peut être imbriqué dans un autre élément de niveau bloc.</li>
 <li>Les éléments en<strong> ligne</strong> sont contenus <strong>dans des éléments de niveau bloc</strong>. Ils entourent seulement des petites parties du contenu du document, ni des paragraphes entiers, ni des regroupements de contenu. Un élément en ligne ne fait pas apparaître une nouvelle ligne dans le document. Il apparaît généralement dans un paragraphe de texte, par exemple un élément (hyperlien) {{htmlelement ("a")}} ou des éléments de mise en évidence tels que {{htmlelement("em")}} ou {{htmlelement("strong")}}.</li>
</ul>

<p>Prenez l'exemple suivant :</p>

<pre class="brush: html">&lt;em&gt;premier&lt;/em&gt;&lt;em&gt;deuxième&lt;/em&gt;&lt;em&gt;troisième&lt;/em&gt;

&lt;p&gt;quatrième&lt;/p&gt;&lt;p&gt;cinquième&lt;/p&gt;&lt;p&gt;sixième&lt;/p&gt;
</pre>

<p>{{htmlelement("em")}} est un élément en ligne et, comme vous pouvez le voir ci-dessous, les trois premiers éléments s'affichent sur la même ligne sans qu'il n'y ait d'espace entre eux. Par contre, {{htmlelement("p")}} est un élément de niveau bloc, donc chaque élément apparaît sur une nouvelle ligne et un espace apparaît au-dessus et au-dessous de chacun d'eux (l'espacement est dû au <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS">style CSS </a>par défaut du navigateur qui s'applique aux paragraphes).</p>

<p>{{ EmbedLiveSample('Éléments_bloc_vs_en_ligne', 700, 200, "", "") }}</p>

<div class="note">
<p><strong>Note :</strong> HTML5 a redéfini les catégories d'éléments dans HTML5 : voir <a href="https://html.spec.whatwg.org/multipage/indices.html#element-content-categories">catégories de contenu d'éléments</a>. Bien que ces définitions soient plus précises et moins ambiguës que celles qui précèdent, elles sont beaucoup plus compliquées à comprendre que « block » et « inline ». Nous nous en tiendrons donc à cela tout au long de ce sujet.</p>
</div>

<div class="note">
<p><strong>Note :</strong> les termes « block » et « inline », tels qu'utilisés dans cet article, ne doivent pas être confondus avec <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Le_mod%C3%A8le_de_bo%C3%AEte">les types de boîtes des CSS </a>portant les mêmes noms. Alors qu'ils sont corrélés par défaut, modifier le type d'affichage des CSS ne modifie pas la catégorie d'un élément et n'affecte pas les éléments qu'il pourrait contenir ni ceux dans lequel il pourrait être contenu. Une des raisons pour lesquelles HTML5 a abandonné ces termes était d'éviter cette confusion assez courante.</p>
</div>

<div class="note">
<p><strong>Note :</strong> Vous trouverez des pages de référence utiles incluant des listes d'<a href="/fr/docs/Web/HTML/%C3%89l%C3%A9ments_en_bloc">éléments de niveau bloc</a> et d'<a href="/fr/docs/Web/HTML/%C3%89l%C3%A9ments_en_ligne">éléments en ligne</a>.</p>
</div>

<h3 id="Éléments_vides">Éléments vides</h3>

<p>Tous les éléments ne suivent pas le modèle ci-dessus d'ouverture de balise, puis contenu, puis fermeture de balise. Certains éléments ne sont composés que d'une balise. Ils servent généralement à insérer / incorporer quelque chose dans le document à l'endroit où ils sont mis. Par exemple, l'élément <code>&lt;img /&gt;</code> ou {{htmlelement("img")}} insère une image dans une page à l'endroit où il est placé (la balise auto-fermante <code>&lt;img /&gt;</code> est à privilégier) :</p>

<pre class="brush: html">&lt;img src="https://raw.githubusercontent.com/mdn/beginner-html-site/gh-pages/images/firefox-icon.png" /&gt;</pre>

<p>Cela affichera l'élément suivant sur votre page :</p>

<p>{{ EmbedLiveSample('Éléments_vides', 700, 300, "", "", "hide-codepen-jsfiddle") }}</p>

<h2 id="Attributs">Attributs</h2>

<p>Les éléments peuvent aussi avoir des attributs, qui comme suit:</p>

<p><img alt='&amp;amp;amp;lt;p class="editor-note">My cat is very grumpy&amp;amp;amp;lt;/p>' src="attribut-chat-grincheux.png"></p>

<p>Les attributs contiennent des informations supplémentaires sur l'élément sans qu'elles n'apparaissent dans le contenu réel. Dans ce cas, l'attribut <code>class</code> vous permet de donner à l'élément un nom d'identification qui peut ensuite être utilisé pour cibler l'élément afin de lui attribuer un <a href="/fr/docs/Web/CSS">style CSS</a> ou un comportement particulier, par exemple.</p>

<p>Pour créer un attribut, il faut :</p>

<ol>
 <li>insérer un espace entre cet attribut et le nom de l'élément (ou l'attribut précédent, si l'élément possède déjà un ou plusieurs attributs) ;</li>
 <li>donner un nom à l'attribut, puis ajouter un signe égal ;</li>
 <li>donner une valeur à l'attribut, entourée par des guillemets d'ouverture et de fermeture.</li>
</ol>

<h3 id="Apprentissage_actif_ajouter_des_attributs_à_un_élément">Apprentissage actif : ajouter des attributs à un élément</h3>

<p>Un autre exemple d'un élément est {{htmlelement("a")}}. Il représente une ancre et permet de transformer en lien l'élément qu'il enveloppe. Il peut recevoir un certain nombre d'attributs, mais voici les deux principaux :</p>

<ul>
 <li><code>href </code>: cet attribut spécifie l'adresse web vers laquelle vous souhaitez que le lien pointe, c'est-à-dire l'adresse vers laquelle le navigateur redirigera lorsqu'on cliquera sur le lien. Par exemple, <code>href="https://www.mozilla.org/"</code>.</li>
 <li><code>title</code> : l'attribut <code>title</code> apporte des informations supplémentaires sur le lien, comme le nom de la page vers laquelle le lien pointe. Par exemple, <code>title="Page d'Accueil Mozilla"</code>, qui apparaîtra comme une info-bulle lorsque le curseur passera sur le lien.</li>
 <li><code>target</code>: L'attribut <code>target</code> définit le contexte de navigation utilisé pour afficher le lien. Par exemple, <code>target="_blank"</code> affichera le lien dans un nouvel onglet. Si vous voulez afficher le lien dans l'onglet courant, simplement, ne mettez pas cet attribut.</li>
</ul>

<p>Modifiez la ligne ci-dessous dans la <em>Zone de saisie</em> pour la transformer en lien vers votre site web préféré. Tout d'abord, ajoutez l'élément &lt;a&gt;, puis l'attribut <code>href</code>, puis l'attribut <code>title</code>. Vous pourrez voir la mise à jour de vos modifications en direct dans la <em>Zone de rendu</em>. Vous devriez voir un lien qui, lorsque vous passez votre pointeur de souris dessus, affiche le contenu de l'attribut <code>title</code> et, lorsque vous cliquez dessus, va à l'adresse web indiquée dans l'élément <code>href</code>. N'oubliez pas d'inclure un espace entre le nom de l'élément et chacun des attributs.</p>

<p>Si vous faites une erreur, vous pouvez toujours réinitialiser la <em>zone de saisie</em> en cliquant sur le bouton <em>Réinitialiser</em>. Si vous êtes vraiment coincé, cliquez sur le bouton <em>Voir la solution</em> pour afficher la réponse.</p>

<pre class="brush: html hidden">&lt;h2&gt;Zone de rendu&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la Zone de saisie (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 100px;width: 95%"&gt;
  &amp;lt;p&amp;gt;Un lien vers mon site Web préféré.&amp;lt;/p&amp;gt;
&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;p&gt;Un lien vers mon &lt;a href="https://www.mozilla.org/" title="Page d\'accueil de Mozilla" target="_blank"&gt;site Web préféré&lt;/a&gt;.&lt;/p&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// stop tab key tabbing out of textarea and
// make it write a tab at the caret position instead

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Update the saved userCode every time the user updates the text area code

textarea.onkeyup = function(){
  // We only want to save the state when the user code is being shown,
  // not the solution, so that solution is not saved over the user code
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_ajouter_des_attributs_à_un_élément', 700, 400,"","","hide-codepen-jsfiddle") }}</p>

<h3 id="Les_attributs_booléens">Les attributs booléens</h3>

<p>Vous verrez parfois des attributs sans valeur définie : c'est tout à fait autorisé. Ils sont appelés attributs booléens ; ils ne peuvent avoir qu'une seule valeur, généralement la même que le nom de l'attribut. Par exemple, prenez l'attribut {{htmlattrxref ("disabled", "input")}}, que vous pouvez affecter aux éléments <code>input</code> (éléments de saisie d'un formulaire) si vous voulez les désactiver (ils seront alors grisés) afin que l'utilisateur ne puisse pas y saisir de données.</p>

<pre>&lt;input type="text" disabled="disabled"&gt;</pre>

<p>Pour aller plus vite, il est parfaitement possible d'écrire cette même ligne de la façon suivante (nous avons également inclus un élément <code>input</code> non-désactivé pour référence, pour que vous puissiez vous faire une meilleure idée de ce qui se passe) :</p>

<pre class="brush: html">&lt;input type="text" disabled&gt;

&lt;input type="text"&gt;
</pre>

<p>Ces deux exemples vous donneront le résultat suivant :</p>

<p>{{ EmbedLiveSample('Les_attributs_booléens', 700, 100) }}</p>

<h3 id="Omettre_des_guillemets_autour_des_valeurs_dattribut">Omettre des guillemets autour des valeurs d'attribut</h3>

<p>Si vous regardez ce qui se passe sur le Web, vous rencontrerez tous types de styles de balises étranges, y compris des valeurs d'attribut sans guillemets. C'est permis dans certaines circonstances, mais cela va briser votre balisage dans d'autres. Par exemple, si nous revisitons notre exemple de lien ci-dessus, nous pourrons écrire une version de base avec seulement l'attribut <code>href</code>, comme ceci :</p>

<pre>&lt;a href=<code>https://www.mozilla.org/</code>&gt;mon site web favori&lt;/a&gt;</pre>

<p>Cependant, si nous ajoutons l'attribut <code>title</code> dans ce même style, cela devient incorrect :</p>

<pre class="brush: html">&lt;a href=https://www.mozilla.org/ title=La page d\'accueil Mozilla &gt;mon site web favori&lt;/a&gt;</pre>

<p>En effet, le navigateur interprétera mal la balise, pensant que l'attribut <code>title</code> est en fait quatre attributs — un attribut <code>title</code> avec la valeur « La » et trois attributs booléens, « <code>page</code> », « <code>d\'accueil</code> » et « <code>Mozilla</code> ». Ce n'est évidemment pas ce qui était prévu et cela provoquera des erreurs ou un comportement inattendu dans le code, comme on le voit dans l'exemple en direct ci-dessous. Essayez de passer la souris sur le lien pour voir ce que le texte de <code>title</code> donne.</p>

<p>{{ EmbedLiveSample("Omettre_des_guillemets_autour_des_valeurs_dattribut", 700, 100, "", "", "hide-codepen-jsfiddle") }}</p>

<p>Nous vous recommandons de toujours inclure les guillemets afin d'éviter ce type de problèmes, mais aussi pour que le code soit plus lisible.</p>

<h3 id="Guillemets_simples_ou_doubles">Guillemets simples ou doubles ?</h3>

<p>Dans cet article, vous remarquerez que les valeurs des attributs sont toutes entre des guillemets doubles (" "). Vous pouvez cependant voir des guillemets simples (' ') dans le code HTML de certaines personnes. C'est purement une question de style, et vous êtes libre de choisir la solution que vous préférez. Les deux lignes suivantes sont équivalentes :</p>

<pre class="brush: html">&lt;a href="http://www.exemple.com"&gt;Un lien vers mon exemple.&lt;/a&gt;

&lt;a href='http://www.example.com'&gt;Un lien vers mon exemple&lt;/a&gt;</pre>

<p>Vous devez cependant vous assurer de ne pas les mélanger. Ce qui suit n'est pas correct :</p>

<pre class="brush: html">&lt;a href="http://www.exemple.com'&gt;Un lien vers mon exemple.&lt;/a&gt;</pre>

<p>Si vous avez utilisé un type de guillemets dans votre code HTML, vous pouvez imbriquer l'autre type :</p>

<pre class="brush: html">&lt;a href="http://www.exemple.com" title="N'est-ce pas drôle ?"&gt;Un lien vers mon exemple.&lt;/a&gt;</pre>

<p>Si vous souhaitez imbriquer le même type de guillemets, vous devez utiliser <a href="/fr/docs/Glossary/Entity">une entité HTML</a> pour représenter ce caractère spécial.</p>

<h2 id="Anatomie_d'un_document_HTML">Anatomie d'un document HTML</h2>

<p>Les éléments HTML basiques ne sont pas très utiles si on les prend séparément. Nous allons voir comment combiner des éléments individuels pour former une page HTML entière :</p>

<pre class="brush: html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;title&gt;Ma page test&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;p&gt;Voici ma page web&lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>

<p>Ici, nous avons :</p>

<ol>
 <li><code>&lt;!DOCTYPE html&gt;</code> : le type de document. Quand HTML était jeune (vers 1991/2), les <code>doctypes</code> étaient censés agir comme des liens vers un ensemble de règles que la page HTML devait suivre pour être considérée comme un bon HTML, ce qui pouvait signifier la vérification automatique des erreurs et d'autres choses utiles. Habituellement, ils ressemblaient à ceci :

  <pre>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</pre>
  Cependant, de nos jours personne ne se soucie vraiment d'eux, et ils sont juste un artefact historique qui doit être inclus pour que tout fonctionne bien. <code>&lt;!DOCTYPE html&gt;</code> est la chaîne de caractères la plus courte qui soit un <code>doctype</code> valide. C'est tout ce que vous avez vraiment besoin de savoir.</li>
 <li><code>&lt;html&gt;&lt;/html&gt;</code> : l'élément <code>&lt;html&gt;</code>. Cet élément est le contenant de tout le code de la page et est parfois connu comme l'élément racine.</li>
 <li><code>&lt;head&gt;&lt;/head&gt;</code> : l'élément <code>&lt;head&gt;</code>. Cet élément a le rôle de conteneur pour toute chose que vous souhaitez inclure dans la page HTML qui ne soit pas du contenu à afficher aux visiteurs de la page : mots clés, description de page que vous souhaitez voir apparaître dans les résultats de recherche, style CSS, déclarations de jeu de caractères et plus encore. Nous vous en dirons plus à ce sujet dans l'article suivant de la série.</li>
 <li><code>&lt;meta charset="utf-8"&gt;</code> : cet élément définit que le jeu de caractères à utiliser pour votre document est UTF-8. Ce jeu comporte la quasi‑totalité des caractères de toutes les écritures de langues humaines connues. Actuellement, il peut pour l'essentiel gérer tout contenu textuel que vous y pourriez mettre. Il n'y a aucune raison de ne pas définir cela et il peut permettre d'éviter certains problèmes plus tard. </li>
 <li><code>&lt;title&gt;&lt;/title&gt;</code> : l'élément <code>title</code>. Il définit le titre de la page, celui qui s'affiche dans l'onglet du navigateur dans lequel la page est chargée et qui est utilisé pour décrire la page lorsque vous la marquez ou l'ajoutez aux favoris. </li>
 <li><code>&lt;body&gt;&lt;/body&gt;</code> : l'élément <code>&lt;body&gt;</code>. Il contient <em>tout </em>le contenu que vous souhaitez afficher aux internautes lorsqu'ils visitent votre page, que ce soit du texte, des images, des vidéos, des jeux, des pistes audio jouables ou autre.</li>
</ol>

<h3 id="Apprentissage_actif_ajouter_certaines_fonctionnalités_à_un_document_HTML">Apprentissage actif : ajouter certaines fonctionnalités à un document HTML</h3>

<p>Si vous voulez essayer d'écrire du HTML sur votre ordinateur en local, vous pouvez :</p>

<ol>
 <li>copier l'exemple de page HTML ci-dessus.</li>
 <li>créer un nouveau fichier dans votre éditeur de texte.</li>
 <li>coller le code dans le nouveau fichier texte.</li>
 <li>enregistrer le fichier sous <code>index.html</code>.</li>
</ol>

<div class="note">
<p><strong>Note :</strong> Vous pouvez également trouver ce modèle HTML dans le<a href="https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/getting-started/index.html"> dépôt GitHub MDN Learning Area</a>.</p>
</div>

<p>Vous pouvez maintenant ouvrir ce fichier dans un navigateur Web pour voir à quoi ressemble le rendu, puis modifier le code et actualiser le navigateur pour voir le résultat. Initialement, il ressemblera à ceci:</p>

<p><img alt="Une simple page HTML affichant Voici ma page" src="fr-capture-modele.png">Dans cet exercice, vous pouvez modifier le code sur votre ordinateur, comme indiqué ci-dessus, ou directement dans la fenêtre d'exemple modifiable ci-dessous (la fenêtre d'exemple modifiable représente uniquement le contenu de l'élément &lt;body&gt;. ) Nous aimerions que vous le fassiez en suivant les étapes suivantes :</p>

<ul>
 <li>Au début du document, juste après la balise d'ouverture &lt;body&gt;, ajoutez un titre principal pour le document. Il doit être entre une balise ouvrante &lt;h1&gt; et la balise fermante &lt;/ h1&gt; ;</li>
 <li>modifiez le contenu du paragraphe pour ajouter un texte sur quelque chose qui vous intéresse ;</li>
 <li>mettez les mots importants en gras en les mettant entre la balise ouvrante <code>&lt;strong&gt;</code> et la balise fermante <code>&lt;/ strong&gt;</code>;</li>
 <li>ajoutez un lien à votre paragraphe, comme <a href="#apprentissage_actif_ajout_d'attributs_à_un_élément">expliqué plus haut dans cet article</a> ;</li>
 <li>ajoutez une image dans votre document, en dessous du paragrahe, comme <a href="#éléments_vides">expliqué plus haut dans cet article</a>. Vous obtiendrez des points bonus si vous parvenez à lier une image différente (localement sur votre ordinateur ou ailleurs sur le Web).</li>
</ul>

<p>Si vous faites une erreur, vous pouvez toujours recommencer en utilisant le bouton <em>Réinitialiser</em>. Si vous êtes vraiment coincé, appuyez sur le bouton <em>Voir la solution</em> pour l'afficher.</p>

<pre class="brush: html hidden">&lt;h2&gt;Zone de rendu&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la Zone de saisie (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 100px;width: 95%"&gt;
  &amp;lt;p&amp;gt;Voici ma page&amp;lt;/p&amp;gt;
&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

img {
  max-width: 100%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;h1&gt;Un peu de musique&lt;/h1&gt;&lt;p&gt;J\'aime vraiment beaucoup &lt;strong&gt;jouer de la batterie&lt;/strong&gt;. Un de mes batteurs préférés est Neal Peart, qui\ joue dans le groupe &lt;a href="https://fr.wikipedia.org/wiki/Rush_%28groupe%29" title="Article Wikipedia sur Rush"&gt;Rush&lt;/a&gt;.\Actuellement, mon album Rush de prédilection est &lt;a href="http://www.deezer.com/album/942295"&gt;Moving Pictures&lt;/a&gt;.&lt;/p&gt;\ &lt;img src="http://www.cygnus-x1.net/links/rush/images/albums/sectors/sector2-movingpictures-cover-s.jpg"&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// stop tab key tabbing out of textarea and
// make it write a tab at the caret position instead

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Update the saved userCode every time the user updates the text area code

textarea.onkeyup = function(){
  // We only want to save the state when the user code is being shown,
  // not the solution, so that solution is not saved over the user code
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_ajouter_certaines_fonctionnalités_à_un_document_HTML', 700, 600, "", "", "hide-codepen-jsfiddle") }}</p>

<h3 id="Espace_vide_en_HTML">Espace vide en HTML</h3>

<p>Dans les exemples ci-dessus, vous avez peut-être remarqué que beaucoup d'espaces sont inclus dans le code — ce n'est pas nécessaire du tout. Les deux extraits de code suivants sont équivalents:</p>

<pre class="brush: html">&lt;p&gt;Les chiens sont idiots.&lt;/p&gt;

&lt;p&gt;Les chiens        sont
           idiots.&lt;/p&gt;</pre>

<p>Peu importe la quantité d'espace que vous utilisez (pour inclure des espaces, ou aussi des sauts de ligne), l'analyseur HTML réduit chacun à un seul espace lors du rendu du code. Alors, pourquoi utiliser autant d'espace blanc? La réponse est la lisibilité — car il est tellement plus facile de comprendre ce qui se passe dans votre code si vous l'avez bien formaté, et non pas simplement l'écrire dans un grand désordre. Dans notre HTML, nous avons chaque élément imbriqué indenté par deux espaces plus que celui qui le contient. C'est à vous de choisir le style de formatage que vous utilisez (combien d'espaces pour chaque niveau d'indentation, par exemple), mais vous devriez envisager d'utiliser une sorte de formatage.</p>

<h2 id="Références_dentités">Références d'entités : inclure les caractères spéciaux en HTML</h2>

<p>En HTML, les caractères <code>&lt;</code>, <code>&gt;</code>,<code>"</code>,<code>'</code> et <code>&amp;</code> sont des caractères spéciaux. Ils font partie de la syntaxe HTML elle-même, alors comment inclure un de ces caractères dans du texte, par exemple si vous voulez vraiment utiliser une esperluette(&amp;) ou un signe inférieur(&lt;), qui ne soit pas interpré en tant que code comme les navigateurs pourraient le faire ?</p>

<p>Nous devons utiliser les références des caractères — codes spéciaux qui représentent des caractères et peuvent être utilisés dans ces circonstances exactes. Chaque référence de caractère est démarrée avec une esperluette (&amp;), et se termine par un point-virgule (;).</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Le caractère</th>
   <th scope="col">Réference équivalent</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>&lt;</td>
   <td>&amp;lt;</td>
  </tr>
  <tr>
   <td>&gt;</td>
   <td>&amp;gt;</td>
  </tr>
  <tr>
   <td>"</td>
   <td>&amp;quot;</td>
  </tr>
  <tr>
   <td>'</td>
   <td>&amp;apos;</td>
  </tr>
  <tr>
   <td>&amp;</td>
   <td>&amp;amp;</td>
  </tr>
 </tbody>
</table>

<p>Dans l'exemple ci-dessous, voici deux paragraphes parlant de techniques Web :</p>

<pre class="brush: html">&lt;p&gt;En HTML, un paragraphe se définit avec l'élément &lt;p&gt;.&lt;/p&gt;

&lt;p&gt;En HTML, un paragraphe se définit avec l'élément &amp;lt;p&amp;gt;.&lt;/p&gt;</pre>

<p>Dans la zone de rendu en direct ci-dessous, vous pouvez voir que le premier paragraphe n'est pas correctement affiché : le navigateur interprète le second &lt;p&gt; comme le début d'un nouveau paragraphe ! Le deuxième paragraphe est bien affiché, car nous avons remplacé les signes inférieur(&lt;) et supérieur(&gt;) par leurs références de caractère.</p>

<p>{{ EmbedLiveSample("Références_dentités", 700, 200, "", "", "hide-codepen-jsfiddle") }}</p>

<div class="note">
<p><strong>Note :</strong> Un graphique de toutes les références d'entité de caractères HTML est disponible sur Wikipedia : <a href="https://fr.wikipedia.org/wiki/Liste_des_entit%C3%A9s_caract%C3%A8re_de_XML_et_HTML">Liste des entités caractère de XML et HTML</a>.</p>
</div>

<h2 id="Commentaires_en_HTML">Commentaires en HTML</h2>

<p>En HTML, comme pour la plupart des langages de programmation, il existe un mécanisme permettant d'écrire des commentaires dans le code. Les commentaires sont ignorés par le navigateur et invisibles à l'utilisateur. Leur but est de permettre d'inclure des commentaires dans le code pour dire comment il fonctionne, que font les diverses parties du code, etc. Cela peut s'avérer très utile si vous revenez à un codage que vous n'avez pas travaillé depuis 6 mois et que vous ne pouvez pas vous rappeler ce que vous avez fait — ou si vous donnez votre code à quelqu'un d'autre pour qu'il y travaille.</p>

<p>Pour transformer une section de contenu dans votre fichier HTML en commentaire, vous devez la mettre dans les marqueurs spéciaux <code>&lt;!-- </code>et<code>--&gt;</code>, par exemple :</p>

<pre class="brush: html">&lt;p&gt;Je ne suis pas dans un commentaire&lt;/p&gt;

&lt;!-- &lt;p&gt;Je suis dans un commmentaire!&lt;/p&gt; --&gt;</pre>

<p>Comme vous pouvez le voir ci-dessous, le premier paragraphe apparaît dans le rendu de l'éditeur en ligne, mais le second n'apparaît pas.</p>

<p>{{ EmbedLiveSample('Commentaires_en_HTML', 700, 100, "", "", "hide-codepen-jsfiddle") }}</p>

<h2 id="Résumé">Résumé</h2>

<p>Vous avez atteint la fin de l'article — nous espérons que vous avez apprécié de faire le tour des bases du HTML ! À ce stade, vous devez comprendre à quoi ce langage ressemble, comment il fonctionne à un niveau de base, et être en mesure d'écrire quelques éléments et attributs. C'est parfait pour le moment, car dans les articles suivants, nous allons approfondir certaines des choses que vous venez de voir, et introduire de nouveaux aspects du langage. Restez à l'écoute !</p>

<div class="note">
<p><strong>Note :</strong> À ce stade, lorsque vous commencez à en apprendre davantage sur le langage HTML, vous pouvez également commencer à explorer les bases des feuilles de style <a href="/fr/docs/Learn/CSS">CSS</a>. CSS est le langage utilisé pour composer vos pages Web (par exemple, changer la police ou les couleurs, ou modifier la mise en page). HTML et CSS vont très bien ensemble, comme vous allez bientôt le découvrir.</p>
</div>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/HTML/Applying_color">Appliquer une couleur aux éléments HTML avec les CSS</a></li>
</ul>

<div>{{NextMenu("Apprendre/HTML/Introduction_à_HTML/The_head_metadata_in_HTML", "Apprendre/HTML/Introduction_à_HTML")}}</div>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li>Commencer avec le HTML</li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML">Qu'y-a-t-il dans l'en-tête ? Métadonnées en HTML</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals">Fondamentaux du texte HTML</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks">Création d'hyperliens</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting">Formatage avancé du texte</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure">Structure de Site Web et de document</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML">Déboguer de l'HTML</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter">Faire une lettre</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content">Structurer une page de contenu</a></li>
</ul>