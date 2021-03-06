---
title: "Windows フォーム コントロールのマルチスレッド処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows フォーム コントロールのマルチスレッド処理
多くのアプリケーションで行うことができます、ユーザー インターフェイス (UI) 応答性の高い別のスレッドで時間のかかる操作を実行することによってです。 多数のツールが使用できるマルチ スレッド処理など、Windows フォーム コントロールを<xref:System.Threading>名前空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッド、および`BackgroundWorker`コンポーネントです。  
  
> [!NOTE]
>  `BackgroundWorker`コンポーネントの置換し、する機能を追加、<xref:System.Threading>名前空間および<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッドです。 ただし、これらは保持されます両方の下位互換性と将来の使用を選択した場合。 詳細については、次を参照してください。 [BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: Windows フォーム コントロールのスレッド セーフな呼び出しを行う](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows フォーム コントロールにスレッド セーフな呼び出しを行う方法を示します。  
  
 [方法: バックグラウンド スレッドを使用してファイルを検索する](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 使用する方法を示します、<xref:System.Threading>名前空間および<xref:System.Windows.Forms.Control.BeginInvoke%2A>メソッドを非同期的にファイルを検索します。  
  
## <a name="reference"></a>参照  
 <xref:System.ComponentModel.BackgroundWorker>  
 非同期操作のワーカー スレッドをカプセル化するコンポーネントについて説明します。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 サウンドを非同期的に読み込む方法について説明します。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 イメージを非同期的に読み込む方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 時間のかかる操作を行う方法を示しています、<xref:System.ComponentModel.BackgroundWorker>コンポーネントです。  
  
 [BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 使用する方法について説明するトピックを提供、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期操作をします。
