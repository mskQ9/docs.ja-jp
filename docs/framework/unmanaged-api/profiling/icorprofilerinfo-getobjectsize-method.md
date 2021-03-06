---
title: "ICorProfilerInfo::GetObjectSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize メソッド
指定したオブジェクトのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `objectId`  
 [in]オブジェクトの ID。  
  
 `pcSize`  
 [out]オブジェクトのサイズ (バイト) へのポインター。  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]
>  このメソッドは、互換性のために残されています。 返します COR_E_OVERFLOW オブジェクトに対して 4 GB より大きい 64 ビット プラットフォーム上でします。 使用して、 [icorprofilerinfo 4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)メソッド代わりにします。  
  
 別のオブジェクトと同じ型の多くの場合、同じサイズであります。 ただし、配列や文字列などのいくつかの種類は、各オブジェクトのサイズが異なる場合があります。  
  
 によって返されるサイズ、`GetObjectSize`メソッドでは、配置のオブジェクトがガベージ コレクション ヒープにした後に表示される埋め込みは含まれません。 使用する場合、`GetObjectSize`ガベージ コレクション ヒープのオブジェクトからオブジェクトを進める方法は、手動で、必要に応じて、パディングの配置を追加します。  
  
-   32 ビット Windows で COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 4 バイトのアラインメントを使用し、COR_PRF_GC_LARGE_OBJECT_HEAP が 8 バイト アラインメントを使用します。  
  
-   64 ビット Windows で、配置は常に 8 バイトです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
