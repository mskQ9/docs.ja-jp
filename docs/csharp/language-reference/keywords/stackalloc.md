---
title: "stackalloc (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# リファレンス)
`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>コメント  
 このキーワードは、ローカル変数初期化子でのみ有効です。 次のコードはコンパイル エラーになります。  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 ポインター型が使用されるため、`stackalloc` には [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要です。 詳細については、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。  
  
 `stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。  
  
 次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。 それぞれの数値が、前の 2 つの数値の和になっています。 このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、 そのブロックのアドレスは `fib` ポインターに格納されます。 このメモリは、ガベージ コレクションの対象にはならないため、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) を使用して固定する必要はありません。 メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。 メソッドから制御が戻る前に、メモリを解放することはできません。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>セキュリティ  
 アンセーフ コードは、セーフ コードほど安全ではありません。 ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。 バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
