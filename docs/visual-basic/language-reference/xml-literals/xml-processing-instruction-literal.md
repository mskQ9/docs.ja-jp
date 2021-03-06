---
title: "XML 処理命令リテラル (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 処理命令リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>指定項目  
 `<?`  
 必須です。 XML 処理命令リテラルの開始を示します。  
  
 `piName`  
 必須です。 アプリケーションを示す処理命令のターゲットを名前します。 "Xml"または"XML"で始まることはできません。  
  
 `piData`  
 省略可能です。 アプリケーションの対象とする方法を示す文字列`piName`XML ドキュメントを処理する必要があります。  
  
 `?>`  
 必須です。 処理命令の終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。  
  
## <a name="remarks"></a>コメント  
 XML 処理命令リテラルは、アプリケーションが XML ドキュメントを処理する方法を示しています。 アプリケーションには、XML ドキュメントが読み込まれると、アプリケーションは、XML 処理命令、ドキュメントを処理する方法を決定を確認できます。 アプリケーションの意味を解釈する`piName`と`piData`です。  
  
 XML ドキュメント リテラルは、XML 処理命令に似ていますが構文を使用します。 詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)です。  
  
> [!NOTE]
>  `piName`要素は、XML 1.0 仕様は、これらの id を予約するため、文字列"xml"または"XML"で始めることはできません。  
  
 変数に XML 処理命令リテラルを代入または XML ドキュメント リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字をことがなく複数行にまたがることができます。 これにより、XML ドキュメントの内容をコピーして貼り付けに直接、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プログラムです。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラへの呼び出しにリテラルの XML 処理命令を変換する、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>コンス トラクターです。  
  
## <a name="example"></a>例  
 次の例では、XML ドキュメントのスタイル シートを識別する処理命令を作成します。  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
