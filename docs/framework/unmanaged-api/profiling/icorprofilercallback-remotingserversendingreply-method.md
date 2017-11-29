---
title: "ICorProfilerCallback::RemotingServerSendingReply メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b99b2de235634b715a6f5ba9fee9ee49ab34063a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="c976c-102">ICorProfilerCallback::RemotingServerSendingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="c976c-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="c976c-103">プロセスがリモート メソッド呼び出しの要求の処理が完了し、チャネルを介して応答を送信しようとしていますが、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c976c-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c976c-104">構文</span><span class="sxs-lookup"><span data-stu-id="c976c-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c976c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c976c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="c976c-106">[in]指定された値と対応する GUID を指すポインター [icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)これらの条件下で。</span><span class="sxs-lookup"><span data-stu-id="c976c-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="c976c-107">リモート処理 GUID cookie はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="c976c-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="c976c-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="c976c-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="c976c-109">GUID の cookie は、クライアント側のプロセスでアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="c976c-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="c976c-110">これにより、論理呼び出し履歴の作成とリモート処理の呼び出しのペアを容易にします。</span><span class="sxs-lookup"><span data-stu-id="c976c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c976c-111">[in]値が`true`呼び出しの場合は、それ以外の非同期`false`です。</span><span class="sxs-lookup"><span data-stu-id="c976c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c976c-112">要件</span><span class="sxs-lookup"><span data-stu-id="c976c-112">Requirements</span></span>  
 <span data-ttu-id="c976c-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c976c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c976c-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c976c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c976c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c976c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c976c-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c976c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c976c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c976c-117">See Also</span></span>  
 [<span data-ttu-id="c976c-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c976c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)