---
title: "関数型構築 (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c68fb71fd59d08574cee9eec933cee25e504d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>関数型構築 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] には、"*関数型構築*" と呼ばれる強力な XML 要素作成機能があります。 関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。  
  
-   <xref:System.Xml.Linq.XElement> コンストラクターは、さまざまな種類のコンテンツ引数を受け取ります。 たとえば、このコンストラクターに、子要素になる別の <xref:System.Xml.Linq.XElement> オブジェクトや、 要素の属性になる <xref:System.Xml.Linq.XAttribute> オブジェクトを渡すことができます。 また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。  
  
-   <xref:System.Xml.Linq.XElement> コンストラクターは、`params` 型の <xref:System.Object> 配列を受け取ります。そのため、任意の数のオブジェクトを配列に渡すことができます。 これにより、複雑なコンテンツを持つ要素を作成できます。  
  
-   オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。 コレクションに <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。 これは重要な機能といえます。その理由は、この機能により、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果をコンストラクターに渡すことができるためです。  
  
 次に例を示します。  
  
 これらの機能を有効にすると、XML リテラルを使用して、XML ツリーを作成しの結果を使用するコードを記述するコードを記述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]XML ツリーを作成するときにクエリを実行します。  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
