# Découvrir des files d'attente de messages Azure

[cour complet site de microsoft](https://learn.microsoft.com/fr-fr/training/modules/discover-azure-message-queue/)

## Envisager d’utiliser des files d’attente Service Bus

En tant que développeur/architecte de solutions, vous devez envisager d’utiliser les files d’attente Service Bus lorsque :

- Votre solution doit recevoir des messages sans avoir à interroger la file d’attente. Avec Service Bus, vous pouvez y parvenir en utilisant une opération de réception à interrogation longue à l’aide des protocoles TCP pris en charge par Service Bus.

- Votre solution nécessite la file d'attente pour fournir une livraison organisée selon la méthode Premier entré, premier sortie.

- Votre solution doit prendre en charge la détection automatique des doublons.

- Vous voulez que votre application traite les messages sous forme de flux durables parallèles (les messages sont associés à un flux à l’aide de la propriété d’ID de session du message). Dans ce modèle, chaque nœud de l'application consommatrice entre en concurrence pour les flux, contrairement aux messages. Lorsqu'un flux est donné à un nœud consommateur, le nœud peut examiner l'état du flux de l'application à l'aide de transactions.

- Votre solution nécessite un comportement transactionnel et l'atomicité lors de l'envoi ou de la réception de plusieurs messages à partir d'une file d'attente.

- Votre application gère des messages qui peuvent dépasser 64 ko, mais qui n’atteindront sans doute pas la limite des 256 ko.


## Envisager d’utiliser des files d’attente Stockage

En tant que développeur/architecte de solutions, vous devez envisager d’utiliser les files d’attente Azure dans les cas de figure suivants :

- Votre application doit stocker plus de 80 Go de messages dans une file d’attente.

- Votre application veut suivre la progression du traitement d’un message dans la file d’attente. Cela est utile si le Worker qui traite un message ne répond plus. Un autre Worker peut alors utiliser ces informations pour continuer là où le Worker précédent s’était arrêté.

- Vous avez besoin de journaux d’activité côté serveur de toutes les transactions exécutées sur les files d’attente.