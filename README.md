# P05_Income_Prediction
<h2><strong><em>Data Analyst Certification by OpenClassrooms, in partnership with&nbsp;ENSAE-ENSAI</em></strong></h2>
<p><em>Predicting the future income of potential customers for a bank</em></p>
<p><br /><em>Skills:</em></p>
<ul>
<li><em>Master the basics of inferential statistics</em></li>
<li><em>Master the basics of probability</em></li>
<li><em>Model data</em></li>
</ul>
<div>
<div>
<div>
<div>
<div>
<h1>Effectuez une pr&eacute;diction de revenus</h1>
</div>
</div>
</div>
<div>
<h3>Pr&eacute;requis</h3>
<p>Pour ce projet, il sera utile de savoir r&eacute;aliser une analyse de&nbsp;<strong>statistique descriptive</strong>&nbsp;en langages&nbsp;<strong>R</strong>&nbsp;ou&nbsp;<strong>Python</strong>&nbsp;(avec des repr&eacute;sentations graphiques). Il faudra &eacute;galement appliquer des mod&eacute;lisations de type&nbsp;<strong>ANOVA</strong>&nbsp;ou&nbsp;<strong>r&eacute;gression lin&eacute;aire</strong>.</p>
<h3>Sc&eacute;nario</h3>
<p>Vous &ecirc;tes employ&eacute; dans une banque, pr&eacute;sente dans de nombreux pays &agrave; travers le monde. Celle-ci souhaite cibler de nouveaux clients potentiels, plus particuli&egrave;rement les jeunes en &acirc;ge d'ouvrir leur tout premier compte bancaire.</p>
<p>Cependant, elle souhaite cibler les prospects les plus susceptibles d'avoir, plus tard dans leur vie, de hauts revenus.</p>
<p>L'&eacute;quipe dans laquelle vous travaillez a donc re&ccedil;u pour mission de cr&eacute;er un mod&egrave;le permettant de d&eacute;terminer le revenu potentiel d'une personne.</p>
<p>Tr&egrave;s bien.</p>
<p>"Quelles informations avons-nous ?" demandez-vous &agrave; votre sup&eacute;rieur, qui vous r&eacute;pond : "&Agrave; vrai dire... quasiment aucune : uniquement le revenu des parents, car nous allons cibler les enfants de nos clients actuels, ainsi que le pays o&ugrave; ils habitent. C'est tout ! Ah oui, une derni&egrave;re chose : ce mod&egrave;le doit &ecirc;tre valable pour la plupart des pays du monde. Je vous laisse m&eacute;diter l&agrave;-dessus&hellip; Bon courage !"</p>
<p>Avec aussi peu de donn&eacute;es disponibles, cela semble &ecirc;tre un sacr&eacute; challenge !</p>
<p>Ainsi, vous proposez une r&eacute;gression lin&eacute;aire avec 3 variables :</p>
<ul>
<li>le revenu des parents ;</li>
<li>le revenu moyen du pays dans lequel habite le prospect ;</li>
<li>l'indice de Gini calcul&eacute; sur les revenus des habitants du pays en question.&nbsp;</li>
</ul>
<aside data-claire-semantic="warning">
<p>Ce projet ne traite que de la construction et de l'interpr&eacute;tation du mod&egrave;le. Vous n'irez pas jusqu'&agrave; la phase de pr&eacute;diction</p>
</aside>
<h3>Les donn&eacute;es</h3>
<p>Ce fichier contient les donn&eacute;es de la&nbsp;<a href="https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/parcours-data-analyst/data-projet7.csv">World Income Distribution</a>, dat&eacute;e de 2008.</p>
<p>Cette base de donn&eacute;es est compos&eacute;e principalement d'&eacute;tudes r&eacute;alis&eacute;es au niveau national pour bon nombre de pays, et contient les distributions de revenus des populations concern&eacute;es.</p>
<p>Vous t&eacute;l&eacute;chargerez &eacute;galement les indices de Gini estim&eacute;s par la Banque mondiale, disponibles&nbsp;<a href="http://data.worldbank.org/indicator/SI.POV.GINI">&agrave; cette adresse</a>. Libre &agrave; vous de trouver &eacute;galement d'autres sources, ou de recalculer les indices de Gini &agrave; partir de la World Income Distribution.</p>
<p>Vous aurez &eacute;galement besoin de r&eacute;cup&eacute;rer le nombre d'habitants de chaque pays pr&eacute;sent dans votre base.</p>
<h3>Vos missions</h3>
<h4>Mission 1</h4>
<p>R&eacute;sumez les donn&eacute;es utilis&eacute;es :</p>
<ul>
<li>ann&eacute;e(s) des donn&eacute;es utilis&eacute;es ;</li>
<li>nombre de pays pr&eacute;sents ;</li>
<li>population couverte par l'analyse (en termes de pourcentage de la population mondiale).</li>
</ul>
<p>Les donn&eacute;es de la World Income Distribution pr&eacute;sentent pour chaque pays les quantiles de la distribution des revenus de leur population respective.</p>
<ul>
<li>De quel type de quantiles s'agit-il (quartiles, d&eacute;ciles, etc.) ?</li>
<li>&Eacute;chantillonner une population en utilisant des quantiles est-il selon vous une bonne m&eacute;thode ? Pourquoi ?</li>
</ul>
<aside data-claire-semantic="information">
<p>Nous appellerons ici chaque quantile une&nbsp;<em>classe de revenu.<br /></em>Ainsi, la valeur de la colonne&nbsp;<em>income</em>&nbsp;pour un quantile donn&eacute; peut &ecirc;tre vue comme le revenu moyen des personnes appartenant &agrave; la classe de revenu correspondante &agrave; ce quantile.</p>
</aside>
<p>L'unit&eacute; utilis&eacute;e dans la colonne&nbsp;<em>income</em>&nbsp;de la world income distribution est le $PPP. Cette unit&eacute; est calcul&eacute;e par la Banque mondiale, selon la m&eacute;thode Elt&ouml;te-K&ouml;ves-Szulc. Apr&egrave;s vous &ecirc;tre document&eacute;, vous expliquerez &agrave; votre mentor&nbsp;<em>tr&egrave;s bri&egrave;vement</em>&nbsp;&agrave; quoi correspond cette unit&eacute; et pourquoi elle est pertinente pour une comparaison de pays diff&eacute;rents (Il n'est pas n&eacute;cessaire de donner cette explication lors de la soutenance).</p>
<h4>Mission 2</h4>
<ul>
<li>Montrez la diversit&eacute; des pays en termes de distribution de revenus &agrave; l'aide d'un graphique. Celui-ci repr&eacute;sentera le revenu moyen (axe des ordonn&eacute;es, sur une &eacute;chelle logarithmique) de chacune des classes de revenus (axe des abscisses) pour 5 &agrave; 10 pays que vous aurez choisis pour montrer la diversit&eacute; des cas.</li>
<li>Repr&eacute;sentez la courbe de Lorenz de chacun des pays choisis.</li>
<li>Pour chacun de ces pays, repr&eacute;sentez l'&eacute;volution de l'indice de Gini au fil des ans.</li>
<li>Classez les pays par indice de Gini. Donnez la moyenne, les 5 pays ayant l'indice de Gini le plus &eacute;lev&eacute; et les 5 pays ayant l'indice de Gini le plus faible. En quelle position se trouve la France ?</li>
</ul>
<h4>Mission 3</h4>
<p>Dans l'&eacute;tat actuel, nous avons &agrave; disposition deux des trois variables explicatives souhait&eacute;es :</p>
<p>\(m_{j}\)&nbsp;le revenu moyen du pays \(j\)</p>
<p>\(G_{j}\)&nbsp;l'indice de Gini du pays&nbsp;\(j\)</p>
<p>Il nous manque donc, pour un individu \(i\)&nbsp;, la classe de revenu&nbsp;\(c_{i,parent}\)&nbsp;de ses parents.</p>
<aside data-claire-semantic="information">
<p>Nous supposons ici que l'on associe &agrave; chaque individu&nbsp;\(i\)&nbsp;une unique classe&nbsp;\(c_{i,parent}\)&nbsp;; quel que soit le nombre de parents de&nbsp;\(i\).</p>
</aside>
<p>Nous allons donc simuler cette information gr&acirc;ce &agrave; un coefficient&nbsp;\(\rho_{j}\)&nbsp;(propre &agrave; chaque pays&nbsp;\(j\)&nbsp;), mesurant une corr&eacute;lation entre le revenu de l'individu&nbsp;\(i\)&nbsp;et le revenu de ses parents. Ce coefficient sera ici appel&eacute;&nbsp;<em>coefficient d'&eacute;lasticit&eacute; ;</em>&nbsp;il mesure la&nbsp;<em>mobilit&eacute; interg&eacute;n&eacute;rationnelle du revenu</em>.</p>
<aside data-claire-semantic="information">
<p>Pour plus d'informations sur le calcul du coefficient d'&eacute;lasticit&eacute;, consulter&nbsp;<a href="https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/parcours-data-analyst/2011-measuring-intergenerational-income-mobility-art.pdf">ce document</a>, notamment l'&eacute;quation 1 de la page 8. Ce coefficient est d&eacute;termin&eacute; par une r&eacute;gression lin&eacute;aire simple dans laquelle le logarithme du revenu de l'enfant&nbsp;\(Y_{child}\)&nbsp;est une fonction du logarithme du revenu des parents&nbsp;\(Y_{parent}\)&nbsp;:</p>
<p>\[ln(Y_{child}) = \alpha + \rho_j\ ln(Y_{parent}) + \epsilon\]</p>
</aside>
<p>Pour obtenir le coefficient d'&eacute;lasticit&eacute;, deux possibilit&eacute;s s'offrent &agrave; vous :</p>
<ol>
<li>Vous baser sur ces coefficients donn&eacute;s par la Banque mondiale,&nbsp;<a href="https://s3.eu-west-1.amazonaws.com/course.oc-static.com/projects/DANV1_P7/GDIMMay2018+(1).csv">dans GDIM dataset</a>. Le coefficient d'&eacute;lasticit&eacute; est donn&eacute; pour certains pays, sous le nom d'IGE Income (relative IGM in income).</li>
<li>Vous baser sur des estimations provenant de multiples &eacute;tudes, extrapol&eacute;es &agrave; diff&eacute;rentes r&eacute;gions du monde : elles se trouvent dans le fichier&nbsp;<a href="https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/parcours-data-analyst/projet_7.zip">elasticity.txt</a>. Attention, ces donn&eacute;es sont parfois anciennes.</li>
</ol>
<p>Il est aussi possible de combiner ces deux approches.</p>
<p>Pour chaque pays, nous allons utiliser une g&eacute;n&eacute;ration al&eacute;atoire de la classe de revenu des parents, &agrave; partir de ces seules deux informations :</p>
<ul>
<li>\(\rho_j\)</li>
<li>la classe de revenu de l'enfant \(c_{i,child}\).</li>
</ul>
<aside data-claire-semantic="warning">
<p>Attention &agrave; bien utiliser la&nbsp;<em>classe</em>&nbsp;de revenu de l'enfant (qui est un nombre compris entre 1 et 100 si vous utilisez 100 quantiles), plut&ocirc;t que son revenu PPP. De m&ecirc;me, on ne cherche pas &agrave; g&eacute;n&eacute;rer le revenu des parents, mais la&nbsp;<em>classe</em>&nbsp;de revenu des parents&nbsp;\(c_{i,parent}\).</p>
</aside>
<p>Voici le protocole de g&eacute;n&eacute;ration pour un pays&nbsp;\(j\)&nbsp;donn&eacute;, qui se base sur l'&eacute;quation donn&eacute;e ci dessus :</p>
<aside data-claire-semantic="information">
<p>Un exemple de code permettant de r&eacute;aliser les op&eacute;rations 1 &agrave; 6 est donn&eacute; tout en bas. Libre &agrave; vous de l'utiliser. Notamment, la fonction <code data-claire-semantic="text">proba_cond</code> vous donnera les probabilit&eacute;s&nbsp;\(P(c_{i,parent}|c_{i,child},j)\).</p>
</aside>
<ol>
<li>G&eacute;n&eacute;rez un grand nombre&nbsp;\(n\)&nbsp;de r&eacute;alisations d'une variable que nous appellerons \(ln(Y_{parent})\)&nbsp;selon une loi normale. Le choix de la moyenne et de l'&eacute;cart type n'auront pas d'incidence sur le r&eacute;sultat final.&nbsp;\(n\)&nbsp;doit &ecirc;tre sup&eacute;rieur &agrave; 1000 fois le nombre de quantiles.</li>
<li>G&eacute;n&eacute;rez&nbsp;\(n\)&nbsp;r&eacute;alisations du terme d'erreur&nbsp;\(\epsilon\)&nbsp;selon une loi normale de moyenne 0 et d'&eacute;cart type 1.</li>
<li>Pour une valeur donn&eacute;e de&nbsp;\(\rho_j\)&nbsp;(par exemple 0.9), calculez&nbsp;\(y_{child} = e^{\alpha+\rho_jln(y_{parent})+\epsilon}\)&nbsp;. Le choix de&nbsp;\( \alpha\)&nbsp;n'a aucune incidence sur le r&eacute;sultat final et peut &ecirc;tre supprim&eacute;. &Agrave; ce stade,&nbsp;\(y_{child}\)&nbsp;contient des valeurs dont l'ordre de grandeur ne refl&egrave;te pas la r&eacute;alit&eacute;, mais cela n'a pas d'influence pour la suite.</li>
<li>Pour chacun des&nbsp;\(n\)&nbsp;individus g&eacute;n&eacute;r&eacute;s, calculez la classe de revenu \(c_{i,child}\)&nbsp;ainsi que la classe de revenu de ses parents&nbsp;\(c_{i,parent}\)&nbsp;, &agrave; partir de&nbsp;\(y_{child}\)&nbsp;et&nbsp;\(y_{parent}\).</li>
<li>&Agrave; partir de cette derni&egrave;re information, estimez pour chaque \(c_{i,child}\)&nbsp;la distribution conditionnelle de&nbsp;\(c_{i,parent}\)&nbsp;. Par exemple, si vous observez 6 individus ayant &agrave; la fois \(c_{i,child} = 5\)&nbsp;et&nbsp;\(c_{i,parent} = 8\)&nbsp;, et que 200 individus sur 20000 ont&nbsp;\( c_{i,child} = 5\)&nbsp;, alors la probabilit&eacute; d'avoir&nbsp;\( c_{i,parent} = 8\)&nbsp;sachant \(c_{i,child} = 5\)&nbsp;et sachant&nbsp;\(\rho_j=0.9\)&nbsp;sera estim&eacute;e &agrave; 6/200 (On note cette probabilit&eacute; comme ceci :&nbsp;\(P(c_{i,parent}=8|c_{i,child}=5,\rho_j=0.9) = 0.03\)). Si votre population est divis&eacute;e en&nbsp;\(c\)&nbsp;classes de revenu, vous devriez alors avoir&nbsp;\(c^2\)&nbsp;estimations de ces probabilit&eacute;s conditionnelles, pour chaque pays.</li>
<li>Optionnellement et pour v&eacute;rifier la coh&eacute;rence de votre code, vous pouvez cr&eacute;er un graphique repr&eacute;sentant ces distributions conditionnelles. Voici 2 exemples pour une population segment&eacute;e en 10 classes, pour 2 valeurs de&nbsp;\(\rho_j\)&nbsp;: l'une traduisant une forte mobilit&eacute; (0.1) et l'autre une tr&egrave;s faible mobilit&eacute; (0.9) :
<figure><a href="https://user.oc-static.com/upload/2018/06/25/15299299335283_p01.png"><img src="https://user.oc-static.com/upload/2018/06/25/15299299335283_p01.png" alt="Faible mobilit&eacute;" /></a>
<figcaption>Forte mobilit&eacute;</figcaption>
</figure>
<figure><a href="https://user.oc-static.com/upload/2018/06/25/1529929973606_p09.png"><img src="https://user.oc-static.com/upload/2018/06/25/1529929973606_p09.png" alt="Forte mobilit&eacute;" /></a>
<figcaption>Faible mobilit&eacute;</figcaption>
</figure>
</li>
<li>&Eacute;ventuellement et pour &eacute;viter toute confusion, effacez les individus que vous venez de g&eacute;n&eacute;rer (nous n'en avons plus besoin), et ne gardez que les distributions conditionnelles.</li>
<li>Nous allons maintenant travailler sur un nouvel &eacute;chantillon. Celui-ci sera cr&eacute;&eacute; &agrave; partir de la WID. Pour chaque individu de la World Income Distribution, cr&eacute;ez-en 499 "clones". La taille de votre nouvel &eacute;chantillon sera donc 500 fois plus grand que celui de la World Income Distribution.</li>
<li>Pour chaque&nbsp;\(c_{i,child}\)&nbsp;et chaque pays, il y a maintenant 500 individus. Vous attribuerez aux 500 individus leurs classes&nbsp;\( c_{i,parent}\)&nbsp;conform&eacute;ment aux distributions trouv&eacute;es pr&eacute;c&eacute;demment. Par exemple, si&nbsp;\(P(c_{i,parent}=8|c_{i,child}=5,\rho_j=0.9) = 0.03\)&nbsp;, alors vous assignerez la classe&nbsp;\(c_{i,parent} = 8\)&nbsp;&agrave; 15 des 500 individus du pays&nbsp;\( j\)&nbsp;ayant&nbsp;\(c_{i,child}=5\)&nbsp;, car 500*0.03 = 15.</li>
<li>&Eacute;ventuellement et pour &eacute;viter toute confusion, effacez la variable&nbsp;\(c_{i,child}\) : nous n'en avons pas besoin pour la mission 4.</li>
<li>Assurez-vous que votre nouvel &eacute;chantillon contiennent bien les variables initialement pr&eacute;sentes dans la World Income Distribution :&nbsp;\(m_j\)&nbsp;et&nbsp;\(G_j\)&nbsp;.</li>
</ol>
<p>Utilisez ce nouvel &eacute;chantillon pour la mission 4.</p>
<h4>Mission 4</h4>
<p>Pour cette mission 4, nous chercherons &agrave; expliquer le revenu des individus en fonction de plusieurs variables explicatives : le pays de l'individu, l'indice de Gini de ce pays, la classe de revenus des parents, etc.</p>
<p>Appliquez une ANOVA sur vos donn&eacute;es, en n&rsquo;incluant comme variable explicative que le pays de l&rsquo;individu. Analysez la performance du mod&egrave;le.</p>
<aside data-claire-semantic="warning">
<p>Pour chacune des r&eacute;gressions suivantes, vous testerez 2 version : l'une en exprimant le revenu moyen du pays et les revenus (parents &amp; enfants) en logarithme (ln), l'autre en les laissant tels quels. Vous choisirez la version la plus performante pour r&eacute;pondre aux question.</p>
</aside>
<p>Appliquez une r&eacute;gression lin&eacute;aire sur vos donn&eacute;es, en incluant comme variables explicatives uniquement le revenu moyen du pays de l&rsquo;individu et l&rsquo;indice de Gini du pays de l&rsquo;individu. Quel est le pourcentage de variance expliqu&eacute;e par votre mod&egrave;le&nbsp;?</p>
<p>Selon ce mod&egrave;le, donnez la d&eacute;composition de variance totale expliqu&eacute;e par :</p>
<ul>
<li>le pays de naissance (ie. le revenu moyen et l&rsquo;indice de Gini) ;</li>
<li>les autres facteurs non consid&eacute;r&eacute;s dans le mod&egrave;le (efforts, chance, etc.).</li>
</ul>
<p>Am&eacute;liorez le mod&egrave;le pr&eacute;c&eacute;dent en incluant maintenant la classe de revenu des parents. Quel est le pourcentage de variance expliqu&eacute;e par ce nouveau mod&egrave;le&nbsp;?</p>
<div data-claire-semantic="question">
<p>En observant le coefficient de r&eacute;gression associ&eacute; &agrave; l&rsquo;indice de Gini, peut-on affirmer que le fait de vivre dans un pays plus in&eacute;galitaire favorise plus de personnes qu&rsquo;il n&rsquo;en d&eacute;favorise ?</p>
</div>
<p>Selon ce dernier mod&egrave;le, donnez la d&eacute;composition de variance totale expliqu&eacute;e par&nbsp;:</p>
<ul>
<li>le pays de naissance et le revenu des parents</li>
<li>les autres facteurs non consid&eacute;r&eacute;s dans le mod&egrave;le (efforts, chance, etc.)</li>
</ul>
<h3>Livrables</h3>
<p>Voici les livrables attendus, &agrave; transmettre dans une archive .zip :</p>
<ul>
<li>le&nbsp;<strong>code</strong>&nbsp;Python ou R permettant de r&eacute;pondre &agrave; l'ensemble de&nbsp;vos missions. Puisqu'il y a beaucoup de questions, faites attention &agrave; ce que votre code soit clair, qu'il d&eacute;limite bien les diff&eacute;rentes parties et questions, et qu'il soit correctement comment&eacute; ;</li>
<li>les&nbsp;<strong>graphiques</strong>&nbsp;g&eacute;n&eacute;r&eacute;s, dans un format image .png ou .jpg&nbsp;</li>
</ul>
<aside data-claire-semantic="information">
<p>Pour faciliter votre passage au jury, d&eacute;posez sur la plateforme, dans un dossier nomm&eacute; &ldquo;<em>P7_nom_prenom</em>&rdquo;, tous les livrables du projet. Chaque livrable doit &ecirc;tre nomm&eacute; avec le num&eacute;ro du projet et selon l'ordre dans lequel il appara&icirc;t, par exemple &ldquo;<em>P7_01_code</em>&rdquo;, &ldquo;<em>P7_02_graphiques</em>&rdquo;, et ainsi de suite.</p>
</aside>
<h3>Soutenance</h3>
<p>Pour chacune des missions propos&eacute;es,<strong>&nbsp;vous d&eacute;taillerez votre d&eacute;marche</strong>, en pr&eacute;cisant&nbsp;<strong>les &eacute;ventuels probl&egrave;mes rencontr&eacute;s</strong>&nbsp;(ainsi que la mani&egrave;re dont vous y avez fait face) et en r&eacute;pondant &agrave; toutes les questions pos&eacute;es dans l'&eacute;nonc&eacute;. La soutenance durera environ<strong>&nbsp;25 minutes,</strong>&nbsp;avec 5 &agrave; 10 minutes de questions-r&eacute;ponses &eacute;ventuelles.</p>
</div>
</div>
</div>
