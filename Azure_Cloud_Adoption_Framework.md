# Framework d’adoption du cloud Microsoft pour Azure

[https://learn.microsoft.com/fr-fr/training/modules/microsoft-cloud-adoption-framework-for-azure/](Lien vers le cours complet Microsoft)


## Qu'y a-t-il dans le Cloud Adoption Framework?

Le Cloud Adoption Framework comprend les étapes suivantes :

#### .1 définir votre stratégie:

Ici, vous répondez à la question de savoir pourquoi vous migrez vers le cloud et ce que vous voulez obtenir de la migration vers le cloud. Avez-vous besoin d’évoluer pour satisfaire à la demande ou d’atteindre de nouveaux marchés ? Cela va-t-il réduire les coûts ou augmenter l’agilité de l’entreprise ? Lorsque vous définissez votre stratégie d’adoption du cloud, vous devez comprendre le modèle économique du cloud et tenir compte de l’impact sur l’activité, des délais de traitement, de la portée mondiale, des performances, etc.

- **Définir et décrire vos motivations** : Rencontrer les parties prenantes et les dirigeants peut vous aider à identifier les raisons pour lesquelles vous migrez vers le cloud.

- **Décrire les résultats pour l’entreprise** : Rencontrez les dirigeants des services financiers, marketing, commerciaux et des ressources humaines pour mieux documenter vos objectifs.

- **Évaluez les aspects financiers** : mesurez les objectifs et identifiez le retour attendu d’un investissement spécifique

- **Comprenez les aspects techniques** : évaluez ces aspects techniques via la sélection et la réalisation de votre premier projet technique.

#### .2 établir un plan:

Ici, vous créez un plan qui fait correspondre vos objectifs ambitieux à des actions spécifiques. Un bon plan garantit que vos efforts correspondent aux résultats commerciaux souhaités.

- **Patrimoine numérique** : Créez un inventaire des ressources numériques et charges de travail existantes que vous envisagez de migrer vers le cloud.

- **Alignement initial de l’organisation** : Veillez à ce que les bonnes personnes soient impliquées dans vos efforts de migration, à la fois du point de vue technique et du point de vue de la gouvernance cloud.

- **Plan de préparation des compétences** : Créez un plan qui aide les personnes à acquérir les compétences dont elles ont besoin pour fonctionner dans le cloud.

- **Plan d’adoption du cloud** : Créez un plan complet qui réunit les équipes de développement, d’exploitation et commerciales vers un objectif commun d’adoption du cloud.

#### .3 préparer votre organisation

Ici, vous créez une zone d’atterrissage, c’est-à-dire un environnement dans le cloud pour commencer à héberger vos charges de travail.

- **Guide de configuration Azure** : Passez en revue le guide de configuration Azure pour vous familiariser avec les outils et approches nécessaires lors de la création d’une zone d’atterrissage.

- **Zone d’atterrissage Azure** : Commencez à construire les abonnements Azure qui soutiennent chacun des principaux domaines de votre entreprise. Une zone d’atterrissage comprend une infrastructure cloud ainsi que des fonctionnalités de gouvernance, de comptabilité et de sécurité.

- **Développer la zone d’atterrissage** : Affinez votre zone d’atterrissage pour vérifier qu’elle répond à vos besoins en matière d’opérations, de gouvernance et de sécurité.

- **Bonnes pratiques** : Commencez avec des pratiques recommandées et éprouvées pour veiller à ce que vos efforts de migration vers le cloud soient scalables et maintenables.

#### .4 adopter le cloud 

Ici, vous commencez à migrer vos applications vers le cloud. En cours de route, vous pourriez trouver des moyens de moderniser vos applications et de construire des solutions innovantes qui utilisent des services cloud.

Le Cloud Adoption Framework divise cette phase en deux parties : *migrer* et *innover*.

Migrer:

- **Migrer votre première charge de travail** : Utilisez le guide de migration Azure pour déployer votre premier projet sur le cloud.
- **Scénarios de migration** : Utilisez d’autres guides détaillés pour explorer des scénarios de migration plus complexes.
- **Bonnes pratiques** : Consultez la liste de vérification des bonnes pratiques de migration vers le cloud Azure pour vérifier que vous suivez les pratiques recommandées.
- **Améliorations de processus** : Identifiez des moyens de rendre le processus de migration évolutif tout en nécessitant moins d’efforts.

Innover:

- **Consensus sur la valeur métier** : Vérifiez que les investissements dans de nouvelles innovations créent de la valeur ajoutée pour l’entreprise et répondent aux besoins des clients.
- **Guide d’innovation Azure** : Utilisez ce guide pour accélérer le développement et créer un produit minimum viable pour votre idée.
- **Bonnes pratiques** : Vérifiez que votre progression est conforme aux pratiques recommandées avant de continuer.
- **Boucles de commentaires** : Vérifiez souvent auprès de vos clients que vous créez ce dont ils ont besoin.

#### .5 gouverner et gérer vos environnements cloud

Ici, vous commencez à former vos stratégies de gouvernance cloud et de gestion cloud. Les processus de *gouvernance* et les *stratégies cloud* changent au même rythme que le patrimoine cloud. Vous avez besoin de créer des solutions résilientes qui sont optimisées en permanence.

Gouverner:

- **Méthodologie** : Considérez votre solution finale. Définissez ensuite une méthodologie qui vous emmène de manière progressive de vos premiers pas jusqu’à la gouvernance complète du cloud.
- **Benchmark** : Utilisez l’outil de benchmark de la gouvernance pour évaluer votre état actuel et votre état futur afin d’établir une vision de l’application de l’infrastructure.
- **Base de la gouvernance initiale** : Créez un produit minimum viable qui capture les premières étapes de votre plan de gouvernance.
- **Améliorer la base de la gouvernance initiale** : Ajoutez de manière itérative des contrôles de gouvernance qui traitent des risques tangibles à mesure que vous progressez vers votre solution à l’état final.

Gerer:

- **Établir une base de référence de gestion** : Définissez votre engagement minimal envers la gestion des opérations. Une base de référence de gestion est l’ensemble minimal d’outils et de processus qui doit être appliqué à chaque ressource d’un environnement.
- **Définir des engagements métier** : Documentez les charges de travail prises en charge pour établir des engagements opérationnels avec l’entreprise et convenez des investissements de gestion de cloud pour chaque charge de travail.
- **Développer la base de référence de gestion** : Appliquez les bonnes pratiques recommandées pour itérer sur votre base de référence de gestion initiale.
- **Principes avancés de la conception et des opérations** : Pour les charges de travail qui nécessitent un niveau d'engagement commercial plus élevé, effectuez un examen plus approfondi de l’architecture pour respecter vos engagements en matière de résilience et de fiabilité.

## Créer une stratégie de gouvernance des abonnements

Au début de toute implémentation de gouvernance cloud, vous identifiez une structure d’organisation cloud répondant à vos besoins métier. Les équipes commencent souvent leur stratégie de gouvernance Azure au niveau de l’abonnement. Trois principaux aspects sont à prendre en considération pour créer et gérer des abonnements :

### .1 Facturation.

Vous pouvez créer un seul rapport de facturation par abonnement. Si vous avez plusieurs services et que vous devez effectuer une « rétrofacturation » des coûts cloud, une solution possible consiste à organiser les abonnements par service ou par projet.

### .2 Contrôle d'accès

Quand vous concevez l’architecture de votre abonnement, tenez compte du facteur de limite de déploiement. Par exemple, avez-vous besoin d’abonnements distincts pour les environnements de développement et de production ? Des abonnements distincts vous permettent de contrôler l’accès à chacun d’eux séparément, et donc d’isoler leurs ressources les unes des autres.

### .3 Limites d'abonnement

Les abonnements ont aussi des limitations de ressources. Par exemple, le nombre maximal de circuits Azure ExpressRoute du réseau par abonnement est de 10. Ces limites doivent être prises en compte lors de la phase de conception. Si vous devez dépasser ces limites, vous devrez peut-être ajouter plus d’abonnements. Si vous atteignez une limite maximale, il n’y a aucune flexibilité pour l’augmenter.