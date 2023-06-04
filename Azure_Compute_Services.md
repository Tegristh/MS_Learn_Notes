# Découvrir Azure Compute Services

[cour complet site de microsoft](https://learn.microsoft.com/fr-fr/training/modules/azure-compute-fundamentals/)


## Vue d'ensemble d'Azure Compute Services

### Machines Virtuelles

Les machines virtuelles sont des émulations logicielles d’ordinateurs physiques. Elles incluent un processeur virtuel, une mémoire, un stockage et des ressources réseau. VM hébergent un système d’exploitation et vous pouvez installer et exécuter des logiciels comme sur un ordinateur physique. Lors de l’utilisation d’un client de bureau à distance, vous pouvez utiliser et contrôler la machine virtuelle comme si vous étiez assis devant.

### Groupes de machines virtuelles identiques

Au fur et à mesure que la demande augmente, plus d’instances de machines virtuelles peuvent être ajoutées. Quand la demande baisse, des instances de machine virtuelle peuvent être supprimées. Le processus peut être manuel, automatisé ou une combinaison des deux.

## Conteneurs et Kubernetes

 Les conteneurs sont des environnements applicatifs légers et virtualisés. Ils sont conçus pour être rapidement créés, mis à l’échelle et arrêtés dynamiquement. Vous pouvez exécuter plusieurs instances d’une application conteneurisée sur une seule machine hôte.

## App Service

Vous pouvez rapidement créer, déployer et mettre à l’échelle des applications API, web et mobiles d’entreprise s’exécutant sur n’importe quelle plateforme. Vous pouvez répondre à des exigences strictes aux niveaux des performances, de la scalabilité, de la sécurité et la conformité tout en utilisant une plateforme complètement managée pour effectuer la maintenance de l’infrastructure. App Service est une offre PaaS (Platform as a Service).

## Fonctions

Les fonctions sont idéales lorsque vous êtes uniquement préoccupé par le code exécutant votre service et non par la plateforme ou l’infrastructure sous-jacente. Cette solution est couramment utilisée quand vous avez besoin d’effectuer un travail en réponse à un événement (souvent via une requête REST), un minuteur ou un message d’un autre service Azure, et que ce travail peut être effectué rapidement, en quelques secondes ou moins.