---
title: "IHostSyncManager::CreateRWLockWriterEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c89dec681102f96f96f1d7f3e802ded0a2df7b4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="292fc-102">IHostSyncManager::CreateRWLockWriterEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="292fc-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="292fc-103">ライター ロックの実装の自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="292fc-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="292fc-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="292fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="292fc-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="292fc-106">[in]自動リセット イベントに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="292fc-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="292fc-107">[out]アドレスへのポインター、 [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)インスタンス、または null の場合、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="292fc-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="292fc-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="292fc-108">Return Value</span></span>  
  
|<span data-ttu-id="292fc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="292fc-109">HRESULT</span></span>|<span data-ttu-id="292fc-110">説明</span><span class="sxs-lookup"><span data-stu-id="292fc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="292fc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="292fc-111">S_OK</span></span>|<span data-ttu-id="292fc-112">`CreateRWLockWriterEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="292fc-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="292fc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="292fc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="292fc-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="292fc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="292fc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="292fc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="292fc-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="292fc-116">The call timed out.</span></span>|  
|<span data-ttu-id="292fc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="292fc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="292fc-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="292fc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="292fc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="292fc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="292fc-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="292fc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="292fc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="292fc-121">E_FAIL</span></span>|<span data-ttu-id="292fc-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="292fc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="292fc-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="292fc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="292fc-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="292fc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="292fc-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="292fc-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="292fc-126">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="292fc-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="292fc-127">コメント</span><span class="sxs-lookup"><span data-stu-id="292fc-127">Remarks</span></span>  
 <span data-ttu-id="292fc-128">CLR の呼び出し、`CreateRWLockWriterEvent`への参照を取得するメソッド、`IHostAutoEvent`ライター ロックの実装で使用するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="292fc-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="292fc-129">ホストが、指定された cookie を使用してのイテレーション メソッドを呼び出すことにより、ロックで待機しているタスクを決定する、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="292fc-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292fc-130">要件</span><span class="sxs-lookup"><span data-stu-id="292fc-130">Requirements</span></span>  
 <span data-ttu-id="292fc-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="292fc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292fc-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="292fc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="292fc-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="292fc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="292fc-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292fc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292fc-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="292fc-135">See Also</span></span>  
 [<span data-ttu-id="292fc-136">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="292fc-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="292fc-137">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="292fc-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="292fc-138">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="292fc-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="292fc-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="292fc-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)