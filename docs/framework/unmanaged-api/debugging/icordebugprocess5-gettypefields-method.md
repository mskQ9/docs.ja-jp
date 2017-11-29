---
title: "ICorDebugProcess5::GetTypeFields メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="c5046-102">ICorDebugProcess5::GetTypeFields メソッド</span><span class="sxs-lookup"><span data-stu-id="c5046-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="c5046-103">型に属するフィールドについてを説明します。</span><span class="sxs-lookup"><span data-stu-id="c5046-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5046-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5046-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5046-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5046-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="c5046-106">[in]フィールド情報を取得する型の識別子。</span><span class="sxs-lookup"><span data-stu-id="c5046-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="c5046-107">[in]数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)フィールド情報を取得するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c5046-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="c5046-108">[out]配列[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)型に属しているフィールドに関する情報を提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c5046-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="c5046-109">[out]数へのポインター [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)に含まれるオブジェクト`fields`です。</span><span class="sxs-lookup"><span data-stu-id="c5046-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5046-110">コメント</span><span class="sxs-lookup"><span data-stu-id="c5046-110">Remarks</span></span>  
 <span data-ttu-id="c5046-111">`celt`フィールドを設定するメソッドを使用してフィールド情報の数を指定するパラメーター`fields`の値に対応する必要があります、`COR_TYPE_LAYOUT::numFields`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="c5046-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5046-112">要件</span><span class="sxs-lookup"><span data-stu-id="c5046-112">Requirements</span></span>  
 <span data-ttu-id="c5046-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5046-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5046-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5046-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5046-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5046-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5046-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5046-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5046-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5046-117">See Also</span></span>  
 [<span data-ttu-id="c5046-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5046-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="c5046-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5046-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)