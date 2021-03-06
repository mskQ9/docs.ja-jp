---
title: "CorDebugMappingResult 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 924cfec87b99cba9621af02d4e78e72094060ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult 列挙型
命令ポインター (IP) の値が得られた方法の詳細を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MAPPING_PROLOG`|ネイティブ コードは、プロローグでは ip アドレスの値が 0 であるためです。|  
|`MAPPING_EPILOG`|Ip アドレスの値は、メソッドの最後の命令のアドレスは、エピローグ内のネイティブ コード。|  
|`MAPPING_NO_INFO`|マッピング情報がない、メソッドを使用できるため、IP の値は 0 です。|  
|`MAPPING_UNMAPPED_ADDRESS`|メソッドのマッピング情報が、現在のアドレスを Microsoft intermediate language (MSIL) コードにマップすることはできません。 Ip アドレスの値は 0 です。|  
|`MAPPING_EXACT`|メソッドは、MSIL コードに完全にマップまたはフレームが解釈されているので、ip アドレスの値は正確です。|  
|`MAPPING_APPROXIMATE`|メソッドが正常にマップされましたが、ip アドレスの値は、概数である可能性があります。|  
  
## <a name="remarks"></a>コメント  
 使用することができます、 [icordebugilframe::getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)命令ポインターの値を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
