---
title: "メソッド ベースのクエリ構文例: 変換演算子 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 562c6d0280d016ce63cda89ff048e3790631fa60
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a>メソッド ベースのクエリ構文例: 変換演算子 (LINQ to DataSet)
このトピックでは、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使ってクエリ式を即時実行する例を示しています。  
  
 `FillDataSet`でこれらの例で使用されるメソッドが指定された[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。  
  
 このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。  
  
 このトピックの例では、次を使用して`using` / `Imports`ステートメント。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 詳細については、次を参照してください。[する方法: Visual Studio でデータセット プロジェクトに LINQ 作成](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)です。  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>例  
 この例では、<xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用して、シーケンスを配列として即時評価します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>例  
 この例では、<xref:System.Linq.Enumerable.ToDictionary%2A> メソッドを使用して、シーケンスおよび関連するキー式をディクショナリとして即時評価します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>例  
 この例では、<xref:System.Linq.Enumerable.ToList%2A> メソッドを使用して、シーケンスを <xref:System.Collections.Generic.List%601> として即時評価します。ここで、`T` は <xref:System.Data.DataRow> 型を表します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>参照  
 [DataSet へのデータの読み込み](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
