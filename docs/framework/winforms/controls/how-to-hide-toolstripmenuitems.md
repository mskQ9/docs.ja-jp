---
title: "方法 : ToolStripMenuItems を非表示にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f5491cfbfc312b2ce3e35170ddc4edc8ee39a61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a>方法 : ToolStripMenuItems を非表示にする
メニュー項目を非表示には、アプリケーションのユーザー インターフェイスを制御し、ユーザーのコマンドを制限する方法です。 多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。 これにより、ユーザーの混乱を避けることが少ないが表示されます。 さらに、ことができますを非表示にして、メニューまたはメニュー項目を無効にするように単独で非表示がショートカット キーを使用して、メニュー コマンドにアクセスできないユーザーを妨げません。  
  
### <a name="to-hide-any-menu-item-programmatically"></a>メニュー項目をプログラムで非表示にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`です。  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [方法: ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
