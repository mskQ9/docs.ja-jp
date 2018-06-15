---
title: '方法 : 簡単なバインディングを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555020"
---
# <a name="how-to-create-a-simple-binding"></a>方法 : 簡単なバインディングを作成する
この例は、単純な<xref:System.Windows.Data.Binding>を作成する方法を示します。  
  
## <a name="example"></a>例  
 この例では、`PersonName`という名前の文字列プロパティを持つ`Person`オブジェクトが必要です。 `Person`オブジェクトは`SDKSample`という名前空間で定義されています。  
  
 次の例において、`<src>`要素を含む強調表示された行で、値が`Joe`である`PersonName`プロパティを持った`Person`オブジェクトをインスタンス化します。 これは、`Resources`セクションで、`x:Key`に割り当てられます。 
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 強調表示された`<TextBlock>`要素を含む行で、<xref:System.Windows.Controls.TextBlock>コントロールを`PersonName`プロパティにバインドします。 その結果、<xref:System.Windows.Controls.TextBlock>に値"Joe"が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
