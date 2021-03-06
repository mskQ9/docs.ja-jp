---
title: "Windows フォームにおける自動スケーリング"
ms.date: 06/15/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 519053576aac0f55dfbfa4c87dbed6096f45abca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows フォームにおける自動スケーリング
自動スケーリングによって、特定のディスプレイの解像度またはシステムのフォントを持つマシンに合わせて設計されたフォームとコントロールを、ディスプレイの別の解像度やシステム フォントを持つ別のマシンで適切に表示することができます。 フォームとコントロールが、ユーザーとその他の開発者のマシンのネイティブ ウィンドウとその他のアプリケーションで、一貫性を持つよう適切にサイズ変更され、 自動スケーリングと視覚スタイルに対する [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のサポートにより、各ユーザーのマシンのネイティブの Windows アプリケーションと比較した場合、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アプリケーションが一貫したルック アンド フィールを維持することができます。
  
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 2.0 以降では、ほとんどの場合、自動スケーリングは正常に機能します。 ただし、フォント パターンの変更が問題になる可能性があります。 この問題を解決する方法の例を参照してください[する方法: Windows フォーム アプリケーションでのフォント パターンの変更に応答](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md)です。
  
## <a name="need-for-automatic-scaling"></a>自動スケーリングの必要性  
自動スケーリングがないと、1 つのディスプレイの解像度やフォントのために設計されたアプリケーションは、その解像度やフォントが変更されたときに、表示が小さすぎたり大きすぎたりします。 たとえば、アプリケーションが基準として Tahoma の 9 ポイントを使用して設計されている場合、調整なしでは、システム フォントが Tahoma の 12 ポイントのマシンで実行すると、表示が小さすぎます。 タイトル、メニュー、テキスト ボックスの内容などのテキストの要素は、他のアプリケーションより小さく表示されます。 さらに、タイトル バー、メニューや、多数のコントロールのテキストを含むユーザー インターフェイス (UI) 要素のサイズは、使用されるフォントに依存します。 この例では、これらの要素は比較的小さく表示されます。

類似する状況は、アプリケーションがディスプレイの特定の解像度のために設計されている場合にも発生します。 最も一般的なディスプレイの解像度が 96 ドット/インチ (DPI)、100% ディスプレイのスケーリングと等しい、これが 125%、150%、200% をサポートする高い解像度表示 (どのそれぞれ等しい 120、144 と 192 DPI) 上記のようになっていますより一般的です。 調整なしだと、特にグラフィックスに基づくアプリケーションで、ある解像度のために設計されたものが、別の解像度で実行したときに、表示が大きすぎたり小さすぎたりします。

自動スケーリングは、相対的なフォント サイズやディスプレイ解像度に従ってフォームと子コントロールを自動でサイズ変更することで、これらの問題を改善しようとしています。 Windows オペレーティング システムは、ダイアログ単位と呼ばれるは、相対的な測定単位を使用して、ダイアログ ボックスの自動スケーリングをサポートします。 ダイアログ単位は、システム フォントに基づいており、ピクセルとの関係は、Win32 SDK 関数 `GetDialogBaseUnits` によって決定できます。 ユーザーが Windows によって使用されるテーマを変更すると、すべてのダイアログ ボックスがそれに合わせて自動的に調整されます。 さらに、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]のいずれか、既定のシステム フォントまたはディスプレイの解像度に応じて、自動スケーリングをサポートします。 必要に応じて、アプリケーションで自動スケーリングを無効化できます。

## <a name="original-support-for-automatic-scaling"></a>自動スケーリングの元のサポート
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のバージョン 1.0 および 1.1 は、Windows の UI に使用される (Win32 SDK 値 **DEFAULT_GUI_FONT** で表す) 既定のフォントに依存した、簡単な方法で自動スケーリングをサポートしていました。 このフォントは、通常、ディスプレイの解像度が変更されたときにのみ変更されました。 自動スケーリングを実装するために、次のメカニズムが使用されていました。

1. デザイン時は、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> プロパティ (これは現在推奨されていません) が、開発者のマシンの既定のシステム フォントの高さと幅に設定されていました。

2. 実行時は、ユーザーのマシンの既定のシステム フォントが <xref:System.Windows.Forms.Form> クラスの <xref:System.Windows.Forms.Control.Font%2A> プロパティを初期化するために使用されていました。

3. フォームを表示する前に、フォームのスケーリングのため、<xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> メソッドが呼び出されました。 このメソッドは、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> と <xref:System.Windows.Forms.Control.Font%2A> から相対スケール サイズを計算し、<xref:System.Windows.Forms.Control.Scale%2A> メソッドを呼び出してフォームとその子を実際にスケーリングしました。

4. <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> への後続の呼び出しがフォームを段階的にサイズ変更することがないよう、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> の値が更新されました。

このメカニズムは、ほとんどの目的では十分ですが、次の制限がありました。

- 以降、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>プロパティでは、ベースラインのフォント サイズを表す整数値として、丸め誤差が発生するフォームが複数の解像度を循環した場合に顕著に表れることです。

- 自動スケーリングは <xref:System.Windows.Forms.Form> クラスでのみ実装されており、<xref:System.Windows.Forms.ContainerControl> クラスでは実装されていませんでした。 その結果、ユーザー コントロールは、それがフォームと同じ解像度で設計されていて、かつデザイン時にそのユーザー コントロールがそのフォームに配置された場合にのみ、正しくスケーリングされるということになっていました。

- フォームとその子コントロールの設計作業を複数の開発者によって並行して進めることができたのは、マシンの解像度が同じ場合に限られていました。 同じように、フォームの継承は、親フォームに関連付けられている解像度に依存していました。

> [!NOTE]
> ディスプレイ Dpi、特に最新の 2-1 のデバイスでの極端な相違点とこれ可能性があります、.NET Framework と Visual Studio の最新のバージョンとします。 異なる DPI ディスプレイを使用して、チームでこの問題に対処をすることを確認してクトリ常には、DPI 対応でないモードでを起動して Windows フォーム デザイナーは、常に 96 DPI のレイアウトの計算のベースします。 このため、単に Visual Studio の HighDPI 認識を無効にするのには、次のレジストリ キーを設定します。
>
> ```
> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe]
> "dpiAwareness"=dword:00000000
> ```

- <xref:System.Windows.Forms.FlowLayoutPanel> や <xref:System.Windows.Forms.TableLayoutPanel> など、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 2.0 で導入された新しいレイアウト マネージャーと互換性がありません。

- [!INCLUDE[compact](../../../includes/compact-md.md)] への互換性に必要なディスプレイの解像度に直接基づくスケーリングをサポートしていませんでした。

このメカニズムは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 2.0 で後方互換性のために保持されますが、次に説明するより堅牢なスケーリング メカニズムによって置き換えられました。 その結果、<xref:System.Windows.Forms.Form.AutoScale%2A>、<xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>、および特定の <xref:System.Windows.Forms.Control.Scale%2A> のオーバーロードは廃止マークが付けられています。

> [!NOTE]
> 従来のコードを [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 2.0 にアップグレードする際、これらのメンバーへの参照を削除して問題ありません。

## <a name="current-support-for-automatic-scaling"></a>自動スケーリングの現在のサポート
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 2.0 は、Windows フォームの自動規スケーリングに次の変更を導入することで、以前の制限を解消しています。

- スケーリングの基本サポートは <xref:System.Windows.Forms.ContainerControl> クラスに移動し、フォーム、ネイティブの複合コントロールおよびユーザー コントロールは、すべて統一されたスケーリングのサポートを受け取ります。 新しいメンバー <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>、および <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> が追加されました。

- <xref:System.Windows.Forms.Control> クラスにも、スケーリングに参加して同じフォームでのスケーリングの混在をサポートできる新しいメンバーがいくつかあります。 具体的には、<xref:System.Windows.Forms.Control.Scale%2A>、<xref:System.Windows.Forms.Control.ScaleChildren%2A>、および <xref:System.Windows.Forms.Control.GetScaledBounds%2A> メンバーが、スケーリングをサポートします。

- 画面の解像度に基づくスケーリングのサポートが追加され、<xref:System.Windows.Forms.AutoScaleMode> の列挙型により定義されるように、システム フォントのサポートを補完します。 このモードは、アプリケーションの移行を容易にする [!INCLUDE[compact](../../../includes/compact-md.md)] によりサポートされる、自動スケーリングと互換性があります。

- <xref:System.Windows.Forms.FlowLayoutPanel> や <xref:System.Windows.Forms.TableLayoutPanel> などのレイアウト マネージャーの互換性が、自動スケーリングの実装に追加されています。

- スケール ファクターが、通常は <xref:System.Drawing.SizeF> 構造を使用する浮動小数点値として表され、エラーの丸めが事実上解決されています。

> [!CAUTION]
> DPI とフォントのスケーリング モードの任意の混在はサポートされません。 1 つのモード (DPI など) を使用してユーザー コントロールのスケールを調整し、別のモード (フォント) を使用してフォームに配置して問題が発生しない場合でも、基底フォームはあるモード、派生フォームは別のモードというように混在させると、予期しない結果が発生することがあります。

### <a name="automatic-scaling-in-action"></a>自動スケーリングの動作
Windows フォームは、次のロジックを使用して、フォームとそのコンテンツを自動的にスケール調整します。

1. デザイン時に、各 <xref:System.Windows.Forms.ContainerControl> は <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> と <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> にそれぞれスケーリング モードと現在の解像度を記録します。

2. 実行時に、実際の解像度は <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> プロパティに格納されます。 <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> プロパティは、実行時と設計時のスケーリング解像度の比率を動的に計算します。

3. フォームが読み込まれたときに、<xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> と <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> の値が異なる場合は、<xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> メソッドが呼び出されてコントロールと子のスケールを調整します。 このメソッドはレイアウトを中断し、<xref:System.Windows.Forms.Control.Scale%2A> メソッドを呼び出して実際のスケーリングを実行します。 その後、<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> の値がプログレッシブ スケーリングを避けるために更新されます。

4. また、<xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> は次のような状況でも自動的に呼び出されます。

    - スケーリング モードが <xref:System.Windows.Forms.AutoScaleMode.Font> の場合の <xref:System.Windows.Forms.Control.OnFontChanged%2A> イベントへの応答。
  
    - コンテナー コントロールのレイアウトが再開され、<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> プロパティまたは <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> プロパティで変更が検出されたとき。
  
    - 上記に示すように、親の <xref:System.Windows.Forms.ContainerControl> がスケーリングされたとき。 各コンテナー コントロールは、親コンテナーからのスケーリング ファクターではなく、独自のスケーリング ファクターを使用してその子のスケーリングを担当します。

5. 子コントロールは、いくつかの方法で、そのスケーリングの動作を変更できます。

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> プロパティをオーバーライドして、子コントロールをスケーリングすべきかどうかを決定することができます。

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> メソッドをオーバーライドして、スケーリングのロジックではなく、コントロールがスケーリングされる両機にを調整することができます。

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> メソッドをオーバーライドして、現在のコントロールのスケーリングのロジックを変更することができます。

## <a name="see-also"></a>関連項目
 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>  
 <xref:System.Windows.Forms.Control.Scale%2A>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>  
 [visual スタイルが使用されているコントロールのレンダリング](./controls/rendering-controls-with-visual-styles.md)  
 [方法: 自動スケーリングを解除してパフォーマンスを向上させる](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
