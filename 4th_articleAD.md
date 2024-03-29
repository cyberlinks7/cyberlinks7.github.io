
<div align="center">

<h1><strong>Active Directory : Les différentes étapes de compromission de l’AD du point de vue de l’attaquant (Hacker)</strong></h1>

</div>
<br/>
<br/>

<p align="justify"> Après avoir défini les bases en ce qui concerne l’active directory, nous allons prendre la place d’un acteur sensible dans le domaine de la sécurité: celui du Hacker. Cet article présentera donc les grandes étapes de l’intrusion d’un hacker dans un système en terminant avec un scénario d’exemple.</p>
<p align="justify"> Déjà pour débuter, nous vous proposons le schéma suivant que nous empruntons à Pentester Academy qui présente le cycle suivi par l’attaquant. Nous tenons à rappeler que pour l’attaquant, dans une architecture AD, c’est d’atteindre les contrôleurs de domaine. Vous vous posez la question de savoir pourquoi ? Nous vous invitons à revoir nos articles sur la description de l’AD.</p>

<p align="center"> 
<img src="img4AD.png" align="center">
</p>

<p align="justify"> Nous allons décrire chacune de ces étapes afin que vous puissiez comprendre le modus operandi d’un attaquant. Cet article vous permettra à la fois de bien comprendre le procédé des cyberattaquants vis à vis de l’Active Directory et de pouvoir faire des campagne de pentest en interne au niveau de vos entreprises actuelles. Sans perdre de temps, abordons la phase de reconnaissance.</p>
  
<p align="justify"> La reconnaissance consiste pour un attaquant à collecter le maximum d’informations possibles en ce qui concerne son entreprise cible. Elle a donc pour but de comprendre le contexte de l’entreprise, avoir une connaissance maximale de tous les aspects internes & externes qui décrivent le système d’information cible. C’est donc le point de départ de toute attaque car elle permet à l’attaquant d’analyser sa cible, d’identifier et découvrir ses faiblesses, défauts et vulnérabilités.</p>
  
<p align="justify"> En ce qui concerne l’AD, il est important d’identifier les informations liées à sa structure logique et quoi de plus important que de s’orienter vers les domaines et les forêts, qui pour rappel, représentent respectivement les frontières administrative & sécuritaire de l’architecture AD. La seconde phase de notre cycle consiste à réaliser une énumération des éléments caractéristiques du domaine (Domain Enum), des entités avec lesquelles ils communiquent, des relations de confiance existantes entre le domaine cible et les autres domaines.</p>
  
<p align="justify"> Dans cette phase, plusieurs informations seront recherchées telles que les nombres et noms des domaines se trouvant dans l’architecture cible, les politiques en place, les contrôleurs de domaines, les utilisateurs, les ressources et les propriétés qui les caractérisent, les ordinateurs, les GPO, les OU, etc… Vous l’aurez compris, cette phase donne une vision encore plus claire de l’entreprise après l’étape de la réconnaissance car elle permet d’obtenir plus d’informations sur l’AD. Pour se faire plusieurs outils existent mais ne font pas l’objet de cet article. N”hésitez pas à nous signifier si vous êtes intéressés par un article qui abordera quelques outils intéressants pour chacune des phases.</p>
  
<p align="justify"> Mais vous devez vous posez une question, comment après avoir recupérer des informations sur l’entreprise, un attaquant est déjà capable de récupérer des informations sur l’architecture AD d’une entreprise cible par exemple. Si vous vous êtes posés cette question, c’est très bien car en effet il y a une étape intermédiaire qui n’a pas été évoqué. Cependant, il est bien de préciser que nous sommes dans le cadre d’un exemple où nous sommes d’un point de vue Hacker et pas de hacking ethique qui aurait pu être une prestation demandée en interne dans une entreprise pour éprouver leur système informatique. Dans ce cas, l’étape que nous allons maintenant évoquée est plutôt négligée dans certains cas dépendant de la prestation demandée (En boite noire, blanche ou grise). Si ces termes ne vous disent rien du tout, n’hésitez pas à nous le signifier en commentaire.</p>
  
<p align="justify"> Revenons donc à cette fameuse étape. Imaginez vous, un hacker collecte toutes les informations sur votre entreprise, connait plutôt sa cible et a donc des idées des vulnérabilités et défauts de votre entreprise. L’étape intermédiaire consiste donc à accéder au système d’information par l’exploitation d’une vulnérabilité propre à votre entreprise. Quels sont ces vecteurs ? Je vous donne un exemple assez fréquent. Votre entreprise a un personnel pas très sensibilisé d’un point de vue cybersécurité, vous pourrez être soumis à une campagne de phishing de la part de l’attaquant qui par la suite pourrait vous inviter à ouvrir une pièce jointe qui lui permettra d’accéder à votre ordinateur à distance. Un autre exemple serait de passer par la problématique liée aux BYOD (Bring Your Own Device) dans la mesure où un utilisateur de votre réseau pourrait utiliser son équipement personnel déjà infecté par un logiciel malveillant pour accéder à des ressources sensibles de l’entreprise. Si le réseau ne dispose pas des équipements couvrant tous les types de terminaux finaux, votre système peut être rapidement mis à mal. </p>

<p align="justify"> Cette étape nous fait penser à deux éléments clés en entreprise: la gestion des risques cyber et la sensibilisation des utilisateurs. Nous pourrons aborder ces thèmes dans de prochains articles si vous êtes intéressés. </p>
  
<p align="justify"> Pour revenir aux étapes d’attaques, l’on suppose que l’attaquant a maintenant accès à votre système et a pu énumérer l’ensemble des éléments caractérisant votre système AD. Dependant de l’utilisateur corrompu pour accéder au système cible, l’attaquant pourra être amené à faire de l’élévation de privilèges (Local Priv Esc). Comme son nom l’indique, cela permet à un attaquant de passer d’un compte utilisateur simple à un compte administrateur sur la machine corrompue qui lui ouvrira un plus grand spectre de manoeuvres réalisable. Ainsi, il sera capable de pouvoir continuer sa progression dans le système car des outils nécessitent les droits d’admin.</p>
  
<p align="justify"> Lorsque l’attaquant aura les droits d’administration, il sera capable de continuer sur son élan et progresser dans la phase d’énumération. Il faut dire que dépendant du statut du compte utilisateur, les retours de outils pourraient être différents, raison pour laquelle lorsqu’on obtient les droits admin, on reprend la phase d’énumération sinon de reconnaissance comme le décrivait le cycle introductif (Admin Recon). </p>
  
<p align="justify"> Rappelez vous, l’objectif de l’attaquant est de pouvoir atteindre le contrôleur de domaine et pour se faire il sera obligé de se déplacer d’un utilisateur à un autre ou d’une machine à une autre. Ce mouvement, ce déplacement dans le système est qualifié de mouvement latéral (Lateral movement) et a pour visée principale de se rapprocher de sa cible en recherchant à augmenter ses privilèges par la même occasion. </p>
  
<p align="justify"> Dans sa quête de l’atteinte du contrôleur de domaine, l’attaquant devra obtenir un certain type de droits, des droits qui lui permettront d’administrer tous les objets et ressources liés à l’AD: ce sont les privilèges de l’administrateur du domaine (Domain admin priviliege). Les administrateurs de domaine sont les utilisateurs qui peuvent modifier les informations dans l’AD, la configuration des serveurs AD et leurs comptes sont donc très prisés par les attaquants car ils seront capable de réaliser des actions à leurs guises.</p>
  
<p align="justify"> Dans une entreprise, il peut exister différents domaines ou forêts qui sont interconnectées à travers des liaisons de confiance (Trusts). Un attaquant après avoir obtenu les droits d’administrateur de privilèges pourrait vouloir profiter de ses liaisons afin de franchir les frontières administratives et sécuritaires representées par les domaines et les forêts en exploitant les liaisons de confiance qui existent entre le domaine ou la forêt corrompue et les entités tierces. Ce types d’attaque est qualifié de Cross trust attack. Pour finir, des moyens peuvent être mis en oeuvre par l’attaquant afin de procéder à l’exfiltration de données ou à réaliser de la persistence afin de pouvoir accéder a système à sa guise par la suite. La persistence et l’exfiltration intervient en fin de processus, le tout dépendant de l’objectif de l’attaquant vis à vis de sa cible.</p>
  
<p align="justify"> Prenons un exemple de bout en bout avec les étapes suivies par un attaquant pour cloturer cet article. L’attaquant a pour but d’intégrer une entreprise de la place. Alors, que fait-il ? </p>

- <p align="justify">Etude du contexte de l’entreprise et surtout des vulnérabilités de l’entreprise: l’attaquant se rend compte que quelques employés publient beaucoup de leurs informations personnelles sur les réseaux sociaux et décide de faire du social engineering. Il applique donc du spearphishing sur les employés identifiés par rapport aux centres d’intérêts qu’il a pu dégager. 
- <p align="justify">L’employé tombe dans le piège et l’attaquant réussi à avoir un accès à distance via le protocole RDP sur sa machine professionnelle. Cependant, cet utilisateur n’a pas les droits d’administration.L’attaquant procède donc à l’énumération de l’architecture AD et recherche les failles qui lui permettront de monter en privilège et obtenir les droits administrateur machine.
- <p align="justify">Une fois cette étape réalisée, l’attaquant continue son énumération avec ses privilèges et recherche maintenant des vulnérabilités qui découleront sur des mouvements latéraux jusqu’à l’atteinte et l’acquisition des privilèges d’administrateur de domaine. L’attaquant a maintenant accès au contrôleur de domaine auquel son point d’entrée était relié.
- <p align="justify">Son but étant d’intégrer l’entreprise, il a maintenant accès à toutes les ressources et peut créer un utilisateur lambda dans des groupes à haut privilèges qui lui permettra de se connecter sans détection par les autres administrateurs si des revues périodiques de droit ne sont pas réalisées.

<p align="justify"> Ce scénario est intéressant et vous avez certainement déjà été confronté à de telles situations. Nous vous invitons à suivre nos prochains articles pour avoir une idée des outils utilisés dans chacune des étapes. A très vite :-) </p>

## Source:
  
- [Reconnaissance dans le hacking](https://www.jigsawacademy.com/blogs/cyber-security/reconnaissance-in-hacking/)
- [Mouvement latéral](https://www.cybertalk.org/what-is-lateral-movement-computing/#:~:text=Lateral%20movement%20refers%20to%20a,of%20moving%20through%20a%20system.)
- [Administrateur du domaine](https://www.ssh.com/academy/iam/user/domain-administrator)
- CRTP Bootcamp Pentester Academy
 
