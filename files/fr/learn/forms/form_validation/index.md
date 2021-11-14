---
title: Validation des données de formulaires
slug: Learn/Forms/Form_validation
translation_of: Learn/Forms/Form_validation
original_slug: Web/Guide/HTML/Formulaires/Validation_donnees_formulaire
---
<div>{{LearnSidebar}}{{PreviousMenuNext("Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires", "Web/Guide/HTML/Formulaires/Comment_construire_des_widgets_de_formulaires_personnalisés", "Web/Guide/HTML/Formulaires")}}</div>

<p>Ce n'est pas tout d'envoyer des données — il faut aussi s'assurer que les données mises dans un formulaire par un utilisateur sont dans un format correct pour pouvoir être traitées correctement et qu'elles ne vont pas casser nos applications. Nous voulons également aider les utilisateurs à compléter les formulaires correctement et à ne pas ressentir de frustration en essayant d'utiliser les applications. La validation des données de formulaire vous aide à remplir ces objectifs — cet article indique ce qu'il est nécessaire de savoir.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Notions concernant les ordinateurs, une bonne compréhension du <a href="/fr/docs/Learn/HTML">HTML</a>, des <a href="/fr/docs/Learn/CSS">CSS</a> et de <a href="/fr/docs/Learn/JavaScript">JavaScript</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Comprendre ce qu'est la validation d'un formulaire, pourquoi c'est important et comment la mettre en œuvre.</td>
  </tr>
 </tbody>
</table>

<h2 id="Qu'est‑ce_qu'une_validation_de_formulaire">Qu'est‑ce qu'une validation de formulaire?</h2>

<p>Allez sur n'importe quel site à la mode avec un formulaire d'inscription et vous remarquerez des retours si vous n'entrez pas les données dans le format attendu. Vous aurez des messages comme :</p>

<ul>
 <li>« Ce champ est obligatoire » (vous ne pouvez pas le laisser vide)</li>
 <li>« Veuillez entrer votre numéro de téléphone au format xxx-xxxx » (il attend trois chiffres suivis d'un tiret, suivi de quatre chiffres).</li>
 <li>« Veuillez entrer une adresse e-mail valide » (ce que vous avez saisi ne ressemble pas à une adresse e-mail valide).</li>
 <li>« Votre mot de passe doit comporter entre 8 et 30 caractères et contenir une majuscule, un symbole et un chiffre » (sérieusement ?).</li>
</ul>

<p>C'est ce qu'on appelle la validation de formulaire —  lorsque vous saisissez des données, l'application Web vérifie si elles sont correctes. Si elles sont correctes, l'application permet que les données soient soumises au serveur et (généralement) sauvegardées dans une base de données ; si ce n'est pas le cas, elle émet des messages d'erreur pour expliquer ce que vous avez fait de mal (pour autant que vous l'ayez fait). La validation des formulaires peut être mise en œuvre de différentes manières.</p>

<p>La vérité est qu'aucun d'entre nous n'<em>aime</em> remplir des formulaires — les formulaires ennuient les utilisateurs, tout le prouve : cela les incite à partir et à aller voir ailleurs s'ils sont mal faits. Bref, les formulaires, c'est nullissime.</p>

<p>Remplir des formulaires web doit être aussi facile que possible. Alors pourquoi être tatillons et bloquer les utilisateurs à chaque fois ? Il y a trois raisons principales :</p>

<ul>
 <li><strong>obtenir de bonnes données dans un bon format</strong> — les applications ne tourneront pas correctement si les données utilisateur sont stockées dans un format fantaisiste, ou si les bonnes informations ne sont pas aux bons endroits ou totalement omises.</li>
 <li><strong>protéger nos utilisateurs</strong> — s'ils entrent un mot de passe facile à deviner ou aucun, des utilisateurs malveillants peuvent aisément accéder à leurs comptes et voler leurs données.</li>
 <li><strong>nous protéger nous‑mêmes</strong> — il existe de nombreuses façons dont les utilisateurs malveillants peuvent utiliser les formulaires non protégés pour endommager l'application dans laquelle ils se trouvent (voir <a href="/fr/docs/Learn/Server-side/First_steps/Website_security">Sécurité du site Web</a>).</li>
</ul>

<h3 id="Les_divers_types_de_validation_de_formulaire">Les divers types de validation de formulaire</h3>

<p>Vous rencontrerez différents types de validation de formulaires sur le Web :</p>

<ul>
 <li>La validation côté client est la validation qui est effectuée dans le navigateur, avant que les données n'aient été soumises au serveur. Cette méthode est plus conviviale que la validation côté serveur car elle donne une réponse instantanée. Il est possible de la subdiviser encore avec :
  <ul>
   <li>la validation JavaScript, codée en JavaScript, entièrement personnalisable.</li>
   <li>la validation de formulaire intégrée avec les fonctions de validation de formulaire HTML5. Elle ne nécessite généralement pas de JavaScript, a de meilleures performances, mais elle n'est pas aussi personnalisable.</li>
  </ul>
 </li>
</ul>

<dl>
</dl>

<ul>
 <li>La validation côté serveur est la validation opérée sur le serveur, après que les données ont été soumises — le code côté serveur est utilisé pour valider les données avant de les mettre dans la base de données. Si elles sont erronées, une réponse est envoyée au client pour dire à l'utilisateur ce qui a mal tourné. La validation côté serveur n'est pas aussi conviviale que la validation côté client, car elle nécessite un aller-retour vers le serveur, mais c'est la dernière ligne de défense de votre application contre les mauvaises données (c'est-à-dire les données incorrectes, voire malveillantes). Tous les modèles de canevas de vérification courants côté serveur ont des fonctions de validation et de nettoyage des données (ce qui les sécurise).</li>
</ul>

<p>Dans le monde réel, les développeurs ont tendance à utiliser une combinaison de validations côté client et côté serveur, pour être du côté sûr.</p>

<h2 id="Utiliser_la_validation_intégrée_au_formulaire">Utiliser la validation intégrée au formulaire</h2>

<p>Une des caractéristiques de <a href="/fr/docs/orphaned/Web/Guide/HTML/HTML5">HTML5</a> est la possibilité de valider la plupart des données utilisateur sans avoir recours à des scripts. Ceci se fait en utilisant des <a href="/fr/docs/Web/Guide/HTML/HTML5/Constraint_validation">attributs de validation</a> sur les éléments de formulaire ; ils vous permettent de spécifier des règles pour une entrée de formulaire comme : une valeur doit‑elle être remplie ? y a-t-il une longueur minimale et/ou maximale des données ? doit‑elle être un nombre, une adresse e-mail ou autre chose ? doit‑elle correspondre à un modèle ? Si les données saisies suivent toutes ces règles, elles sont considérées comme valides ; si ce n'est pas le cas, elles sont considérées comme non valides.<br>
 Quand un élément est valide :</p>

<ul>
 <li>l'élément correspond à la pseudo‑classe CSS {{cssxref(":valid")}}  ; cela vous permet d'appliquer une composition de style distinctive.</li>
 <li>si l'utilisateur essaie d'envoyer les données, le navigateur soumet le formulaire pour autant qu'il n'y ait rien d'autre qui l'empêche de le faire (par ex. du JavaScript).</li>
</ul>

<p>Quand un élément est invalide :</p>

<ul>
 <li>l'élément correspond à la pseudo‑classe CSS {{cssxref(":invalid")}}  ; cela vous permet d'appliquer une composition de style distinctive.</li>
 <li>si l'utilisateur essaie d'envoyer le formulaire, le navigateur le bloquera et affichera un message d'erreur.</li>
</ul>

<h3 id="Contraintes_de_validation_sur_les_éléments_input_—_simple_début">Contraintes de validation sur les éléments input — simple début</h3>

<p>Dans cette section, nous examinerons quelques unes des diverses fonctionnalités HTML5 peuvant être utilisées pour valider des éléments d'{{HTMLElement("input")}}.</p>

<p>Commençons par un exemple simple — une entrée ouvrant un choix, selon votre préférence, entre banane ou cerise. Il faut un texte {{HTMLElement("input")}} simple avec une étiquette correspondante et un {{htmlelement("button")}} de soumission. Le code source est sur GitHub à l'adresse <a href="https://github.com/mdn/learning-area/blob/master/html/forms/form-validation/fruit-start.html">fruit-start.html</a> et un exemple « live » ci-dessous :</p>

<pre class="brush: html hidden">&lt;form&gt;
  &lt;label for="choose"&gt;Préférez‑vous la banane ou la cerise ?&lt;/label&gt;
  &lt;input id="choose" name="i_like"&gt;
  &lt;button&gt;Soumettre&lt;/button&gt;
&lt;/form&gt;</pre>

<pre class="brush: css hidden">input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 1px solid black;
}</pre>

<p>{{EmbedLiveSample("Contraintes_de_validation_sur_les_éléments_input_—_simple_début", "100%", 55)}}</p>

<p>Pour commencer, faites une copie de fruit-start.html dans un nouveau répertoire sur votre disque dur.</p>

<h3 id="Attribut_required">Attribut required</h3>

<p>La fonctionnalité de validation HTML5 la plus simple à utiliser est l'attribut {{htmlattrxref("required", "input")}}} — si vous voulez rendre une entrée obligatoire, vous pouvez marquer l'élément en utilisant cet attribut. Lorsque cet attribut est mis, le formulaire ne sera pas soumis (et affichera un message d'erreur) si l'entrée est vide (l'entrée sera également considérée comme invalide).</p>

<p>Ajoutez un attribut <code>required</code> à votre saisie, comme montré ci‑dessous :</p>

<pre class="brush: html">&lt;form&gt;
  &lt;label for="choose"&gt;Préférez-vous la banane ou la cerise ?&lt;/label&gt;
  &lt;input id="choose" name="i_like" required&gt;
  &lt;button&gt;Soumettre&lt;/button&gt;
&lt;/form&gt;</pre>

<p>Notez aussi le CSS incorporé dans le fichier exemple :</p>

<pre class="brush: css">input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 1px solid black;
}</pre>

<p>L'entrée a une bordure en pointillés rouge vif lorsqu'elle n'est pas valide, et une bordure noire plus subtile lorsqu'elle est valide. Essayez le nouveau comportement dans l'exemple ci-dessous :</p>

<p>{{EmbedLiveSample("Attribut_required", "100%", 55)}}</p>

<h3 id="Validation_selon_une_expression_régulière">Validation selon une expression régulière</h3>

<p>Une autre fonctionnalité de validation très courante est l'attribut {{htmlattrxref("pattern", "input")}}, qui attend une <a href="/fr/docs/Web/JavaScript/Guide/Regular_Expressions">expression régulière</a> comme valeur. Une expression régulière (regex) est un modèle qui peut être utilisé pour faire correspondre des combinaisons de caractères dans des chaînes de texte, de sorte qu'elles sont idéales pour la validation de formulaires (ainsi que diverses autres utilisations en JavaScript). Les Regex sont assez complexes et nous n'avons pas l'intention de vous les enseigner de manière exhaustive dans cet article.</p>

<p>Vous trouverez ci-dessous quelques exemples pour vous donner une idée de base de leur fonctionnement :</p>

<ul>
 <li><code>a</code> — correspond à un caractère qui doit être un a (ni b, ni aa, etc.)</li>
 <li><code>abc</code> — correspond à <code>a</code>, suivi de <code>b</code>, suivi de <code>c</code>.</li>
 <li><code>a*</code> — correspond au caractère a, absent ou présent plusieurs fois (<code>+</code> correspond à un caractère une ou plusieurs fois).</li>
 <li><code>[^a]</code> — correspond à un caractère qui <strong>n'est pas</strong> un a.</li>
 <li><code>a|b</code> — correspond à un caractère qui est a ou b.</li>
 <li><code>[abc]</code> — correspond à un caractère qui est a, b ou c.</li>
 <li><code>[^abc]</code> — correspond à un caractère qui <strong>n'est pas</strong> a, b ou c.</li>
 <li><code>[a-z]</code> — correspond à tout caractère de la plage a–z, en minuscules seulement (utilisez <code>[A-Za-z]</code> pour minuscules et majuscules et <code>[A-Z]</code> pour les majuscules uniquement).</li>
 <li><code>a.c</code> — correspond à a, suivi par n'importe quel caractère,suivi par c.</li>
 <li><code>a{5}</code> — correspond à a, 5 fois.</li>
 <li><code>a{5,7}</code> — correspond à  a, 5 à 7 fois, mais ni plus, ni moins.</li>
</ul>

<p>Vous pouvez utiliser des nombres ou d'autres caractères dans ces expressions, comme :</p>

<ul>
 <li><code>[ -]</code> — correspond à une espace ou un tiret.</li>
 <li><code>[0-9]</code> — correspond à tout nombre compris entre 0 et 9.</li>
</ul>

<p>Vous pouvez combiner cela pratiquement comme vous l'entendez en précisant les différentes parties les unes après les autres :</p>

<ul>
 <li><code>[Ll].*k</code> — Un seul caractère L en majuscules ou minuscules, suivi de zéro ou plusieurs caractères de n'importe quel type, suivis par un k minuscules.</li>
 <li><code>[A-Z][A-Za-z' -]+</code> — Un seul caractère en majuscules suivi par un ou plusieurs caractères en majuscules ou minuscules, un tiret, une apostrophe ou une espace. Cette combinaison peut s'utiliser pour valider les nom de villes dans les pays anglo‑saxons ; ils débutent par une majuscule et ne contiennent pas d'autre caractère. Quelques exemples de ville de GB correspondant à ce schéma : Manchester, Ashton-under-lyne et Bishop's Stortford.</li>
 <li><code>[0-9]{3}[ -][0-9]{3}[ -][0-9]{4}</code> — Un schéma pour un numéro de téléphone intérieur américain — trois chiffres, suivis par une espace ou un tiret, suivis par trois nombres, suivis par une espace ou un tiret, suivis par quatre nombres. Vous aurez peut-être à faire plus compliqué, car certains écrivent leur numéro de zone entre parenthèses, mais ici il s'agit simplement de faire une démonstration.</li>
</ul>

<p>Voyons un exemple — mettons à jour notre HTML en y ajoutant un attribut <code>pattern</code>, ainsi :</p>

<pre class="brush: html">&lt;form&gt;
  &lt;label for="choose"&gt;Préférez‑vous la banane ou la cerise ?&lt;/label&gt;
  &lt;input id="choose" name="i_like" required pattern="banane|cerise"&gt;
  &lt;button&gt;Soumettre&lt;/button&gt;
&lt;/form&gt;</pre>

<pre class="brush: css">input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 1px solid black;
}</pre>

<p>{{EmbedLiveSample("Validation_selon_une_expression_régulière", "100%", 55)}}</p>

<p>Dans cet exemple, l'élément {{HTMLElement("input")}}} accepte l'une des deux valeurs possibles : la chaîne « banane » ou la chaîne « cerise ».</p>

<p>Maintenant, essayez de changer la valeur à l'intérieur de l'attribut <code>pattern</code> suivant certains exemples vus plus haut et regardez comment les valeurs entrées en sont affectées pour rester valides. Écrivez vos propres textes et voyez comment vous vous en sortez ! Restez dans le domaine des fruits dans la mesure du possible, afin que vos exemples aient du sens !</p>

<div class="note">
<p><strong>Note :</strong> Certains types d'éléments {{HTMLElement("input")}} n'ont pas besoin d'un attribut {{htmlattrxref("pattern", "input")}} pour être validés. Spécifier le type <code>email</code>, par exemple, valide la valeur saisie par rapport à une expression régulière correspondant à une adresse e‑mail bien formée (ou une liste d'adresses e‑mail séparées par des virgules si elle possède l'attribut {{htmlattrxref("multiple", "input")}}. Comme autre exemple, les champs de type <code>url</code> vont automatiquement nécessiter une URL correctement formée.</p>
</div>

<div class="note">
<p><strong>Note :</strong> L'élément {{HTMLElement("textarea")}} ne prend pas en charge l'attribut {{htmlattrxref("pattern", "input")}}.</p>
</div>

<h3 id="Limitation_de_la_taille_des_entrées">Limitation de la taille des entrées</h3>

<p>Tous les champs de texte créés avec ({{HTMLElement("input")}} ou {{HTMLElement("textarea")}}) peuvent être limités en taille avec les attributs {{htmlattrxref("minlength", "input")}} et {{htmlattrxref("maxlength", "input")}}. Le champ sera invalide si sa taille est inférieure à la valeur {{htmlattrxref("minlength", "input")}} ou supérieure la valeur {{htmlattrxref("maxlength", "input")}}. Souvent, les navigateurs ne permettent pas aux utilisateurs de saisir des textes de grande longueur dans les champs texte, mais il peut être utile de disposer d'un contrôle plus fin.</p>

<p>Pour les champs numériques (c'est à dire, &lt;type d'entrée="nombre"&gt;), les attributs {{htmlattrxref("min", "input")}} et {{htmlattrxref("max", "input")}} permettent également des contraintes de validité. Si la valeur du champ est inférieure à l'attribut {{htmlattrxref("min", "input")}} ou supérieure à l'attribut {{htmlattrxref("max", "input")}}, le champ ne sera pas valide.</p>

<p>Prenons un autre exemple. Créez une nouvelle copie du fichier <a href="https://github.com/mdn/learning-area/blob/master/html/forms/form-validation/fruit-start.html">fruit-start.html</a>.</p>

<p>Supprimez maintenant le contenu de l'élément <code>&lt;body&gt;</code> et remplacez-le par le suivant :</p>

<pre class="brush: html">&lt;form&gt;
  &lt;div&gt;
    &lt;label for="choose"&gt;Préférez‑vous la banane ou la cerise ?&lt;/label&gt;
    &lt;input id="choose" name="i_like" required minlength="6" maxlength="6"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;label for="number"&gt;Combien en voulez‑vous ?&lt;/label&gt;
    &lt;input type="number" id="number" name="amount" value="1" min="1" max="10"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;button&gt;Soumettre&lt;/button&gt;
  &lt;/div&gt;
&lt;/form&gt;</pre>

<ul>
 <li>Ici, nous avons donné au champ de texte une taille minimale et maximale de 6 caractères — la même que celle de <em>banane</em> ou <em>cerise</em>. La saisie de moins de 6 caractères s'affichera comme non valide et la saisie de plus de 6 caractères ne sera pas possible dans la plupart des navigateurs.</li>
 <li>Nous avons également contraint le champ <code>number</code> à un <code>min</code> de 1 et un <code>max </code>de 10 — les nombres entrés hors de cette plage seront affichés comme non valides, et vous ne pourrez pas utiliser les flèches d'incrémentation/décrémentation pour porter la valeur en dehors de cette plage.</li>
</ul>

<pre class="brush: html hidden">input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 2px solid black;
}

div {
  margin-bottom: 10px;
}</pre>

<p>Voici cet exemple s'exécutant en « live » :</p>

<p>{{EmbedLiveSample('Limitation_de_la_taille_des_entrées', "100%", 100)}}</p>

<div class="note">
<p><strong>Note :</strong> <code>&lt;input type="number"&gt;</code> (et d'autres types, comme <code>range</code>) acceptent aussi un attribut {{htmlattrxref("step", "input")}} qui spécifie l'incrément en plus ou en moins de la valeur quand les contrôles d'entrée sont utilisés (comme les boutons <kbd>^</kbd> et <kbd>v</kbd>).</p>
</div>

<h3 id="Exemple_complet">Exemple complet</h3>

<p>Voici un exemple complet montrant l'utilisation des fonctionnalités HTML intégrées pour la validation :</p>

<pre class="brush: html">&lt;form&gt;
  &lt;p&gt;
    &lt;fieldset&gt;
      &lt;legend&gt;Qualité&lt;abbr title="Ce champ est obligatoire"&gt;*&lt;/abbr&gt;&lt;/legend&gt;
      &lt;input type="radio" required name="title" id="r1" value="Mr"&gt;&lt;label for="r1"&gt;M.&lt;/label&gt;
      &lt;input type="radio" required name="title" id="r2" value="Ms"&gt;&lt;label for="r2"&gt;Mme.&lt;/label&gt;
    &lt;/fieldset&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="n1"&gt;Quel est votre âge ?&lt;/label&gt;
    &lt;!-- L'attribut pattern peut servir de recours pour les navigateurs dont le type number n'est
         pas implémenté pour input mais qui prennent en charge l'attribut pattern. Veuillez noter
         que les navigateurs prenant en charge l'attribut pattern ne signalent pas d'erreur quand
         il est utilisé avec un champ number. Seule son utilisation ici agit en tant que recours. --&gt;
    &lt;input type="number" min="12" max="120" step="1" id="n1" name="age"
           pattern="\d+"&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="t1"&gt;Quel est votre fruit favori ?&lt;abbr title="Ce champ est obligatoire"&gt;*&lt;/abbr&gt;&lt;/label&gt;
    &lt;input type="text" id="t1" name="fruit" list="l1" required
           pattern="[Bb]anane|[Cc]erise|[Cc]itron|[Ff]raise|[Oo]range|[Pp]omme"&gt;
    &lt;datalist id="l1"&gt;
      &lt;option&gt;Banane&lt;/option&gt;
      &lt;option&gt;Cerise&lt;/option&gt;
      &lt;option&gt;Citron&lt;/option&gt;
      &lt;option&gt;Fraise&lt;/option&gt;
      &lt;option&gt;Orange&lt;/option&gt;
      &lt;option&gt;Pomme&lt;/option&gt;
    &lt;/datalist&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="t2"&gt;Quelle est votre adresse électronique ?&lt;/label&gt;
    &lt;input type="email" id="t2" name="email"&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="t3"&gt;Laissez un court message&lt;/label&gt;
    &lt;textarea id="t3" name="msg" maxlength="140" rows="5"&gt;&lt;/textarea&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;button&gt;Soumettre&lt;/button&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<pre class="brush: css">body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 300px;
  margin: 0;
  padding: 0 5px;
}

p &gt; label {
  display: block;
}

input[type=text],
input[type=email],
input[type=number],
textarea,
fieldset {
/* requis pour composer de manière appropriée les éléments
   de formulaire sur les navigateurs fondés sur WebKit */
  -webkit-appearance: none;

  width : 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

input:invalid {
  box-shadow: 0 0 5px 1px red;
}

input:focus:invalid {
  outline: none;
}</pre>

<p>{{EmbedLiveSample("Exemple_complet", "100%", 450)}}</p>



<h3 id="Messages_adaptés_pour_les_erreurs">Messages adaptés pour les erreurs</h3>

<p>Comme nous avons vu dans les exemples précédents, à chaque fois qu'un utilisateur tente d'envoyer un formulaire invalide, le navigateur affiche un message d'erreur. La manière dont le message est affiché dépend du navigateur.</p>

<p>Ces messages automatiques présentent deux inconvénients:</p>

<ul>
 <li>Il n'y a pas de façon standard de changer leur apparence avec CSS.</li>
 <li>Ils dépendent des paramètres régionaux du navigateur, ce qui signifie que vous pouvez avoir une page dans une langue mais les messages d'erreurs affichés dans une autre.</li>
</ul>

<table>
 <caption>Versions françaises des navigateurs sur une page en anglais</caption>
 <thead>
  <tr>
   <th scope="col">Navigateur</th>
   <th scope="col">Affichage</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Firefox 17 (Windows 7)</td>
   <td><img alt="Example of an error message with Firefox in French on an English page" src="error-firefox-win7.png"></td>
  </tr>
  <tr>
   <td>Chrome 22 (Windows 7)</td>
   <td><img alt="Example of an error message with Chrome in French on an English page" src="error-chrome-win7.png"></td>
  </tr>
  <tr>
   <td>Opera 12.10 (Mac OSX)</td>
   <td><img alt="Example of an error message with Opera in French on an English page" src="error-opera-macos.png"></td>
  </tr>
 </tbody>
</table>

<p>Pour personnaliser l'apparence et le texte de ces messages, vous devez utiliser JavaScript ; il n'est pas possible de l'implémenter en utilisant uniquement HTML et CSS.</p>

<p>HMTL5 fournit une <a href="https://www.w3.org/TR/html5/forms.html#the-constraint-validation-api">API de contraintes de validation</a> pour vérifier et personnaliser l'état des élément d'un formulaire. Il est possible, entre autres, de changer le texte des messages d'erreur. Voici un court exemple :</p>

<pre class="brush: html">&lt;form&gt;
  &lt;label for="mail"&gt;Pourriez-vous nous fournir une adresse mail ?&lt;/label&gt;
  &lt;input type="email" id="mail" name="mail"&gt;
  &lt;button&gt;Envoyer&lt;/button&gt;
&lt;/form&gt;</pre>

<p>En JavaScript, il faut appeler la méthode <a href="/fr/docs/HTML/HTML5/Constraint_validation#Constraint_API's_element.setCustomValidity()" title="/en-US/docs/HTML/HTML5/Constraint_validation#Constraint_API's_element.setCustomValidity()"><code>setCustomValidity()</code></a>:</p>

<pre class="brush: js">var email = document.getElementById("mail");

email.addEventListener("keyup", function (event) {
  if(email.validity.typeMismatch) {
    email.setCustomValidity("J'attend un e-mail, mon cher !");
  } else {
    email.setCustomValidity("");
  }
});</pre>

<p>{{EmbedLiveSample("Messages_adaptés_pour_les_erreurs", "100%", 50)}}</p>

<h2 id="Validation_de_formulaires_avec_JavaScript">Validation de formulaires avec JavaScript</h2>

<p>Si vous souhaitez avoir le contrôle de l'apparence des messages d'erreur, ou si vous voulez gérer le comportement des navigateurs n'ayant pas implémenté la validation de formulaire HTML5, vous n'avez pas d'autre choix que d'utiliser JavaScript.</p>

<h3 id="API_de_contraintes_de_validation_HTML5">API de contraintes de validation HTML5</h3>

<p>De plus en plus de navigateurs prennent maintenant en charge l'API de validation des contraintes, et elle devient fiable. Cette API se compose d'un ensemble de méthodes et de propriétés disponibles sur chaque élément de formulaire.</p>

<p>Propriétés de l'API de validation des contraintes</p>

<table>
 <thead>
  <tr>
   <th scope="col">Propriétés</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>validationMessage</code></td>
   <td>Un message (dans la langue locale) décrivant les contraintes de validation que le contrôle ne satisfait pas (si c'est le cas), ou une chaîne vide si le contrôle n'est pas soumis à validation (<code>willValidate</code> est alors <code>false</code>), ou bien la valeur de l'élément satisfait ses contraintes.</td>
  </tr>
  <tr>
   <td><code>validity</code></td>
   <td>Un objet {{domxref("ValidityState")}} qui décrit l'état de validité de l'élément.</td>
  </tr>
  <tr>
   <td><code>validity.customError</code></td>
   <td>Renvoie <code>true</code> si l'élément à une erreur personnalisée, <code>false</code> a contrario.</td>
  </tr>
  <tr>
   <td><code>validity.patternMismatch</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément ne correspond pas au motif fourni, <code>false</code> dans le cas contraire. Si la méthode renvoie <code>true</code>, l'élément fera partie de la pseudo-classe CSS {{cssxref(":invalid")}}.</td>
  </tr>
  <tr>
   <td><code>validity.rangeOverflow</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément est supérieure au maximum défini, <code>false</code> dans le cas contraire. Si le retour est <code>true</code>, l'élément fera partie des  pseudo-classes CSS {{cssxref(":invalid")}} et {{cssxref(":out-of-range")}}.</td>
  </tr>
  <tr>
   <td><code>validity.rangeUnderflow</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément est plus petite que le minimum défini, <code>false</code> dans le cas contraire. Si le retour est <code>true</code>, l'élément fera partie des pseudo-classes CSS {{cssxref(":invalid")}} et {{cssxref(":out-of-range")}}.</td>
  </tr>
  <tr>
   <td><code>validity.stepMismatch</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément ne correspond pas aux règles définies par l'attribut <code>step</code>,<code>false</code> a contrario. Si le retour est <code>true</code>, l'élément fera partie des pseudo-classes CSS {{cssxref(":invalid")}} et {{cssxref(":out-of-range")}}.</td>
  </tr>
  <tr>
   <td><code>validity.tooLong</code></td>
   <td>Renvoie <code>true</code> si la taille de l'élément est supérieure à la longueur maximum définie, <code>false</code> dans le cas contraire. Si le retour est <code>true</code>, l'élément fera partie des pseudo-classes CSS {{cssxref(":invalid")}} et {{cssxref(":out-of-range")}}.</td>
  </tr>
  <tr>
   <td><code>validity.typeMismatch</code></td>
   <td>Renvoie <code>true</code> si la syntaxe de la valeur de l'élément n'est pas correcte ; <code>false</code> dans le cas contraire. Si le retour est <code>true</code>, l'élément sera de la pseudo-classe CSS {{cssxref(":invalid")}}.</td>
  </tr>
  <tr>
   <td><code>validity.valid</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément n'a pas de problème de validité, sinon <code>false</code>. L'élément sera de la pseudo-classe CSS {{cssxref(":valid")}} si le retour est <code>true</code> ; de la pseudo-classe CSS {{cssxref(":invalid")}} si le retour est <code>false</code>.</td>
  </tr>
  <tr>
   <td><code>validity.valueMissing</code></td>
   <td>Renvoie <code>true</code> si l'élément n'a pas de valeur alors que le champ est requis, sinon<code>false</code>. L'élément sera de la pseudo-classe CSS {{cssxref(":invalid")}} si le retour est <code>true</code>.</td>
  </tr>
  <tr>
   <td><code>willValidate</code></td>
   <td>Retourne <code>true</code> si l'élément est validé lorsque le formulaire est soumis, <code>false</code> dans le cas contraire.</td>
  </tr>
 </tbody>
</table>

<h4 id="Méthodes_de_l'API_de_validation_des_contraintes">Méthodes de l'API de validation des contraintes</h4>

<table>
 <thead>
  <tr>
   <th scope="col">Méthodes</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>checkValidity()</code></td>
   <td>Renvoie <code>true</code> si la valeur de l'élément n'a pas de problème de validation, <code>false</code> autrement. Si l'élément est invalide, cette méthode déclenche aussi un événement {{event("invalid")}} sur cet élément.</td>
  </tr>
  <tr>
   <td><code>setCustomValidity(<em>message</em>)</code></td>
   <td>Ajoute un message d'erreur personnalisé à l'élément ; si vous définissez un message d'erreur personnalisé, l'élément est considéré comme invalide, et le message spécifié est affiché. Cela vous permet d'utiliser du code JavaScript pour établir une erreur de validation autre que celles offertes par l'API standard des contraintes de validation. Le message est affiché à l'utilisateur lorsque le problème est rapporté. Si l'argument est une chaîne de caractères vide, l'erreur personnalisée est considérée comme effacée.</td>
  </tr>
 </tbody>
</table>

<p>Pour les anciens navigateurs, il existe <a href="https://hyperform.js.org/">une prothèse d'émulation (<em>polyfill</em>) comme Hyperform</a>, pour compenser le défaut de prise en charge de cette API. Comme vous utilisez déjà JavaScript, l'utilisation d'une prethèse d'émulation n'est pas un souci supplémentaire pour la conception ou l'implémentation de votre site ou application Web.</p>

<h4 id="Exemple_utilisant_la_validation_des_contraintes">Exemple utilisant la validation des contraintes</h4>

<p>Voyons comment utiliser l'API pour créer des messages d'erreur personnalisés. Tout d'abord, le HTML :</p>

<pre class="brush: html">&lt;form novalidate&gt;
  &lt;p&gt;
    &lt;label for="mail"&gt;
      &lt;span&gt;Veuillez saisir une adresse e-mail :&lt;/span&gt;
      &lt;input type="email" id="mail" name="mail"&gt;
      &lt;span class="error" aria-live="polite"&gt;&lt;/span&gt;
    &lt;/label&gt;
  &lt;p&gt;
  &lt;button&gt;Envoyer&lt;/button&gt;
&lt;/form&gt;</pre>

<p>Ce formulaire simple utilise l'attribut {{htmlattrxref("novalidate","form")}} pour désactiver la validation automatique par le navigateur ; cela permet donc à notre script d'avoir le contrôle sur la validation. Toutefois, cela ne désactive la prise en charge par l'API de validation des contraintes, ni l'application des pseudo-classes CSS  {{cssxref(":valid")}}, {{cssxref(":invalid")}}, {{cssxref(":in-range")}} et {{cssxref(":out-of-range")}}. Cela signifie que, même si le navigateur ne vérifie pas automatiquement la validité du formulaire avant l'envoi des données, vous pouvez toujours effectuer cette validation et définir l'apparence du formulaire par vous-même.</p>

<p>L'attribut <code><a href="/fr/docs/Accessibility/ARIA/ARIA_Live_Regions">aria-live</a></code> garantit que nos messages d'erreur personnalisés seront affichés à tout le monde, y compris les personnes utilisant des techniques d'assistance comme des lecteurs d'écran.</p>

<h5 id="CSS">CSS</h5>

<p>Ce CSS compose le formulaire et les messages d'erreur pour les rendre plus attrayants.</p>

<pre class="brush: css">/* Juste pour que notre exemple soit plus joli */
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
}

p * {
  display: block;
}

input[type=email]{
  -webkit-appearance: none;

  width: 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* Voici notre composition pour les champs invalides */
input:invalid{
  border-color: #900;
  background-color: #FDD;
}

input:focus:invalid {
  outline: none;
}

/* Voici la mise en forme pour les erreurs */
.error {
  width  : 100%;
  padding: 0;

  font-size: 80%;
  color: white;
  background-color: #900;
  border-radius: 0 0 5px 5px;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.error.active {
  padding: 0.3em;
}</pre>

<h5 id="JavaScript">JavaScript</h5>

<p>Le code JavaScript suivant gère la validation personnalisée des erreurs.</p>

<pre class="brush: js">// Il y a plusieurs façon de sélectionner un nœud DOM ; ici on récupère
// le formulaire et le champ d'e-mail ainsi que l'élément span
// dans lequel on placera le message d'erreur

var form  = document.getElementsByTagName('form')[0];
var email = document.getElementById('mail');
var error = document.querySelector('.error');

email.addEventListener("input", function (event) {
  // Chaque fois que l'utilisateur saisit quelque chose
  // on vérifie la validité du champ e-mail.
  if (email.validity.valid) {
    // S'il y a un message d'erreur affiché et que le champ
    // est valide, on retire l'erreur
    error.innerHTML = ""; // On réinitialise le contenu
    error.className = "error"; // On réinitialise l'état visuel du message
  }
}, false);
form.addEventListener("submit", function (event) {
  // Chaque fois que l'utilisateur tente d'envoyer les données
  // on vérifie que le champ email est valide.
  if (!email.validity.valid) {

    // S'il est invalide, on affiche un message d'erreur personnalisé
    error.innerHTML = "J'attends une adresse e-mail correcte, mon cher !";
    error.className = "error active";
    // Et on empêche l'envoi des données du formulaire
    event.preventDefault();
  }
}, false);</pre>

<p>Voici le résultat:</p>

<p>{{EmbedLiveSample("Exemple_utilisant_la_validation_des_contraintes", "100%", 130)}}</p>

<p>L'API de validation des contraintes fournit un outil puissant pour gérer la validation des formulaires, en vous laissant un contrôle sur l'interface utilisateur bien supérieur à ce que vous auriez pu avoir avec uniquement HTML et CSS. </p>

<h3 id="Valider_des_formulaires_sans_API_intégrée">Valider des formulaires sans API intégrée</h3>

<p>Il arrive parfois, comme c'est le cas avec des navigateurs anciens ou de <a href="/fr/docs/HTML/Forms/How_to_build_custom_form_widgets">widgets personnalisés</a>, de ne pas pouvoir (ou vouloir) utiliser l'API de validation des contraintes. Dans ce cas, vous pourrez toujours utiliser JavaScript pour valider votre formulaire. Valider un formulaire est plus une question d'interface utilisateur que de réelle validation des données.</p>

<p>Pour valider un formulaire, vous devez vous poser un certain nombre de questions:</p>

<dl>
 <dt>Quel type de validation dois-je réaliser ?</dt>
 <dd>Vous devez déterminer comment valider vos données : opération sur des chaînes de caractères, conversion de type, expressions rationnelles, etc. C'est comme vous voulez. Mais retenez simplement que les données de formulaire sont toujours du texte et sont toujours fournies à vos scripts sous forme de chaînes de caractères.</dd>
 <dt>Que dois-je faire si le formulaire n'est pas valide ?</dt>
 <dd>C'est clairement une affaire d'interface utilisateur. Vous devez décider comment le formulaire doit se comporter : enverra-t-il quand même les données ? Devriez-vous mettre en évidence les champs qui sont en erreur ? Devriez-vous afficher des messages d'erreur ?</dd>
 <dt>Comment puis-je aider l'utilisateur à corriger ses données invalides?</dt>
 <dd><p>Pour limiter la frustration de l'utilisateur, il est très important de fournir autant d'information d'aide que nécessaire pour le guider dans la correction de sa saisie. Vous devriez afficher des suggestions en amont pour que l'utilisateur sache ce qui est attendu, ainsi que des messages d'erreur clairs. Si vous souhaitez vous plonger dans les exigences d'interface utilsateur pour la validation de formulaires, voici quelques articles (en anglais) utiles que vous devriez lire :</p>
 <ul>
  <li>SmashingMagazine : <a href="http://uxdesign.smashingmagazine.com/2012/06/27/form-field-validation-errors-only-approach/" rel="external">Form-Field Validation: The Errors-Only Approach</a></li>
  <li>SmashingMagazine : <a href="http://www.smashingmagazine.com/2009/07/07/web-form-validation-best-practices-and-tutorials/" rel="external">Web Form Validation: Best Practices and Tutorials</a></li>
  <li>Six Revision : <a href="http://sixrevisions.com/user-interface/best-practices-for-hints-and-validation-in-web-forms/" rel="external">Best Practices for Hints and Validation in Web Forms</a></li>
  <li>A List Apart : <a href="https://www.alistapart.com/articles/inline-validation-in-web-forms/" rel="external">Inline Validation in Web Forms</a></li>
 </ul>
 </dd>
</dl>

<h4 id="Exemple_sans_utilisation_de_la_validation_des_contraintes">Exemple sans utilisation de la validation des contraintes</h4>

<p>Afin d'illustrer le propos, réécrivons le précédent exemple afin qu'il fonctionne avec d'anciens navigateurs:</p>

<pre class="brush: html">&lt;form&gt;
  &lt;p&gt;
    &lt;label for="mail"&gt;
        &lt;span&gt;Veuillez saisir une adresse e-mail :&lt;/span&gt;
        &lt;input type="text" class="mail" id="mail" name="mail"&gt;
        &lt;span class="error" aria-live="polite"&gt;&lt;/span&gt;
    &lt;/label&gt;
  &lt;p&gt;
  &lt;!-- Certains navigateurs historiques ont besoin de l'attribut
       `type` avec la valeur `submit` sur l'élément `button` --&gt;
  &lt;button type="submit"&gt;Envoyer&lt;/button&gt;
&lt;/form&gt;</pre>

<p>Comme vous pouvez voir, le HTML est quasiment identique; nous avons juste enlevé les fonctionnalités de validation HTML. Notez que <a href="/fr/docs/Accessibility/ARIA" title="/en-US/docs/Accessibility/ARIA">ARIA</a> est une spécification indépendante qui n'est pas spécifiquement liée à HTML5.</p>

<h5 id="CSS_2">CSS</h5>

<p>De même, nous n'avons pas eu à changer radicalement les CSS ; nous avons simplement transformé la pseudo-classe {{cssxref(":invalid")}} en une vraie classe et évité d'utiliser le sélecteur d'attribut, qui ne fonctionne pas avec Internet Explorer 6.</p>

<pre class="brush: css">/* On améliore l'aspect de l'exemple avec ces quelques règles */
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
}

p * {
  display: block;
}

input.mail {
  -webkit-appearance: none;

  width: 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* Voici les règles de mise en forme pour les champs invalides */
input.invalid{
  border-color: #900;
  background-color: #FDD;
}

input:focus.invalid {
  outline: none;
}

/* Voici les règles utilisées pour les messages d'erreur */
.error {
  width  : 100%;
  padding: 0;

  font-size: 80%;
  color: white;
  background-color: #900;
  border-radius: 0 0 5px 5px;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.error.active {
  padding: 0.3em;
}</pre>

<h5 id="JavaScript_2">JavaScript</h5>

<p>Les changements les plus importants sont dans le code JavaScript, qui nécessite bien plus que de simples retouches.</p>

<pre class="brush: js">// Il existe moins de méthode pour sélectionner un nœud DOM
// avec les navigateurs historiques
var form  = document.getElementsByTagName('form')[0];
var email = document.getElementById('mail');

// Ce qui suit est une bidouille pour atteindre le prochain nœud Element dans le DOM
// Attention à cette méthode, elle peut permettre de construire une boucle
// infinie. Pour les navigateurs plus récents, on utilisera element.nextElementSibling
var error = email;
while ((error = error.nextSibling).nodeType != 1);

// Pour respecter la spécification HTML5
var emailRegExp = /^[a-zA-Z0-9.!#$%&amp;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;

// De nombreux navigateurs historiques ne supportent pas la méthode
// addEventListener. Voici une méthode simple (il en existe d'autres)
function addEvent(element, event, callback) {
  var previousEventCallBack = element["on"+event];
  element["on"+event] = function (e) {
    var output = callback(e);

    // Une fonction de rappel (callback) qui renvoie `false`
    // pour arrêter la chaîne des callback
    // et interrompre l'exécution du callback d'événement.
    if (output === false) return false;

    if (typeof previousEventCallBack === 'function') {
      output = previousEventCallBack(e);
      if(output === false) return false;
    }
  }
};

// On peut désormais reconstruire notre validation de contrainte
// Étant donné qu'on n'utilise pas la pseudo-classe CSS, il faut
// explicitement gérer la classe valid/invalid du champ e-mail
addEvent(window, "load", function () {
  // Ici, on teste si le champ est vide (rappel : le champ n'est pas obligatoire)
  // S'il ne l'est pas, on vérifie que son contenu est une adresse e-mail valide.
  var test = email.value.length === 0 || emailRegExp.test(email.value);

  email.className = test ? "valid" : "invalid";
});

// Ici, on définit ce qui se passe lorsque l'utilisateur
// saisit quelque chose dans le champ
addEvent(email, "keyup", function () {
  var test = email.value.length === 0 || emailRegExp.test(email.value);
  if (test) {
    email.className = "valid";
    error.innerHTML = "";
    error.className = "error";
  } else {
    email.className = "invalid";
  }
});

// Ici, on définit ce qui se passe lorsque l'utilisateur
// tente d'envoyer les données du formulaire
addEvent(form, "submit", function () {
  var test = email.value.length === 0 || emailRegExp.test(email.value);

  if (!test) {
    email.className = "invalid";
    error.innerHTML = "Merci d'écrire une adresse e-mail valide.";
    error.className = "error active";

    // Certains navigateurs historiques ne supportent pas
    // la méthode event.reventDefault()
    return false;
  } else {
    email.className = "valid";
    error.innerHTML = "";
    error.className = "error";
  }
});</pre>

<p>Voici le résultat:</p>

<p>{{EmbedLiveSample("Exemple_sans_utilisation_de_la_validation_des_contraintes", "100%", 130)}}</p>

<p>Comme vous avez pu le voir, il n'est pas si difficile de créer par soi-même un système de validation. La difficulté consiste à rendre le tout assez générique pour l'utiliser à la fois sur toutes les plateformes et pour chaque formulaire que vous pourriez créer. Il existe de nombreuses bibliothèques permettant ce genre de validation de formulaire ; n'hésitez pas à les utiliser. En voici quelques exemples :</p>

<ul>
 <li>Bibliothèques indépendantes :
  <ul>
   <li><a href="http://rickharrison.github.com/validate.js/" rel="external">Validate.js</a></li>
  </ul>
 </li>
 <li>Greffons jQuery :
  <ul>
   <li><a href="http://bassistance.de/jquery-plugins/jquery-plugin-validation/" rel="external">Validation</a> </li>
  </ul>
 </li>
</ul>

<h4 id="Validation_à_distance">Validation à distance</h4>

<p>Il peut être utile, dans certains cas, d'effectuer une validation à distance. Ce genre de validation est nécessaire lorsque les données saisies par l'utilisateur sont liées à des données supplémentaires stockées sur le serveur hébergeant votre application. Prenons par exemple les formulaires d'inscription, pour lesquels on vous demande un nom d'utilisateur. Pour éviter toute duplication d'un nom d'utilisateur, il est plus judicieux d'effectuer une requête AJAX pour vérifier la disponibilté du nom d'utilisateur que de demander à envoyer les données saisies et de renvoyer le formulaire avec une erreur.</p>

<p>Pour réaliser une telle validation, plusieurs précautions doivent être prises :</p>

<ul>
 <li>Il est nécessaire d'exposer une API et des données ; assurez-vous que ces données ne soient pas critiques.</li>
 <li>Un décalage (<em>lag</em>) du réseau nécessite une validtion asynchrone. L'interface utilisateur doit être conçue de façon à pas être bloquée si cette validation n'est pas réalisée correctement.</li>
</ul>

<h2 id="Conclusion">Conclusion</h2>

<p>La validation d'un formulaire ne requiert pas de code JavaScript complexe, mais il est nécessaire de penser tout particulièrement à l'utilisateur. Rappelez-vous de toujours aider l'utilisateur à corriger les données qu'il saisit. Pour ce faire, assurez-vous de toujours :</p>

<ul>
 <li>Afficher des messages d'erreur explicites.</li>
 <li>Être tolérant sur le format des données à envoyer.</li>
 <li>Indiquer exactement où est l'erreur (en particulier pour les formulaires longs).</li>
</ul>

<p>{{PreviousMenuNext("Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires", "Web/Guide/HTML/Formulaires/Comment_construire_des_widgets_de_formulaires_personnalisés", "Web/Guide/HTML/Formulaires")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/Forms/Your_first_form">Mon premier formulaire HTML</a></li>
 <li><a href="/fr/docs/Learn/Forms/How_to_structure_a_web_form">Comment structurer un formulaire HTML</a></li>
 <li><a href="/fr/docs/Learn/Forms/Basic_native_form_controls">Les widgets natifs pour formulaire</a></li>
 <li><a href="/fr/docs/Learn/Forms/Sending_and_retrieving_form_data">Envoi des données de formulaire</a></li>
 <li><a href="/fr/docs/Learn/Forms/Form_validation">Validation des données de formulaire</a></li>
 <li><a href="/fr/docs/Learn/Forms/How_to_build_custom_form_controls">Comment construire des widgets personnalisés pour formulaire</a></li>
 <li><a href="/fr/docs/Learn/Forms/Sending_forms_through_JavaScript">Envoi de formulaires à l'aide du JavaScript</a></li>
 <li><a href="/fr/docs/Learn/Forms/HTML_forms_in_legacy_browsers">Formulaires HTML dans les navigateurs anciens</a></li>
 <li><a href="/fr/docs/Learn/Forms/Styling_web_forms">Mise en forme des formulaires HTML</a></li>
 <li><a href="/fr/docs/Learn/Forms/Advanced_form_styling">Mise en forme avancée des formulaires HTML</a></li>
 <li><a href="/fr/docs/Learn/Forms/Property_compatibility_table_for_form_controls">Table de compatibilité des propriétés pour les widgets de formulaire</a></li>
</ul>