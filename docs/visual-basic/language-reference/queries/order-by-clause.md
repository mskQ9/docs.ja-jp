---
title: "Order By 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ee21942b966668a67b14aba72b8f9fc5ee903c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-clause-visual-basic"></a>Order By 句 (Visual Basic)
クエリ結果の並べ替え順序を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>指定項目  
 `orderExp1`  
 必須です。 1 つまたは複数のフィールド現在のクエリ結果からを返される値を順序付ける方法を示すです。 フィールド名は、コンマ (,) で区切る必要があります。 昇順または降順に並べ替えを使用して、ソート済みとして、各フィールドを識別することができます、`Ascending`または`Descending`キーワード。 ない場合は`Ascending`または`Descending`キーワードを指定すると、既定の並べ替え順序は昇順です。 並べ替え順序フィールドには、左から右への優先順位が与えられます。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Order By`句、クエリの結果の並べ替えにします。 `Order By`句では、現在のスコープの範囲変数に基づく結果を並べ替えることができますのみです。 たとえば、`Select`句にそのスコープに対する新しい反復変数によりクエリ式で、新しいスコープが導入されています。 範囲変数の前に定義されている、`Select`後に使用できるクエリの句は、`Select`句。 したがってでは使用できませんのフィールドで、結果の並べ替えをする場合、`Select`句を付ける必要があります、`Order By`句の前に、`Select`句。 1 つはしなければならない場合の例は、結果の一部として返されないフィールドで、クエリの並べ替えを行うときにします。  
  
 昇順と降順の実装によって、フィールドを特定の順序、<xref:System.IComparable>フィールドのデータ型のインターフェイスです。 データ型を実装しない場合、<xref:System.IComparable>インターフェイス、並べ替え順序は無視されます。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`book`の`books`コレクション。 `Order By`句が昇順 (既定) に価格を指定して、クエリの結果を並べ替えます。 書籍の価格が同じ順序の昇順のタイトルに基づいて並べ替えられます。 `Select`句を選択、`Title`と`Price`プロパティとして、クエリによって返される値。  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`Order By`価格の降順でクエリ結果を並べ替えるための句。 書籍の価格が同じ順序の昇順のタイトルに基づいて並べ替えられます。  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`Select`書籍のタイトルを選択して、価格、発行日、および作成する句。 設定し、 `Title`、 `Price`、 `PublishDate`、および`Author`新しいスコープの範囲変数のフィールドです。 `Order By`句の作成者名、ブック タイトル、および price によって新しい範囲変数の順序。 各列は、既定の順序 (昇順) で並べ替えられます。  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
