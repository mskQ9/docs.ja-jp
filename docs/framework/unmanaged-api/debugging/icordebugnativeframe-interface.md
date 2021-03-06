---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd49d745be9db0c4c5309cf5febc3ff651a860f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe-interface1"></a>ICorDebugNativeFrame Interface1
ネイティブ フレームで使用される ICorDebugFrame の特殊な実装です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|命令ポインターをネイティブ コードで指定されたオフセット位置に設定しても安全かどうかを示す値を取得します。|  
|[GetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|ネイティブ コードに、スタック フレームのオフセットを取得します。|  
|[GetLocalDoubleRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|引数またはネイティブ フレームの 2 つのメモリ レジスタに格納されているローカル変数の値を表す ICorDebugValue へのポインターを取得します。|  
|[GetLocalMemoryRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|ポインターを取得、`ICorDebugValue`うち下位ビットが指定のレジスタに格納されているし、上位ビットが指定されたメモリ アドレスに格納されている、ローカル変数の値を表すです。|  
|[GetLocalMemoryValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|ポインターを取得、`ICorDebugValue`を表す、指定されたメモリ アドレスに格納されているローカル変数の値。|  
|[GetLocalRegisterMemoryValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|ポインターを取得、`ICorDebugValue`うち上位ビットが指定のレジスタに格納されているし、指定されたメモリ アドレスに下位ビットが格納されている、ローカル変数の値を表す|  
|[GetLocalRegisterValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|ポインターを取得、`ICorDebugValue`引数または、指定されたネイティブなレジスタに格納されているローカル変数の値を表すです。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|ポインターを取得、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)これのレジスタ セットを表す`ICorDebugNativeFrame`です。|  
|[SetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|命令ポインターをネイティブ コードで指定されたオフセット位置に設定します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
