---
title: "LoadLibraryShim 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b8fe8413d0eff332e60508a083f03574e58d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 関数
指定したバージョンの .NET Framework 再頒布可能パッケージに含まれている DLL を読み込みます。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。 使用して、 [iclrruntimeinfo::loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szDllName`  
 [in].NET Framework ライブラリから読み込まれる DLL の名前を表す 0 で終わる文字列。  
  
 `szVersion`  
 [in]読み込まれる DLL のバージョンを表す、0 で終わる文字列。 場合`szVersion`は null、読み込みはバージョン 4 未満である指定された DLL の最新バージョン用に選択したバージョンです。 つまり、同じかまたは version 4 より大きいすべてのバージョン パラメーターは無視されます`szVersion`が null で、バージョン 4 未満のバージョンがインストールされていない場合、DLL 読み込みに失敗するとします。 これはのインストールを行うことを確認するため、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]既存のアプリケーションまたはコンポーネントには影響しません。 エントリを参照して[インプロセス SxS と移行のクイック スタート](http://go.microsoft.com/fwlink/?LinkId=200329)CLR チームのブログでします。  
  
 `pvReserved`  
 将来使用するために予約されています。  
  
 `phModDll`  
 [out]モジュールのハンドルへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|CLR_E_SHIM_RUNTIMELOAD|読み込み`szDllName`共通言語ランタイム (CLR)、および必要なバージョンの CLR を読み込めません。 読み込みが必要です。|  
  
## <a name="remarks"></a>コメント  
 この関数は、.NET Framework 再頒布可能パッケージに含まれている Dll の読み込みに使用されます。 ユーザーが生成した Dll は読み込まれません。  
  
> [!NOTE]
>  以降、.NET Framework version 2.0 と、読み込まれる CLR Fusion.dll の読み込みとします。 Fusion.dll で関数が、ラッパーが、この実装は、ランタイムによって提供されるためです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [サポートされなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
