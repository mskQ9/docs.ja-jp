---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d6ac2967b4314a57aa30bbb34ff3d354a6365
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="38f09-102">ICorDebugProcess2::SetUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="38f09-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="38f09-103">ネイティブ イメージを指定したオフセット位置には、アンマネージのブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="38f09-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f09-104">構文</span><span class="sxs-lookup"><span data-stu-id="38f09-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38f09-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38f09-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="38f09-106">[in]A`CORDB_ADDRESS`ネイティブ イメージのオフセットを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="38f09-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="38f09-107">[in]サイズをバイト単位での`buffer`配列。</span><span class="sxs-lookup"><span data-stu-id="38f09-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="38f09-108">[out]ブレークポイントで置き換えられるオペコードを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="38f09-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="38f09-109">[out]返されるバイト数へのポインター、`buffer`配列。</span><span class="sxs-lookup"><span data-stu-id="38f09-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f09-110">コメント</span><span class="sxs-lookup"><span data-stu-id="38f09-110">Remarks</span></span>  
 <span data-ttu-id="38f09-111">ネイティブ イメージのオフセットが共通言語ランタイム (CLR) 内にある場合は、ブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="38f09-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="38f09-112">これにより、CLR がデバッガーでブレークポイントが設定されている場合、帯域外のブレークポイントのディスパッチを回避できます。</span><span class="sxs-lookup"><span data-stu-id="38f09-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f09-113">要件</span><span class="sxs-lookup"><span data-stu-id="38f09-113">Requirements</span></span>  
 <span data-ttu-id="38f09-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="38f09-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f09-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38f09-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38f09-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38f09-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f09-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f09-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>