# Vue d'ensemble des abonnements, groupes d'adiminstration et ressources Azure
[https://learn.microsoft.com/fr-fr/training/modules/azure-architecture-fundamentals/](Le cours complet en ligne)

## Hierarchie d'organisation des niveaux de ressources

.1 **Groupe d'Administration**
Ces groupes vous permettent de gérer l’accès, la stratégie et la conformité de plusieurs abonnements. Tous les abonnements dans un groupe d’administration héritent automatiquement des conditions appliquées à ce groupe d’administration.

.1A- **Abonnements** 
    un abonnement regroupe des comptes d’utilisateur et les ressources qui ont été créées par ces derniers. Pour chaque abonnement, il existe des limites ou des quotas sur la quantité de ressources que vous pouvez créer et utiliser. Les organisations peuvent utiliser des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.

.1A1 **Groupe de ressources**
        les ressources sont combinées en groupes de ressources. Les groupes de ressources agissent comme un conteneur logique dans lequel des ressources Azure comme des applications web, des bases de données et des comptes de stockage sont déployées et gérées.

.1A1a **Ressources**
            les ressources sont des instances de services que vous créez, comme des machines virtuelles, du stockage ou des bases de données SQL.

## Regions Azure, zones de disponibilité et paires de régions

### Régions Azure

Une région est une zone géographique qui contient au moins un centre de données, voire plusieurs centres de données proches les uns des autres et reliés par un réseau à faible latence. Azure assigne et contrôle intelligemment les ressources au sein de chaque région pour que les charges de travail soient correctement équilibrées.

**Certains services ou fonctionnalités des machines virtuelles ne sont disponibles que dans certaines régions, par exemple des tailles de machines virtuelles ou des types de stockage spécifiques. De même, certains services Azure mondiaux ne vous obligent pas à sélectionner une région particulière, comme c’est le cas d’Azure Active Directory, d’Azure Traffic Manager et d’Azure DNS.**

#### Pourquoi les régions sont-elles importantes?

Azure couvre plus de régions que tout autre fournisseur de cloud. Ces régions vous permettent de rapprocher facilement les applications de vos utilisateurs, où qu’ils soient. Les régions globales offrent une meilleure scalabilité et une meilleure redondance. Elles préservent également la résidence des données pour vos services.

***Régions Azure spéciales**

Lors de la création de vos applications, vous pouvez utiliser certaines régions Azure spécialisées pour répondre à vos besoins de conformité ou de réglementation.
Les régions sont celles que vous utilisez pour identifier la localisation de vos ressources. Il existe deux autres termes que vous devez également connaître : zones géographiques et zones de disponibilité.

### Zone de disponibilité Azure

Vous devez vérifier que vos services et données sont redondants pour protéger vos informations en cas de défaillance. Quand vous hébergez votre infrastructure, la configuration de votre propre redondance nécessite la création d’environnements matériels en double. Azure peut vous aider à rendre votre application hautement disponible via des zones de disponibilité.

#### Qu'est-ce qu'une zone de disponibilité?

Les zones de disponibilité sont des centres de données physiquement séparés au sein d’une région Azure. Chaque zone de disponibilité est composée d’un ou de plusieurs centres de données équipés d’une alimentation, d’un refroidissement et d’un réseau indépendants. Une zone de disponibilité est configurée pour être une limite d’isolation. Si une zone de disponibilité tombe en panne, l’autre continue à fonctionner. Les zones de disponibilité sont connectées via des réseaux en fibre optique privés très rapides.

#### Utiliser des zones de disponibilité dans vos applications

Avec la colocalisation de vos ressources de calcul, de stockage, de mise en réseau et de données dans une zone et en les répliquant dans d’autres zones. Vous pouvez utiliser des zones de disponibilité pour exécuter des applications stratégiques et générer la haute disponibilité dans votre architecture d’applications. N’oubliez pas qu’il peut y avoir un coût lié à la duplication de vos services et au transfert de données entre les zones.

Les zones de disponibilité sont utilisées principalement pour les machines virtuelles, les disques managés, les équilibreurs de charge et les bases de données SQL. Les catégories suivantes de services Azure prennent en charge les zones de disponibilité :

 - **Services zonaux**: vous épinglez la ressource à une zone spécifique (par exemple, des machines virtuelles, des disques managés, des adresses IP).
 - **Services redondants interzones** : la plateforme effectue automatiquement une réplication entre des zones (par exemple, un stockage redondant interzone, SQL Database).
 - **Services non régionaux** : les services sont toujours disponibles à partir de zones géographiques Azure et sont résilients aux pannes à l’échelle de la zone et aux pannes à l’échelle de la région.

 ### Paires de région Azure

 Les zones de disponibilité sont créées à l’aide d’un ou de plusieurs centres de données. Il y a au moins trois zones au sein d’une région. Il est possible qu’un sinistre provoque une panne suffisamment importante pour affecter même deux centres de données, donc Azure crée également des paires de régions.

 #### Qu'est-ce qu'une paire de régions?

 Chaque région Azure est toujours associée à une autre région au sein de la même zone géographique (par exemple, États-Unis, Europe ou Asie) à au moins 480 kilomètres de distance. Cette approche permet la réplication des ressources (telles que le stockage sur machines virtuelles) dans une zone géographique afin de réduire la probabilité d’interruptions dues à des événements catastrophiques. Par exemple, des événements tels que des catastrophes naturelles, des troubles civils, des pannes de courant ou des pannes du réseau physique qui affectent plusieurs zones à la fois. Si une région d’une paire est touchée par une catastrophe naturelle, les services basculent automatiquement vers l’autre région dans la paire de régions.

## Ressources Azure et Azure Ressource Manager

- **Ressource** : Élément gérable disponible dans Azure. Les machines virtuelles, les comptes de stockage, les applications web, les bases de données et les réseaux virtuels sont des exemples de ressources.
- **Groupe de ressources** : Conteneur qui contient les ressources associées d’une solution Azure. Le groupe de ressources comprend des ressources que vous devez gérer ensemble. Vous déterminez quelles sont les ressources qui appartiennent à un groupe de ressources en fonction de ce qui convient le mieux à votre organisation.

### Groupes de ressources Azure

Les groupes de ressources sont un composant fondamental de la plateforme Azure. Un groupe de ressources est un conteneur logique de ressources déployées dans Azure. Ces ressources sont tous les éléments que vous créez dans un abonnement Azure, comme les machines virtuelles, les instances Azure Application Gateway et les instances Azure Cosmos DB. Toutes les ressources doivent se trouver dans un groupe de ressources, toutefois, une ressource ne peut être membre que d’un seul groupe de ressources à la fois. Vous pouvez déplacer de nombreuses ressources d’un groupe de ressources à l’autre, mais certains services présentent des limitations ou exigences spécifiques. Les groupes de ressources ne peuvent pas être imbriqués. Une ressource peut être provisionnée uniquement s’il existe déjà un groupe de ressources dans lequel la placer.

#### Regroupement logique

Les groupes de ressources sont conçus pour vous aider à gérer et organiser vos ressources Azure. En regroupant les ressources selon leur utilisation, leur type ou leur emplacement dans un groupe de ressources, vous organisez et structurez l’ensemble des ressources que vous créez dans Azure. 

#### Cycle de vie

Si vous supprimez un groupe de ressources, toutes les ressources qu’il contient seront également supprimées. L’organisation des ressources par cycle de vie peut être utile dans des environnements hors production, afin de pouvoir faire des tests et supprimer les ressources quand vous avez terminé. L’utilisation de groupes de ressources facilite la suppression en bloc des ressources.

#### Autorisation

Les groupes de ressources constituent également une étendue pour l’application des autorisations de contrôle d’accès en fonction du rôle (RBAC). 

### Azure Resource Manager

Azure Resource Manager est le service de déploiement et de gestion d’Azure. Il fournit une couche de gestion qui vous permet de créer, de mettre à jour et de supprimer des ressources dans votre compte Azure. Vous pouvez utiliser des fonctionnalités de gestion telles que le contrôle d’accès, les verrous et les étiquettes pour sécuriser et organiser vos ressources après le déploiement.

Quand un utilisateur envoie une requête à partir d’un outil, d’une API ou d’un kit SDK Azure, Resource Manager reçoit la requête. Il authentifie et autorise la requête. Resource Manager envoie la requête au service Azure, qui effectue l’action demandée. Comme toutes les demandes sont gérées via la même API, vous voyez des résultats cohérents et des capacités cohérentes dans tous les différents outils.

**Toutes les fonctionnalités qui sont disponibles dans le portail Azure sont également disponibles via PowerShell, Azure CLI, les API REST et les SDK clients. Les fonctionnalités initialement publiées par le biais des API seront représentées dans le portail dans les 180 jours après la publication de la version initiale.**

#### Avantages de l'utilisation de Resource Manager

Avec Resource Manager, vous pouvez :

 - Gérer votre infrastructure à l’aide de modèles déclaratifs plutôt que de scripts Un modèle Resource Manager est un fichier JSON qui définit ce que vous voulez déployer sur Azure.
 - Déployer, gérer et superviser toutes les ressources de votre solution sous forme de groupe, plutôt qu’individuellement
 - Vous pouvez redéployer votre solution tout au long du cycle de vie de développement en ayant l’assurance que vos ressources seront déployées dans un état cohérent.
 - Définir les dépendances entre les ressources pour qu’elles soient déployées dans le bon ordre
 - Appliquez le contrôle d’accès à tous les services, car le contrôle d’accès en fonction du rôle (RBAC) est intégré à la plateforme de gestion.
 - Appliquer des étiquettes aux ressources pour organiser de manière logique toutes les ressources de votre abonnement
 - Clarifiez la facturation de votre organisation en affichant les coûts d’un groupe de ressources qui partagent une même étiquette.

## Abonnements et groupes d'administration Azure

une des premières choses à faire sera de créer au moins un abonnement Azure. Vous l’utiliserez pour créer vos ressources cloud dans Azure.

### Abonnements Azure

L’utilisation d’Azure nécessite un abonnement Azure. Un abonnement vous donne un accès authentifié et autorisé aux produits et services Azure. Il vous permet également de provisionner des ressources. Un abonnement Azure est une unité logique de services Azure qui établit une liaison avec un compte Azure, lequel est une identité dans Azure Active Directory (Azure AD) ou dans un annuaire approuvé par Azure AD.

Un compte peut avoir un ou plusieurs abonnements ayant des modèles de facturation différents et auxquels vous appliquez des stratégies de gestion des accès différentes. Vous pouvez utiliser des abonnements Azure pour définir des limites autour de produits, de services et de ressources Azure. Vous pouvez utiliser deux types de limites d’abonnement :

 - **Limites de facturation** : Ce type d’abonnement détermine la façon dont l’utilisation d’Azure est facturée à un compte Azure. Vous pouvez créer plusieurs abonnements en fonction des conditions de facturation. Azure génère des factures et des rapports de facturation distincts pour chaque abonnement afin que vous puissiez organiser et gérer les coûts.
 - **Limites de contrôle d’accès** : Azure applique des stratégies de gestion des accès au niveau de l’abonnement, ce qui vous permet de créer des abonnements distincts pour les différentes structures organisationnelles. Par exemple, dans une entreprise, vous avez différents services auxquels vous appliquez des stratégies d’abonnement Azure distinctes. Ce modèle de facturation vous permet de gérer et de contrôler l’accès aux ressources créées par les utilisateurs dans différents abonnements.

#### Créer des abonements Azure supplémentaires

Vous avez la possibilité de créer des abonnements supplémentaires pour gérer les ressources ou la facturation selon vos besoins. Par exemple, vous pouvez choisir de créer des abonnements supplémentaires pour une facturation séparée :

 - **Environnements** : dans le cadre de la gestion de vos ressources, vous pouvez choisir de créer plusieurs abonnements afin de configurer des environnements séparés pour le développement et le test, pour des raisons de sécurité ou pour isoler les données conformément à des stratégies de conformité. Cette conception est particulièrement utile, car le contrôle d’accès aux ressources s’effectue au niveau de l’abonnement.

 - **Structures organisationnelles** : vous pouvez créer des abonnements qui reflètent vos différentes structures organisationnelles. Par exemple, vous pouvez limiter l’accès d’une équipe aux ressources peu coûteuses, mais autoriser le service informatique à accéder à l’ensemble des ressources. Cette conception vous permet de gérer et contrôler l’accès aux ressources créées par les utilisateurs dans chaque abonnement.

 - **Facturation** : vous pouvez également créer des abonnements supplémentaires pour vos besoins de facturation. Les coûts sont initialement agrégés au niveau de l’abonnement, mais vous pouvez créer plusieurs abonnements pour gérer et suivre les coûts de la manière qui vous convient le mieux. Par exemple, créez un abonnement dédié à vos charges de travail de production et un autre abonnement réservé à vos charges de travail de développement et de test.

Vous pouvez également avoir besoin d’abonnements supplémentaires pour la raison suivante :

 - **Limites d’abonnement** : les abonnements font l’objet de certaines limites strictes. Par exemple, le nombre maximal de circuits Azure ExpressRoute par abonnement est de 10. Vous devez tenir compte de ces limites quand vous créez des abonnements sur votre compte. Si ces limites ne peuvent pas être respectées dans des scénarios particuliers, vous avez la possibilité de créer des abonnements supplémentaires.

#### Personnaliser la facturation selon vos besoins

Si vous avez plusieurs abonnements, vous pouvez les organiser en postes de facture. Chaque poste de facture est une ligne de facture qui indique les frais facturés pour le mois. Par exemple, il est possible d’avoir une facture unique pour toute votre organisation, mais d’organiser les frais par service, équipe ou projet.

Pour répondre à vos besoins, vous pouvez configurer plusieurs factures au sein du même compte de facturation en créant des profils de facturation supplémentaires. Chaque profil de facturation a une facture mensuelle et un mode de paiement qui lui sont associés.

### Groupes d'administration Azure

Si votre organisation a un grand nombre d’abonnements, vous pouvez avoir besoin d’un moyen de gérer efficacement l’accès, les stratégies et la conformité de ces abonnements. Les groupes d’administration Azure offrent un niveau d’étendue au-dessus des abonnements. Vous organisez les abonnements en conteneurs appelés groupes d’administration et vous appliquez vos conditions de gouvernance aux groupes d’administration. Tous les abonnements d’un groupe d’administration héritent automatiquement des conditions appliquées à ce groupe d’administration. Les groupes d’administration vous permettent une gestion de qualité professionnelle à grande échelle, quel que soit le type de vos abonnements. Tous les abonnements d’un même groupe d’administration doivent approuver le même locataire Azure AD.

Par exemple, vous pouvez appliquer des stratégies à un groupe d’administration qui limite le nombre de régions disponibles pour la création des machines virtuelles. Une telle stratégie s’appliquerait alors à tous les groupes d’administration, abonnements et ressources sous ce groupe d’administration en autorisant uniquement la création de machines virtuelles dans une région donnée.

#### Hiérarchie des groupes d'administration et des abonnements

Vous pouvez créer une structure flexible de groupes d’administration et d’abonnements pour organiser vos ressources dans une hiérarchie à des fins de stratégie unifiée et de gestion de l’accès. 

#### Faits importants sur les groupes d'administration

 - 10 000 groupes d’administration peuvent être pris en charge dans un seul annuaire.
 - Une arborescence de groupes d’administration peut prendre en charge jusqu’à six niveaux de profondeur. Cette limite n’inclut pas le niveau Racine ni le niveau de l’abonnement.
 - Chaque groupe d’administration et chaque abonnement ne peut avoir qu’un seul parent.
 - Chaque groupe d’administration peut avoir de nombreux enfants.
 - Dans chaque annuaire, tous les abonnements et groupes d’administration sont dans une même hiérarchie.