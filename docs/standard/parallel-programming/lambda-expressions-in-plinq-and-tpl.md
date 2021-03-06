---
title: "PLINQ および TPL のラムダ式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79ab0f4427e0f37259f88cd3ec0762d1582481f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ および TPL のラムダ式
タスク並列ライブラリ (TPL) を含む多くの方法のいずれかを<xref:System.Func%601?displayProperty=nameWithType>または<xref:System.Action?displayProperty=nameWithType>入力パラメーターとしてデリゲートのファミリです。 これらのデリゲートを使用して、並列ループ、タスク、またはクエリにカスタムのプログラム ロジックを渡します。 TPL と PLINQ のコード例では、ラムダ式を使用して、インライン コード ブロックとしてこれらのデリゲートのインスタンスを作成します。 このトピックでは、Func および Action について簡単に紹介し、タスク並列ライブラリと PLINQ でラムダ式を使用する方法を示します。  
  
 **メモ** 一般的なデリゲートの詳細については、「[デリゲート](../../csharp/programming-guide/delegates/index.md)」と「[デリゲート](../../visual-basic/programming-guide/language-features/delegates/index.md)」を参照してください。 C# と [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] のラムダ式の詳細については、それぞれ「[ラムダ式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」と「[ラムダ式](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
## <a name="func-delegate"></a>Func デリゲート  
 `Func` デリゲートは、値を返すメソッドをカプセル化します。 Func シグネチャでは、末尾または最も右の型パラメーターが常に戻り値の型を指定します。 コンパイラ エラーの一般的な原因の 1 つは、2 つの入力パラメーターに渡すしようとする、<xref:System.Func%602?displayProperty=nameWithType>以外の場合は実際にはこの型では 1 つの入力パラメーターだけです。 Framework クラス ライブラリの 17 バージョンを定義して`Func`: <xref:System.Func%601?displayProperty=nameWithType>、 <xref:System.Func%602?displayProperty=nameWithType>、 <xref:System.Func%603?displayProperty=nameWithType>、最大などを介して<xref:System.Func%6017?displayProperty=nameWithType>です。  
  
## <a name="action-delegate"></a>Action デリゲート  
 A<xref:System.Action?displayProperty=nameWithType>デリゲート メソッドをカプセル化 (でサブ[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) を返しますまたは、値を返さない[void](~/docs/csharp/language-reference/keywords/void.md)です。 Action 型シグネチャでは、型パラメーターは、入力パラメーターのみを表します。 Func のように、Framework クラス ライブラリでは、型パラメーターを持たないバージョンから 16 の型パラメーターを持つバージョンまでの、17 バージョンの Action が定義されています。  
  
## <a name="example"></a>例  
 次の例、<xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType>メソッドは、ラムダ式を使用して Func および Action の両方のデリゲートを表現する方法を示しています。  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>関連項目  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)
