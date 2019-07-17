---
ms.openlocfilehash: 6cf3dd279f33ea0c157743d4b4c11248267a0a62
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215628"
---
3. Sur tous les nœuds du cluster, ouvrez les ports de pare-feu de Pacemaker. Pour ouvrir ces ports avec `firewalld`, exécutez la commande suivante :

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Si le pare-feu n’a pas une configuration de haute disponibilité intégrée, ouvrez les ports suivants pour Pacemaker.
   >
   > * TCP : Ports 2224, 3121, 21064
   > * UDP : Port 5405

1. Installez les packages Pacemaker sur tous les nœuds.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

2. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur tous les nœuds. 

   ```bash
   sudo passwd hacluster
   ```

3. Pour autoriser les nœuds à rejoindre le cluster après le redémarrage, activez et démarrez le service `pcsd` et Pacemaker. Exécutez la commande suivante sur tous les nœuds.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Créez le cluster. Pour ce faire, exécutez la commande suivante :

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2> <node3> 
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >Si vous avez précédemment configuré un cluster sur les mêmes nœuds, vous devez utiliser l’option `--force` pendant l’exécution de `pcs cluster setup`. Cette option revient à exécuter `pcs cluster destroy`. Pour réactiver Pacemaker, exécutez `sudo systemctl enable pacemaker`.

5. Installez l’agent de ressources SQL Server pour SQL Server. Exécutez les commandes suivantes sur tous les nœuds. 

   ```bash
   sudo yum install mssql-server-ha
   ```
