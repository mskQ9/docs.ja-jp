---
title: "永続性発行済みトークン プロバイダー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# 永続性発行済みトークン プロバイダー
このサンプルでは、カスタム クライアントの発行済みトークン プロバイダーを実装する方法を示します。  
  
## 説明  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のトークン プロバイダーは、資格情報をセキュリティ インフラストラクチャに提供するために使用します。一般的に、トークン プロバイダーは、ターゲットをチェックし、適切な証明書を発行して、セキュリティ インフラストラクチャがメッセージのセキュリティを保護できるようにします。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] にはトークン プロバイダー [!INCLUDE[infocard](../../../../includes/infocard-md.md)] が付属しています。カスタム トークン プロバイダは、次の場合に便利です。  
  
-   組み込みのトークン プロバイダが連係動作できない資格情報ストアがある場合。  
  
-   資格情報をユーザーが詳細を提供した時点から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが資格情報を使用した時点に変換するための、独自のカスタム メカニズムを提供する場合。  
  
-   カスタム トークンを構築している場合。  
  
 このサンプルでは、セキュリティ トークン サービス \(STS\) によって発行されたトークンをキャッシュする、カスタム トークン プロバイダーを構築する方法を示します。  
  
 このサンプルに示されている手順の概要は次のとおりです。  
  
-   クライアントをカスタム トークン プロバイダーを使用して構成する手順。  
  
-   発行済みトークンをキャッシュして [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントに提供する手順。  
  
-   サーバーがクライアントによってサーバーの X.509 証明書を使用して認証される手順。  
  
 このサンプルは、クライアント コンソール プログラム \(Client.exe\)、セキュリティ トークン サービス コンソール プログラム \(Securitytokenservice.exe\)、およびサービス コンソール プログラム \(Service.exe\) で構成されています。サービスは、要求\/応答通信パターンを定義するコントラクトを実装します。このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 \(加算、減算、乗算、および 除算\) を公開しています。クライアントは、セキュリティ トークンをセキュリティ トークン サービス \(STS\) から取得し、指定された算術演算を実行する同期要求をサービスに対して行います。サービスは、結果を添えて応答します。クライアント アクティビティは、コンソール ウィンドウに表示されます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用して ICalculator コントラクトを公開します。このバインディングのクライアント側の構成は、次のコードに示すとおりです。  
  
```  
<bindings>  <wsFederationHttpBinding>    <binding name="ServiceFed" >      <security mode ="Message">        <message issuedKeyType ="SymmetricKey" issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >          <issuer address ="http://localhost:8000/sts/windows" binding ="wsHttpBinding" />        </message>      </security>    </binding>  </wsFederationHttpBinding></bindings>  
```  
  
 `wsFederationHttpBinding` の `security` 要素では、使用するセキュリティ モードは `mode` 値で構成されます。このサンプルでは、メッセージ セキュリティが使用されています。このため、`wsFederationHttpBinding` の `message` 要素が `wsFederationHttpBinding` の `security` 要素の内側で指定されています。`wsFederationHttpBinding` の `message` 要素の内側にある `wsFederationHttpBinding` の `issuer` 要素は、セキュリティ トークンをクライアントに発行するセキュリティ トークン サービスのアドレスとバインディングを指定します。これにより、クライアントが Calculator サービスに認証されるようになります。  
  
 このバインディングのサービス側の構成は、次のコードに示すとおりです。  
  
```  
<bindings>  <wsFederationHttpBinding>    <binding name="ServiceFed" >      <security mode ="Message">        <message issuedKeyType ="SymmetricKey" issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >          <issuerMetadata address ="http://localhost:8000/sts/mex" >            <identity>              <certificateReference storeLocation ="CurrentUser"                                     storeName="TrustedPeople"                                     x509FindType ="FindBySubjectDistinguishedName"                                     findValue ="CN=STS" />            </identity>          </issuerMetadata>        </message>      </security>    </binding>  </wsFederationHttpBinding></bindings>  
```  
  
 `wsFederationHttpBinding` の `security` 要素では、使用するセキュリティ モードは `mode` 値で構成されます。このサンプルでは、メッセージ セキュリティが使用されています。このため、`wsFederationHttpBinding` の `message` 要素が `wsFederationHttpBinding` の `security` 要素の内側で指定されています。`wsFederationHttpBinding` の `message` 要素の内側にある `wsFederationHttpBinding` の `issuerMetadata` 要素は、セキュリティ トークン サービスのメタデータ取得に使用できるエンドポイントのアドレスと ID を指定します。  
  
 このサービスの動作を次のコードに示します。  
  
```  
<behavior name ="ServiceBehavior" >  <serviceDebug includeExceptionDetailInFaults ="true"/>  <serviceMetadata httpGetEnabled ="true"/>  <serviceCredentials>    <issuedTokenAuthentication>      <knownCertificates>        <add storeLocation ="LocalMachine"             storeName="TrustedPeople"             x509FindType="FindBySubjectDistinguishedName"             findValue="CN=STS" />      </knownCertificates>    </issuedTokenAuthentication>    <serviceCertificate storeLocation ="LocalMachine"                        storeName ="My"                        x509FindType ="FindBySubjectDistinguishedName"                        findValue ="CN=localhost"/>  </serviceCredentials></behavior>  
```  
  
 `serviceCredentials` 要素の内側にある `issuedTokenAuthentication` 要素を使用すると、サービスは、認証時にクライアントが提示できるトークンに関する制約を指定できます。この構成の指定では、サブジェクト名が CN\=STS である証明書によって署名されたトークンがサービスによって受け入れられます。  
  
 セキュリティ トークン サービスは、標準の wsHttpBinding を使用して、単一のエンドポイントを公開します。セキュリティ トークン サービスは、クライアントからのトークンの要求に応答し、クライアントが Windows アカウントを使用して認証していることを前提として、クライアントのユーザー名がクレームとして含まれているトークンを発行します。セキュリティ トークン サービスは、トークン作成の一環として、CN\=STS 証明書に関連付けられている秘密キーを使用して、トークンに署名します。また、対称キーを作成し、CN\=localhost 証明書に関連付けられている秘密キーを使用して暗号化します。セキュリティ トークン サービスは、トークンをクライアントに返すときに、対称キーも返します。クライアントは、発行されたトークンを Calculator サービスに提示し、対称キーを使用してメッセージに署名することで対称キーを認識していることを証明します。  
  
## カスタム クライアント資格情報とトークン プロバイダ  
 発行済みトークンをキャッシュするカスタム トークン プロバイダーを開発して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティに統合する方法を、次の手順に示します。  
  
#### カスタム トークン プロバイダーを開発するには  
  
1.  カスタム トークン プロバイダーを作成します。  
  
     サンプルでは、キャッシュから取得したセキュリティ トークンを返すカスタム トークン プロバイダーを実装します。  
  
     このタスクを実行するため、カスタム トークン プロバイダは <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスを派生し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> メソッドをオーバーライドします。このメソッドは、キャッシュ内のトークンの取得を試行します。キャッシュ内にトークンが見つからない場合は、基になるプロバイダからトークンを取得してキャッシュします。どちらの場合も、メソッドは `SecurityToken` を返します。  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2.  カスタム セキュリティ トークン マネージャーを作成します。  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> は、`CreateSecurityTokenProvider` メソッド内で渡される特定の <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> の <xref:System.IdentityModel.Selectors.SecurityTokenProvider> の作成に使用されます。セキュリティ トークン マネージャーは、トークン認証システムとトークン シリアライザーの作成にも使用されますが、このサンプルでは扱っていません。このサンプルでは、カスタム セキュリティ トークン マネージャーは <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承し、`CreateSecurityTokenProvider` メソッドをオーバーライドして、渡されたトークンの要件で発行済みトークンが必要であることが示されている場合にはカスタム トークン プロバイダーを返します。  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3.  カスタム クライアント資格情報を作成します。  
  
     クライアント資格情報クラスは、クライアント プロキシ用に構成された資格情報を表すために使用され、トークン認証システム、トークン プロバイダ、およびトークン シリアライザの取得に使用されるセキュリティ トークン マネージャを作成します。  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4.  トークン キャッシュを実装します。サンプルの実装では抽象基本クラスを使用し、トークン キャッシュの利用先ではこのクラスを通じてキャッシュとやり取りします。  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     クライアントがカスタム クライアント資格情報を使用するため、サンプルでは既定のクライアント資格情報を削除し、新しいクライアント資格情報クラスを提供しています。  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## サンプルの実行  
 サンプルの実行方法を次の手順に示します。サンプルを実行すると、セキュリティ トークン要求がセキュリティ トークン サービスのコンソール ウィンドウに表示されます。操作要求と応答は、クライアントとサービスのコンソール ウィンドウに表示されます。いずれかのコンソール ウィンドウで Enter キーを押すと、アプリケーションがシャットダウンします。  
  
## Setup.cmd バッチ ファイル  
 このサンプルに用意されている Setup.cmd バッチ ファイルを使用すると、適切な証明書を使用してサーバーとセキュリティ トークン サービスを構成し、自己ホスト型アプリケーションを実行できるようになります。このバッチ ファイルにより、CurrentUser\/TrustedPeople 証明書ストアのどちらにも 2 つの証明書が作成されます。片方の証明書は CN\=STS のサブジェクト名を持ち、クライアントに発行するセキュリティ トークンを署名するためにセキュリティ トークン サービスが使用します。もう片方の証明書は CN\=localhost のサブジェクト名を持ち、サービスが暗号化を解除できるようにシークレットを暗号化するためにセキュリティ トークン サービスが使用します。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  Setup.cmd ファイルを実行して、必要な証明書を作成します。  
  
2.  ソリューションをビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。ソリューション内のすべてのプロジェクトがビルドされていることを確認します \(Shared、RSTRSTR、Service、SecurityTokenService、Client\)。  
  
3.  Service.exe と SecurityTokenService.exe がどちらも管理者権限で実行されていることを確認します。  
  
4.  Client.exe を実行します。  
  
#### サンプルの実行後にクリーンアップするには  
  
1.  サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## 参照