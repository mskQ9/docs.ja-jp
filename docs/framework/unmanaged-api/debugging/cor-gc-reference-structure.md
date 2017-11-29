---
title: "COR_GC_REFERENCE 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11be45743bd215315139fb77f016e85bc9b592c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corgcreference-structure"></a><span data-ttu-id="78f41-102">COR_GC_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="78f41-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="78f41-103">ガベージ コレクトされるオブジェクトに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="78f41-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f41-104">構文</span><span class="sxs-lookup"><span data-stu-id="78f41-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="78f41-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="78f41-105">Members</span></span>  
  
|<span data-ttu-id="78f41-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="78f41-106">Member</span></span>|<span data-ttu-id="78f41-107">説明</span><span class="sxs-lookup"><span data-stu-id="78f41-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="78f41-108">ハンドルまたはオブジェクトが所属するアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="78f41-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="78f41-109">その値があります`null`です。</span><span class="sxs-lookup"><span data-stu-id="78f41-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="78f41-110">ICorDebugValue またはガベージ コレクトされるオブジェクトに対応する ICorDebugReferenceValue インターフェイスのいずれか。</span><span class="sxs-lookup"><span data-stu-id="78f41-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="78f41-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)でルートの出所を示す列挙値。</span><span class="sxs-lookup"><span data-stu-id="78f41-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="78f41-112">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f41-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="78f41-113">ガベージ コレクトされるオブジェクトに関する追加データ。</span><span class="sxs-lookup"><span data-stu-id="78f41-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="78f41-114">この情報は、によって示される、オブジェクトのソースとは異なります。、`type`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="78f41-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="78f41-115">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f41-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f41-116">コメント</span><span class="sxs-lookup"><span data-stu-id="78f41-116">Remarks</span></span>  
 <span data-ttu-id="78f41-117">`type`フィールドは、 [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)参照元の場所を示す列挙値。</span><span class="sxs-lookup"><span data-stu-id="78f41-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="78f41-118">特定の`COR_GC_REFERENCE`値は、管理対象オブジェクトの次の種類のいずれかを反映できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="78f41-119">すべてのマネージ スタックからオブジェクト (`CorGCReferenceType.CorReferenceStack`)。</span><span class="sxs-lookup"><span data-stu-id="78f41-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="78f41-120">これには、共通言語ランタイムによって作成されたオブジェクトと同様に、マネージ コードでのライブ参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="78f41-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="78f41-121">オブジェクト ハンドル テーブルから (`CorGCReferenceType.CorHandle*`)。</span><span class="sxs-lookup"><span data-stu-id="78f41-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="78f41-122">これには、強い参照が含まれます (`HNDTYPE_STRONG`と`HNDTYPE_REFCOUNT`) とモジュールの静的変数。</span><span class="sxs-lookup"><span data-stu-id="78f41-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="78f41-123">ファイナライザー キューからのオブジェクト (`CorGCReferenceType.CorReferenceFinalizer`)。</span><span class="sxs-lookup"><span data-stu-id="78f41-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="78f41-124">ファイナライザー キューは、ファイナライザーが実行されるまで、オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="78f41-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="78f41-125">`extraData`フィールドには参照のソース (または型) によって余分なデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="78f41-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="78f41-126">指定できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78f41-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="78f41-127">`DependentSource`。</span><span class="sxs-lookup"><span data-stu-id="78f41-127">`DependentSource`.</span></span> <span data-ttu-id="78f41-128">場合、`type`は`CorGCREferenceType.CorHandleStrongDependent`、このフィールドはオブジェクトでガベージ コレクトされるオブジェクトの場合は、ルートを`COR_GC_REFERENCE.Location`です。</span><span class="sxs-lookup"><span data-stu-id="78f41-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="78f41-129">`RefCount`。</span><span class="sxs-lookup"><span data-stu-id="78f41-129">`RefCount`.</span></span> <span data-ttu-id="78f41-130">場合、`type`は`CorGCREferenceType.CorHandleStrongRefCount`、このフィールドは、ハンドルの参照カウントします。</span><span class="sxs-lookup"><span data-stu-id="78f41-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="78f41-131">`Size`。</span><span class="sxs-lookup"><span data-stu-id="78f41-131">`Size`.</span></span> <span data-ttu-id="78f41-132">場合、`type`は`CorGCREferenceType.CorHandleStrongSizedByref`、このフィールドは、ガベージ コレクターがオブジェクトのルートを計算する、オブジェクト ツリーの最後のサイズ。</span><span class="sxs-lookup"><span data-stu-id="78f41-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="78f41-133">この計算は最新の状態とは限りませんではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="78f41-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f41-134">要件</span><span class="sxs-lookup"><span data-stu-id="78f41-134">Requirements</span></span>  
 <span data-ttu-id="78f41-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78f41-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f41-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78f41-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78f41-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78f41-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78f41-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f41-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f41-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="78f41-139">See Also</span></span>  
 [<span data-ttu-id="78f41-140">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="78f41-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="78f41-141">デバッグ</span><span class="sxs-lookup"><span data-stu-id="78f41-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)