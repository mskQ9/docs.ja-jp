---
title: "ICorDebugManagedCallback2::Exception メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception メソッド
例外ハンドラーの検索が開始されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]ICorDebugAppDomain を表すオブジェクトを含む例外がスローされたスレッドのアプリケーション ドメインへのポインター。  
  
 `pThread`  
 [in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pFrame`  
 [in]によって決定されたように、フレームを表す ICorDebugFrame オブジェクトへのポインター、`dwEventType`パラメーター。 詳細については、「解説」セクションの表を参照してください。  
  
 `nOffset`  
 [in]によって決定される、オフセットを指定する整数、`dwEventType`パラメーター。 詳細については、「解説」セクションの表を参照してください。  
  
 `dwEventType`  
 [in]この例外コールバックの型を指定する CorDebugExceptionCallbackType 列挙型の値です。  
  
 `dwFlags`  
 [in]値、 [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)例外に関する追加情報を指定する列挙体  
  
## <a name="remarks"></a>コメント  
 `Exception`フェーズでは、検索、例外処理プロセスのさまざまな時点で呼び出されるコールバック。 つまり、呼び出すことができますを超える 1 回、例外のアンワインド中にします。  
  
 によって参照される ICorDebugThread オブジェクトから処理される例外を取得できる、`pThread`パラメーター。  
  
 特定のフレームとのオフセットによって決定されます、`dwEventType`次のようにパラメーター。  
  
|`dwEventType` の値|`pFrame` の値|`nOffset` の値|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|例外をスローしたフレームです。|フレーム内の命令ポインター。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|スローされた例外の位置に最も近いユーザー コード フレーム。|フレーム内の命令ポインター。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Catch ハンドラーを含むフレーム。|Catch ハンドラーの最初の Microsoft intermediate language (MSIL) オフセットします。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|定義されていません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
