---
title: "Visual Basic における Me、My、MyBase、MyClass"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic における Me、My、MyBase、MyClass
`Me`、 `My`、 `MyBase`、および`MyClass`で[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]似た名前が、さまざまな目的があります。 このトピックでは、これらを区別するためにこれらのエンティティの各を説明します。  
  
## <a name="me"></a>Me  
 `Me`キーワードはクラスまたは構造体の現在のコードが実行されているは、特定のインスタンスを参照する方法を提供します。 `Me`オブジェクト変数または現在のインスタンスを参照する構造体変数のいずれかのように動作します。 使用して`Me`は別のクラス、構造体、またはモジュール内のプロシージャにクラスまたは構造体の現在実行中のインスタンスに関する情報を渡すために特に便利です。  
  
 たとえば、モジュール内に、次の手順があるとします。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 このプロシージャを呼び出すしの現在のインスタンスを渡すことができます、<xref:System.Windows.Forms.Form>次のステートメントを使用して、引数としてのクラスです。  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`機能の数を容易かつ直観的なアクセスを提供する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスを有効にすると、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンピューター、アプリケーション、設定、リソースと対話するユーザー。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`キーワードはクラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。 `MyBase`通常オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーへのアクセスに使用されます。 `MyBase.New`派生クラスのコンス トラクターから基本クラスのコンス トラクターを明示的に呼び出すに使用されます。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`キーワードが最初に実装されたクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass`ような`Me`、上のすべてのメソッド呼び出しとして扱われますはこのメソッドが、`NotOverridable`です。  
  
## <a name="see-also"></a>関連項目  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
