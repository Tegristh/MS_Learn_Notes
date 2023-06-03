# Sécuriser l'accès à vos applications à l'aide des services d'identité Azure

[https://learn.microsoft.com/fr-fr/training/modules/secure-access-azure-identity-services/](Cours complet Microsoft)

## Enjeux: 

Par le passé, la protection de l’accès aux systèmes et aux données reposait sur le périmètre du réseau local et des contrôles d’accès physiques.

Face au développement du télétravail, ainsi que l’essor des stratégies de “bring your own device” (BYOD), des applications mobiles et des applications cloud, une grande proportion de ces points d’accès se trouvent désormais en dehors des réseaux physiques de l’entreprise.

L’identité est devenue la nouvelle limite de sécurité primordiale. Prouver avec précision qu’une personne est un utilisateur légitime de votre système, avec un niveau d’accès approprié, est essentiel pour maintenir le contrôle de vos données. Cette couche d’identité est désormais plus souvent la cible d’attaques que le réseau.

## Authentification (AuthN) Vs Autorisation(AuthZ)

L’**authentification** est le processus qui consiste à établir l’identité d’un utilisateur ou d’un service voulant accéder à une ressource. Le fait de demander à une partie des informations d’identification légitimes fait partie de ce processus qui jette les bases de la création d’un principal de sécurité à des fins de contrôle d’identité et d’accès. Elle permet de déterminer si l’utilisateur est bien la personne qu’il prétend être.


L’**autorisation** est le processus qui permet de déterminer quel niveau d’accès une personne ou un service authentifié peut avoir. Elle spécifie les données auxquelles ils sont autorisés à accéder et ce qu’ils peuvent en faire.
