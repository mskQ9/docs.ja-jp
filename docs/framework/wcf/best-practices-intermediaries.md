---
title: "ベスト プラクティス: 中継局"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7aecdcecedcee98828b398f9172985d2e09fb9be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-intermediaries"></a>ベスト プラクティス: 中継局
中継局のサービス側のチャネルが適切に閉じられていることを確認するために中継局を呼び出すときは、エラーが正しく処理されるよう注意する必要があります。  
  
 次に例を示します。 クライアントが中継局を呼び出すと、中継局はバックエンド サービスを呼び出します。  バックエンド サービスはエラー コントラクトを定義しないので、そのサービスからスローされるエラーはすべて型指定されていないエラーとして扱われます。  バックエンド サービスからスロー、<xref:System.ApplicationException>され、WCF が正しく、サービス側チャネルを中止します。 <xref:System.ApplicationException> が <xref:System.ServiceModel.FaultException> として中継局にスローされます。 中継局は <xref:System.ApplicationException> を再スローします。 WCF はこれを中継局からの型指定されていないエラーとして解釈し、クライアントに転送します。 エラーを受け取ると、中継局とクライアントのクライアント側チャネルはエラーを示します。 ただし、WCF にはエラーが致命的であることが通知されていないため、中継局のサービス側チャネルは開いたままです。  
  
 このシナリオのベスト プラクティスとしては、次のコード スニペットに示すように、サービスからスローされたエラーが致命的かどうかを検出し、致命的である場合は、中継局のサービス側チャネルでエラーを示します。  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [WCF エラー処理](../../../docs/framework/wcf/wcf-error-handling.md)  
 [コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
