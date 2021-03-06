---
title: 'Tutorial: Get started analyze data with a serverless SQL pool' 
description: In this tutorial, you'll learn how to analyze data with a serverless SQL pool using data located in Spark databases.
services: synapse-analytics
author: saveenr
ms.author: saveenr
manager: julieMSFT
ms.reviewer: jrasnick
ms.service: synapse-analytics
ms.subservice: sql
ms.topic: tutorial
ms.date: 12/31/2020
---

# Analyze data with a serverless SQL pool

In this tutorial, you'll learn how to analyze data with serverless SQL pool using data located in Spark databases. 

## The Built-in serverless SQL pool

Every workspace comes with a pre-built serverless SQL pool called **Built-in**. This pool can't be deleted. Serverless SQL pools let you use SQL without having to reserve capacity with dedicated SQL pools. Unlike the dedicated SQL pools, billing for a serverless SQL pool is based on the amount of data scanned to run the query, not the number of capacity allocated to the pool.

## Analyze NYC Taxi data in blob storage using serverless SQL pool

1. In Synapse Studio go to the **Develop** hub
2. Create a new SQL script.
4. Paste the following code into the script.

    ```
    SELECT
        TOP 100 *
    FROM
        OPENROWSET(
            BULK     'https://azureopendatastorage.blob.core.windows.net/nyctlc/yellow/puYear=*/puMonth=*/*.parquet',
            FORMAT = 'parquet'
        ) AS [result];
    ```
1. Click **Run**

## Next steps

> [!div class="nextstepaction"]
> [Analyze data with a serverless Spark pool](get-started-analyze-spark.md)
