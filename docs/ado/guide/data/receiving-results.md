---
title: Réception des résultats | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b861553e9a71ce56377f8d87bba0f9e26e929c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924525"
---
# <a name="receiving-results"></a>Réception de résultats
Dans ADO la plupart des commandes entraîner certaines informations retournées à l’appelant. Pour retourner l’ensemble de lignes de commandes, les résultats sont reçus dans un **Recordset** objet, qui est probablement la plus utilisée des objets ADO.  
  
 Il existe plusieurs façons de recevoir des données dans un **Recordset** objet à partir d’une source de données, y compris l’appel de ce qui suit :  
  
-   [Connection.Execute (méthode)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Méthode Command.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset.Open (méthode)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Recevoir des données dans un **Recordset** objet conclut le processus de récupération de données, avec la participation d’un **connexion** objet et un **commande** de l’objet, implicitement ou explicitement. Dans un système d’application client/serveur typique, l’ensemble du processus d’obtention de données requiert un aller-retour sur le réseau pour chaque rempli **Recordset**.  
  
 Pour recevoir plusieurs jeux de résultats signifie que vous devez effectuer plusieurs allers-retours sur le réseau, une pour chaque jeu de données encapsulée dans un **Recordset** objet. Pour les réseaux lents ou encombrés, ce qui réduit le nombre d’allers-retours peut-être aider à améliorer les performances de l’application. Par conséquent, certains fournisseurs offrent un support pour la réception de plusieurs **Recordset**s dans un seul aller-retour. Ce sujet est abordé dans la rubrique suivante :  
  
-   [Réception de plusieurs recordsets](../../../ado/guide/data/receiving-multiple-recordsets.md)
