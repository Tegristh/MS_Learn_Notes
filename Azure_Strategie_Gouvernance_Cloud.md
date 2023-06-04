# Créer une stratégie de gouvernance cloud sur Azure

[cour complet site de microsoft](https://learn.microsoft.com/fr-fr/training/modules/build-cloud-governance-strategy-azure/)


## Contrôlez l'accès aux ressources cloud en utilisant le contrôle d'accès basé sur les rôles Azure

Azure propose des rôles intégrés qui décrivent les règles d’accès courantes des ressources cloud. Vous pouvez également définir vos propres rôles. Chaque rôle a un ensemble associé de permissions d’accès qui se rapportent à ce rôle. Quand vous attribuez un ou plusieurs rôles à des personnes ou des groupes, ils reçoivent toutes les autorisations d’accès associées.

### Comment le contrôle d'accès en fonction du rôle est-il appliqué aux ressources?

Le contrôle d’accès en fonction du rôle s’applique à une étendue, qui est une ressource ou un ensemble de ressources auxquelles cet accès s’applique.

Les étendues incluent :

 - Un groupe d’administration (collection de plusieurs abonnements).
 - Un seul abonnement.
 - Un groupe de ressources.
 - Une seule ressource.

Les observateurs, les utilisateurs gérant des ressources, les administrateurs et les processus automatisés illustrent les genres d’utilisateurs ou de comptes généralement attribués à chacun des différents rôles.

Quand vous accordez l’accès à une étendue parente, ces autorisations sont héritées par toutes les étendues enfants. Par exemple :

- Quand vous attribuez le rôle **Propriétaire** à un utilisateur au niveau de l’étendue du groupe d’administration, cet utilisateur peut gérer tout le contenu de tous les abonnements au sein du groupe d’administration.
 - Quand vous attribuez le rôle **Lecteur** à un groupe au niveau de l’étendue de l’abonnement, les membres de ce groupe peuvent afficher tous les groupes de ressources et les ressources de l’abonnement.
 - Lorsque vous attribuez le rôle **Contributeur** à une application au niveau de l’étendue du groupe de ressources, l’application peut gérer les ressources de tous les types au sein de ce groupe de ressources, mais pas d’autres groupes de ressources de l’abonnement.

#### Quand dois-je utiliser RBAC Azure?

Utilisez RBAC Azure quand vous avez besoin de :

 - Permettre à un utilisateur de gérer les machines virtuelles d’un abonnement, et à un autre de gérer les réseaux virtuels.
 - Permettre à un groupe d’administrateurs de bases de données de gérer les bases de données SQL d’un abonnement
 - Permettre à un utilisateur de gérer toutes les ressources d’un groupe de ressources (machines virtuelles, sites web, sous-réseaux, etc.)
 - Permettre à une application d’accéder à toutes les ressources d’un groupe de ressources

#### Comment RBAC Azure est-il appliqué?

RBAC utilise un modèle d’autorisation. Lorsque vous êtes affecté à un rôle, un RBAC vous permet d’effectuer certaines actions telles que lire, écrire ou supprimer. Si une attribution de rôle vous accorde des autorisations de lecture sur un groupe de ressources et qu’une autre attribution de rôle vous accorde des autorisations d’écriture sur le même groupe de ressources, vous disposez à la fois d’autorisations de lecture et d’écriture sur ce groupe de ressources.

#### A qui s'applique RBAC Azure?

Vous pouvez appliquer RBAC Azure à une personne particulière ou à un groupe. Vous pouvez également appliquer un RBAC Azure à d’autres types d’identité spéciaux, comme des principaux de service et des identités managées. Ces types d’identités sont utilisés par les applications et services pour automatiser l’accès aux ressources Azure.

 - **Administrateurs informatiques** Cette équipe a la propriété ultime des ressources informatiques, à la fois locales et dans le cloud. L’équipe a besoin d’un contrôle total sur toutes les ressources.
 - **Sauvegarde et récupération après sinistre** Cette équipe est responsable de la gestion de l’intégrité des sauvegardes régulières et de l’invocation de toute récupération de données ou de système.
 - **Coûts et facturation** Les personnes de cette équipe suivent et rapportent les dépenses liées à la technologie. Elles gèrent également les budgets internes de l’organisation.
 - **Opérations de sécurité** Cette équipe surveille et répond aux incidents de sécurité liés à la technologie. L’équipe a besoin d’un accès permanent aux fichiers journaux et aux alertes de sécurité.

#### Comment puis-je faire pour gérer les autorisations RBAC Azure?

Vous gérez les autorisations d’accès dans le volet Contrôle d’accès (IAM) du portail Azure. Ce volet indique qui a accès à quelle portée et quels rôles s’appliquent. Vous pouvez également accorder ou supprimer des accès à partir de ce volet.

## Empêcher les modifications accidentelles à l'aide de verrous de ressource

**Un verrou de ressource empêche la suppression ou modification accidentelle des ressources.**

Même avec des stratégies de contrôle d’accès en fonction du rôle Azure (RBAC Azure) en place, il existe toujours un risque que les personnes dotées du niveau d’accès approprié puissent supprimer des ressources cloud critiques. Imaginez un verrou de ressource comme un système d’avertissement qui vous rappelle qu’une ressource ne doit pas être supprimée ou modifiée.

### Comment faire pour gérer des verrous de ressource?

Vous pouvez gérer les verrous de ressource à partir du portail Azure, de PowerShell, d’Azure CLI ou depuis un modèle Azure Resource Manager.

Pour voir, ajouter ou supprimer des verrous dans le portail Azure, accédez à la section “Paramètres” du volet “Verrous” de n’importe quelle ressource dans le portail Azure.

### Quels sont les niveaux de verrouillage disponibles?

Vous pouvez appliquer des verrous à un abonnement, à un groupe de ressources ou à une ressource individuelle. Vous pouvez définir le niveau de verrouillage sur **CanNotDelete** ou **ReadOnly***.

 - **CanNotDelete** signifie que les personnes autorisées peuvent toujours lire et modifier une ressource, mais qu’elles ne peuvent pas la supprimer sans supprimer au préalable le verrou.
 - **ReadOnly** signifie que les personnes autorisées peuvent lire une ressource, mais qu’elles ne peuvent pas la supprimer ni la modifier. L’application de ce verrou est comme restreindre tous les utilisateurs autorisés aux autorisations accordées par le rôle “Lecteur”(Reader) dans RBAC Azure.

### Comment faire pour supprimer ou modifier une ressource verrouillée?

Bien que le verrouillage permette d’éviter des modifications accidentelles, vous pouvez quand même apporter des modifications en suivant un processus en deux étapes.

Pour modifier une ressource verrouillée, vous devez d’abord retirer le verrou. Après avoir retiré le verrou, vous pouvez appliquer toutes les actions que vous êtes autorisé à effectuer. Cette étape supplémentaire permet d’exécuter l’action, mais elle aide à protéger vos administrateurs contre le fait de faire quelque chose qu’ils n’auraient peut-être pas voulu faire.

Les verrous de ressource s’appliquent indépendamment des autorisations RBAC définies. Même si vous êtes le propriétaire de la ressource, vous devez toujours retirer le verrou avant de pouvoir effectuer l’activité bloquée.

### Combiner des verrous de ressource avec Azure Blueprints

Que se passe-t-il si un administrateur cloud supprime accidentellement un verrou de ressource ? Si le verrou de ressource est retiré, les ressources associées peuvent être modifiées ou supprimées.

Pour rendre le processus de protection plus solide, vous pouvez combiner des verrous de ressource avec Azure Blueprints. Azure Blueprints vous permet de définir l’ensemble des ressources Azure standard dont votre organisation a besoin. Par exemple, vous pouvez définir un blueprint qui spécifie qu’un certain verrou de ressource doit exister. Azure Blueprints peut remplacer automatiquement le verrou de ressource si ce verrou est retiré.

## Organiser vos ressources Azure à l'aide de balises

Au fur et à mesure que votre utilisation du cloud augmente, il est de plus en plus important de rester organisé. Une bonne stratégie d’organisation vous aide à comprendre votre utilisation du cloud et peut vous aider à gérer les coûts.

Une façon d’organiser des ressources associées consiste à les placer dans leurs propres abonnements. Vous pouvez également utiliser des groupes de ressources pour gérer des ressources associées. Les balises de ressource constituent une autre façon d’organiser les ressources. Les balises fournissent des informations supplémentaires, ou métadonnées, sur vos ressources. Ces métadonnées sont utiles pour :

- **Gestion des ressources** Les étiquettes vous permet de localiser et d’agir sur des ressources associées à des charges de travail spécifiques, des environnements, des unités commerciales et des propriétaires.

- **Gestion et optimisation des coûts** Les étiquettes vous permettent de regrouper des ressources afin d’établir des rapports sur les coûts, d’allouer des centres de coûts internes, de suivre des budgets et de prévoir une estimation des coûts.

- **Gestion des opérations** Les étiquettes vous permettent de regrouper les ressources en fonction de l’importance de leur disponibilité pour votre entreprise. Ce regroupement vous aide à formuler des contrats de niveau de service (SLA). Un contrat SLA est une garantie de durée de bon fonctionnement ou de performances entre vos utilisateurs et vous.

- **Sécurité** Les étiquettes vous permettent de classifier les données en fonction de leur niveau de sécurité, comme public ou confidentiel.

- **Gouvernance et conformité réglementaire** Les étiquettes vous permettent d’identifier les ressources conformes aux exigences de gouvernance ou de conformité réglementaire, comme la norme ISO 27001. Les tags peuvent également faire partie de vos efforts de mise en application des normes. Par exemple, vous pouvez exiger que toutes les ressources soient balisées avec un nom de propriétaire ou de service.

- **Optimisation et automatisation des charges de travail** Les étiquettes peuvent vous aider à visualiser toutes les ressources qui participent à des déploiements complexes. Par exemple, vous pouvez étiqueter une ressource avec sa charge de travail ou son nom d’application associé et utiliser des logiciels tels que Azure DevOps pour effectuer des tâches automatisées sur ces ressources.

### Comment faire pour gérer des balises de ressource?

Vous pouvez ajouter, modifier ou supprimer des balises de ressource à l’aide de PowerShell, d’Azure CLI, de modèles Azure Resource Manager, de l’API REST ou du portail Azure.

Vous pouvez également gérer les balises à l’aide d’Azure Policy. Par exemple, vous pouvez appliquer des balises à un groupe de ressources, mais ces tags ne sont pas automatiquement appliqués aux ressources dans ce groupe de ressources. Vous pouvez utiliser Azure Policy pour vous assurer qu’une ressource hérite des mêmes tags que son groupe de ressources parent. Vous en apprendrez davantage sur Azure Policy plus tard dans ce module.

Vous pouvez également utiliser Azure Policy pour appliquer des règles et des conventions de balisage. Par exemple, vous pouvez exiger que certaines balises soient ajoutées aux nouvelles ressources au fur et à mesure de leur provisionnement. Vous pouvez également définir des règles qui réappliquent les balises qui ont été supprimées.

### Exemple de structure de balisage

Une balise de ressource comprend un nom et une valeur. Vous pouvez attribuer plusieurs balises à chaque ressource Azure.

## Contrôler et auditer vos ressources à l'aide d'Azure Policy

Azure Policy est un service Azure qui vous permet de créer, attribuer et gérer des stratégies qui contrôlent ou auditent vos ressources. Ces stratégies appliquent des règles différentes sur toutes vos configurations de ressources afin que ces configurations restent conformes aux standards de l’entreprise.

### Comment le service Azure Policy définit-il des stratégies?

Azure Policy vous permet de définir à la fois des stratégies individuelles et des groupes de stratégies associées, appelées initiatives. Azure Policy évalue vos ressources et met en évidence celles qui ne sont pas conformes aux stratégies que vous avez créées. Azure Policy vous permet également d’empêcher la création de ressources non conformes.

Azure Policy est fourni avec des définitions de stratégie et d’initiative intégrées pour le stockage, le réseau, le calcul, Security Center et le monitoring. Par exemple, si vous définissez une stratégie qui autorise seulement une certaine taille de référence SKU pour les machines virtuelles à utiliser dans votre environnement, cette stratégie est appelée quand vous créez une machine virtuelle et chaque fois que vous redimensionnez des machines virtuelles existantes. Azure Policy assure également l’évaluation et le monitoring de toutes les machines virtuelles actuellement dans votre environnement.

Dans certains cas, Azure Policy permet de corriger automatiquement les ressources et configurations non conformes pour garantir l’intégrité de l’état des ressources. Par exemple, si toutes les ressources d’un certain groupe de ressources doivent être marquées avec l’étiquette “AppName” et une valeur de “SpecialOrders”, Azure Policy réappliquera automatiquement cette balise si elle était manquante.

Azure Policy s’intègre aussi à Azure DevOps en appliquant toutes les stratégies relatives aux pipelines d’intégration continue et de livraison continue qui concernent les phases de prédéploiement et de postdéploiement de vos applications.

### Azure Policy en action

L’implémentation d’une stratégie dans Azure Policy implique trois tâches :

#### .1 Créer une définition de stratégie

Une définition de stratégie indique ce qu’il faut évaluer et l’action à entreprendre. Par exemple, vous pouvez empêcher les machines virtuelles d’être déployées dans certaines régions Azure. Vous pouvez également auditer vos comptes de stockage pour vérifier qu’ils acceptent uniquement des connexions en provenance de réseaux autorisés.

Chaque définition de stratégie présente des conditions dans lesquelles elle est appliquée. Une définition de stratégie entraîne aussi un effet qui se produit quand les conditions sont remplies. 

#### .2 Attribuer la définition aux ressources

Pour mettre en œuvre vos définitions de stratégie, vous affectez les définitions aux ressources. Une attribution de stratégie est une définition de stratégie qui s’applique à une étendue spécifique. Cette étendue peut être un groupe d’administration (une collection de plusieurs abonnements), un seul abonnement ou un groupe de ressources.

Toutes les ressources enfants au sein de cette étendue héritent des attributions de stratégie. Si une stratégie est appliquée à un groupe de ressources, cette stratégie est appliquée à toutes les ressources dans celui-ci. Vous pouvez exclure une sous-étendue de l’attribution de stratégie si des ressources enfants spécifiques ont besoin d’en être exemptées.

#### .3 Examiner les résultats de l'évaluation

Quand une condition est évaluée par rapport à vos ressources existantes, chaque ressource est marquée comme conforme ou non conforme. Cous pouvez passer en revue les résultats de stratégie non conformes afin de prendre toutes les mesures nécessaires.

L’évaluation de la stratégie se produit environ une fois par heure. Si vous apportez des modifications à votre définition de stratégie et vous créez une attribution de stratégie, cette stratégie est évaluée sur vos ressources dans l’heure.

### Que sont les initiatives Azure Policy?

Une initiative Azure Policy est un moyen de regrouper ensemble des stratégies associées. La définition d’initiative contient toutes les définitions de stratégie qui permettent de suivre l’état de conformité d’un objectif plus large.

Par exemple, Azure Policy comprend une initiative nommée Activer la supervision dans Azure Security Center. Son objectif est de superviser toutes les recommandations de sécurité disponibles pour tous les types de ressources Azure dans Azure Security Center.

Sous cette initiative, les définitions de politiques suivantes sont incluses :

- **Surveiller les bases de données SQL non chiffrées** dans Security Center Cette stratégie surveille les bases de données et les serveurs SQL Server non chiffrés.
- **Surveiller les vulnérabilités du système d’exploitation** dans Security Center Cette stratégie surveille les serveurs qui ne répondent pas à la base de référence des vulnérabilités du système d’exploitation configurée.
- **Surveiller Endpoint Protection manquant dans Security Center** Cette stratégie surveille les serveurs qui n’ont aucun agent Endpoint Protection installé.

Azure Policy inclut également des initiatives qui supportent les normes de conformité réglementaires, telles que HIPAA et ISO 27001.

#### Comment faire pour définir une initiative?

Vous définissez des initiatives en utilisant le portail Azure ou des outils en ligne de commande. À partir du portail Azure, vous pouvez effectuer des recherches dans la liste des initiatives intégrées à Azure. Vous pouvez également créer votre propre définition de stratégie personnalisée.

#### Comment faire pour attribuer une initiative?

Comme une attribution de stratégie, une attribution d’initiative est une définition d’initiative attribuée à une étendue spécifique d’un groupe d’administration, d’un abonnement ou d’un groupe de ressources.

Même si vous n’avez qu’une seule stratégie, une initiative vous permet d’augmenter le nombre de politiques au fil du temps. Étant donné que l’initiative associée reste attribuée, il est plus facile d’ajouter et de supprimer des stratégies sans avoir à modifier l’attribution de stratégie de vos ressources.

## Gouverner plusieurs abonnements à l'aide d'Azure Blueprints

Que se passe-t-il lorsque votre environnement cloud commence à se développer au-delà d’un seul abonnement ? Comment pouvez-vous faire évoluer la configuration de ces fonctionnalités, en sachant qu’elles doivent s’appliquer aux ressources incluses dans les nouveaux abonnements ?

Au lieu de configurer des fonctionnalités comme Azure Policy pour chaque nouvel abonnement, Avec Azure Blueprints vous pouvez définir un ensemble reproductible d’outils de gouvernance et de ressources Azure standard requis par votre organisation. Cela permet aux équipes de développement de créer et de déployer rapidement de nouveaux environnements dans le respect des exigences de conformité de l’organisation avec un ensemble de composants intégrés qui accélèrent les phases de développement et de déploiement.

### Azure Blueprints en action

L’implémentation d’un blueprint dans Azure Blueprints implique ces trois étapes :

.1 Créer un blueprint Azure
.2 Attribuer le blueprint
.3 Suivez les attributions du blueprint

Avec Azure Blueprints, la relation entre la définition du blueprint (ce qui doit être déployé) et l’affectation du blueprint (ce qui a été déployé) est conservée. En d’autres termes, Azure crée un enregistrement qui associe une ressource au blueprint qui la définit. Cette connexion vous permet de suivre et d’auditer vos déploiements.

Les blueprints sont aussi versionnés. Le contrôle de version vous permet de suivre et de commenter les modifications apportées à votre blueprint.

### Que sont les artefacts de blueprint?

Chaque composant dans la définition de plan directeur est appelé un “artefact”.

Il est possible que les artefacts n’aient pas de paramètres supplémentaires (configurations). C’est le cas, par exemple, de la stratégie Déployer la détection des menaces sur les serveurs SQL qui ne nécessite aucune configuration supplémentaire.

Les artefacts peuvent également contenir un ou plusieurs paramètres que vous pouvez configurer.

Vous pouvez spécifier la valeur d’un paramètre lorsque vous créez la définition de blueprint ou quand vous attribuez cette dernière à une étendue. Ainsi, vous pouvez gérer un seul blueprint standard, tout en ayant la flexibilité de spécifier les paramètres de configuration appropriés au niveau de chaque étendue où la définition est attribuée.

### Comment utiliser les Blueprints Azure pour la conformité à l'ISO 27001?

La norme ISO 27001 s’applique à la sécurité des systèmes informatiques. Elle est publiée par l’Organisation internationale de normalisation. Azure Blueprints comporte plusieurs définitions de blueprint intégrées qui se rapportent à la norme ISO 27001.

En tant qu’administrateur informatique, vous décidez d’examiner la définition ISO 27001 : Blueprint des services partagés. Voici les grandes lignes de votre plan.

Définissez un groupe d’administration nommé PROD-MG. N’oubliez pas qu’un groupe d’administration gère l’accès, les stratégies et la conformité de plusieurs abonnements Azure. Chaque nouvel abonnement Azure est ajouté à ce groupe d’administration lors de la création de l’abonnement.
Créez une définition de blueprint basée sur le modèle ISO 27001 : Blueprint des services partagés. Publiez ensuite le blueprint.
Attribuez le blueprint à votre groupe d’administration PROD-MG.

## Accélérer votre parcours d'adoption du cloud en utilisant Cloud Adoption Framework pour Azure

Le Cloud Adoption Framework pour Azure vous fournit des conseils éprouvés pour vous aider dans votre parcours d’adoption du cloud. Cloud Adoption Framework vous aide à créer et à implémenter les stratégies métier et technologiques nécessaires pour réussir dans le cloud.
