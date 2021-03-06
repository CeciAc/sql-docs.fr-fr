---
title: 'Tutoriel Python : Préparer des données en cluster'
description: Dans la deuxième partie de cette série de tutoriels qui en compte quatre, vous allez préparer les données à partir d’une base de données SQL Server pour effectuer un clustering en Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 11c24d5403e6540da52ec3557c64e1dc8fa57c78
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727088"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>Tutoriel : Préparer des données pour classer des clients dans Python avec SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans la deuxième partie de cette série de didacticiels en quatre parties, vous allez restaurer et préparer des données à partir d’une base de données SQL à l’aide de Python. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de clustering dans Python avec SQL Server Machine Learning Services.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Séparer des clients en fonction de leurs dimensions à l’aide de Python
> * Charger les données issues de la base de données SQL dans une trame de données Python

Dans la [première partie](python-clustering-model.md), vous avez installé les prérequis et restauré l’exemple de base de données.

Dans la [troisième partie](python-clustering-model-build.md), vous apprendrez à créer et à effectuer l’apprentissage d’un modèle de clustering dans Python.

Dans la [quatrième partie](python-clustering-model-deploy.md), vous allez créer une procédure stockée dans une base de données SQL capable d’effectuer un clustering en Python sur la base des nouvelles données.

## <a name="prerequisites"></a>Conditions préalables requises

* La deuxième partie de ce tutoriel suppose que vous avez rempli les conditions préalables de la [**première partie**](python-clustering-model.md).

## <a name="separate-customers"></a>Séparer des clients

Pour préparer le clustering des clients, vous devez d’abord les séparer selon les dimensions suivantes :

* **orderRatio** = renvoie le taux de commandes (nombre total de commandes partiellement ou entièrement renvoyées par rapport au nombre total de commandes)
* **itemsRatio** = renvoie le taux d’éléments (nombre total d’éléments renvoyés par rapport au nombre d’éléments achetés)
* **monetaryRatio** = renvoie le taux des montants (montant monétaire total des éléments renvoyés par rapport au montant acheté)
* **frequency** = renvoie la fréquence

Ouvrez un nouveau bloc-notes dans Azure Data Studio et entrez le script suivant.

Dans la chaîne de connexion, remplacez les détails de connexion, le cas échéant.

```python
# Load packages.
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import revoscalepy as revoscale
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = 'Driver=SQL Server;Server=localhost;Database=tpcxbb_1gb;Trusted_Connection=True;'

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
FROM
(
  SELECT
    ss_customer_sk,
    -- return order ratio
    COUNT(distinct(ss_ticket_number)) AS orders_count,
    -- return ss_item_sk ratio
    COUNT(ss_item_sk) AS orders_items,
    -- return monetary amount ratio
    SUM( ss_net_paid ) AS orders_money
  FROM store_sales s
  GROUP BY ss_customer_sk
) orders
LEFT OUTER JOIN
(
  SELECT
    sr_customer_sk,
    -- return order ratio
    count(distinct(sr_ticket_number)) as returns_count,
    -- return ss_item_sk ratio
    COUNT(sr_item_sk) as returns_items,
    -- return monetary amount ratio
    SUM( sr_return_amt ) AS returns_money
FROM store_returns
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>Charger les données dans une trame de données

Les résultats de la requête sont renvoyés vers Python à l’aide de la fonction **RxSqlServerData** revoscalepy. Dans le cadre du processus, vous utiliserez les informations de colonne que vous avez définies dans le script précédent.

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

À présent, affichez le début de la trame de données pour vérifier qu’elle semble correcte.

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne poursuivez pas ce tutoriel, supprimez la base de données tpcxbb_1gb de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Dans la deuxième partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Séparer des clients en fonction de leurs dimensions à l’aide de Python
* Charger les données issues de la base de données SQL dans une trame de données Python

Pour effectuer l’apprentissage d’un modèle de Machine Learning qui utilise ces données client, suivez la troisième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel : Créer un modèle prédictif en Python avec SQL Server Machine Learning Services](python-clustering-model-build.md)
