---
title: "new 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a>new 演算子 (C# リファレンス)
オブジェクトを作成し、コンストラクターを呼び出すために使用します。 例:  
  
```  
Class1 obj  = new Class1();  
```  
  
 匿名型のインスタンスの作成にも使用します。  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` 演算子は値型の既定コンストラクターの呼び出しにも使用します。 例:  
  
```  
int i = new int();  
```  
  
 上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。 このステートメントは次のステートメントと同じ効果があります。  
  
```  
int i = 0;  
```  
  
 既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
 すべての値型には暗黙的に既定のパブリック コンストラクターがあるため、[構造体](../../../csharp/language-reference/keywords/struct.md) に対して既定のコンストラクターを宣言するとエラーになります。 パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。  
  
 構造体などの値型オブジェクトはスタック領域に作成され、クラスなどの参照型オブジェクトはヒープ領域に作成されます。 どちらの型のオブジェクトも自動的に破棄されますが、値型に基づくオブジェクトがスコープの適用外になると破棄されるのに対し、参照型に基づくオブジェクトは、そのオブジェクトへの最後の参照が削除されたあと、随時破棄されます。 大量のメモリ、ファイル ハンドル、ネットワーク接続などの固定のリソースを消費する参照型の場合、確定的な最終処理を行い、オブジェクトが破棄されたことをできるだけ早く確認することが望ましい場合があります。 詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。  
  
 `new` 演算子はオーバーロードできません。  
  
 `new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。  
  
## <a name="example"></a>例  
 次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。 既定値と代入値が表示されます。  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 この例では、文字列の既定値は `null` です。 このため、文字列の既定値は表示されません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
