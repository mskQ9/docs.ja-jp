---
title: "方法 : グローバル アセンブリ キャッシュの内容を表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e50292d1cbb5f2906f053ffd6e21ca21174e2914
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>方法 : グローバル アセンブリ キャッシュの内容を表示する
[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用すると、グローバル アセンブリ キャッシュの内容を表示できます。  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、次のようにします。  
  
1.  [Visual Studio コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。  
  
     **gacutil -l**   
     - または -  
    **gacutil /l**  
  
 以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。  
  
## <a name="see-also"></a>参照  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
