---
title: "既定のサービスの動作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "既定のサービス動作のサンプル [Windows Communication Foundation]"
  - "サービスの動作, 既定"
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# 既定のサービスの動作
このサンプルでは、サービスの動作設定を構成する方法を示します。このサンプルは、`ICalculator` サービス コントラクトを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。このサンプルは、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性と <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、サービスの動作と操作の動作を明示的に定義しています。動作の構成は、このサンプルに示すように、構成ファイルで行うことも、コード内で強制的に行うこともできます。  
  
 この例では、クライアントはコンソール アプリケーション \(.exe\) で、サービスはインターネット インフォメーション サービス \(IIS\) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス クラスは、<xref:System.ServiceModel.ServiceBehaviorAttribute> と <xref:System.ServiceModel.OperationBehaviorAttribute> を使用して動作を指定します。次のサンプル コードを参照してください。指定されたすべての値は、既定値です。  
  
```  
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
  
```  
  
 サービスの動作は、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性で指定されます。これらの動作のいくつかを次の表に示します。  
  
|サービスの動作|説明|  
|-------------|--------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|セッションをクライアントの要求で自動的にシャットダウンします。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|各サービス インスタンスの同時実行モードを指定します。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|インスタンス コンテキスト モードを指定します。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|同期コンテキストが設定されている場合、その同期コンテキストを使用するかどうかを判断します。Windows フォーム アプリケーションで `WindowsFormsSynchronizationContext` を使用するかどうかを制御する場合に、これを使用します。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|一般的な未処理の実行例外を `Fault<string>` に変換してエラー メッセージとして送信するかどうかを判断します。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|トランザクションの分離レベルを指定します。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|予期しないメッセージのヘッダーがエラーの原因であるかどうかを判断します。|  
  
 操作の動作は <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して指定されます。これらの動作のいくつかを次の表に示します。  
  
|操作の動作|説明|  
|-----------|--------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|現在のトランザクションがサービス操作の完了によってコミットされるかどうかを判断します。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|サービス操作がクライアントからフローされたトランザクションに参加するかどうかを判断します。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|サービス操作が呼び出し元の ID を偽装するかどうかを判断します。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|サービス操作の呼び出しの開始時または終了時に、サービス インスタンスが再利用されるかどうかを判断します。|  
  
 このサンプルを実行する場合は、操作要求および応答はクライアントのコンソール ウィンドウに表示されます。呼び出し間の遅延は、サービス操作で `System.Threading.Thread.Sleep()` が呼び出されることによるものです。以降の動作サンプルでは、これらの動作の詳細について説明します。クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## 参照