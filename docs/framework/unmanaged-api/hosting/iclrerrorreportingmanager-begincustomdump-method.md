---
title: "ICLRErrorReportingManager::BeginCustomDump メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d09afd9fe0a2905c79ffb2d50b342041865b593b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump メソッド
エラー報告用にカスタムのヒープ ダンプの構成を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFlavor`  
 [in]A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)カスタム ヒープ ダンプを構築するためのヒープ ダンプの種類を示す値。  
  
 `dwNumItems`  
 [in]長さ、`items`配列。 場合`dwFlavor`が DUMP_FLAVOR_Mini、 `dwNumItems` 0 にする必要があります。  
  
 `items`  
 [in]配列[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)インスタンス、ミニ ダンプに追加する項目を指定します。 場合`dwFlavor`が DUMP_FLAVOR_Mini、 `items` null にする必要があります。  
  
 `dwReserved`  
 [in]将来使用するために予約されています。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 `BeginCustomDump`メソッドは、カスタム ヒープ ダンプ構成を設定します。 [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)メソッドは、カスタム ヒープ ダンプ構成をクリアし、その関連付けられた状態を解放します。 これはカスタム ヒープ ダンプの完了後に呼び出す必要があります。  
  
> [!IMPORTANT]
>  呼び出しに失敗する`EndCustomDump`によってメモリ リークが発生します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [CustomDumpItem 構造体](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [ECustomDumpFlavor 列挙型](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [ICLRErrorReportingManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
