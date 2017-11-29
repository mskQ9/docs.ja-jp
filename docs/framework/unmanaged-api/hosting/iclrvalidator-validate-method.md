---
title: "ICLRValidator::Validate メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 50915201b6e57bd116b80f067f01b8862372bc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="103b9-102">ICLRValidator::Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="103b9-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="103b9-103">ポータブル実行可能 (PE) または Microsoft intermediate language (MSIL) で指定されたファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="103b9-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="103b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="103b9-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
#### <a name="parameters"></a><span data-ttu-id="103b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="103b9-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="103b9-106">[in]ポインター、`IVEHandler`妥当性確認エラーを処理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="103b9-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="103b9-107">[in]現在の識別子<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="103b9-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="103b9-108">[in]組み合わせた[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)を実行する検証の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="103b9-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="103b9-109">[in]検証を終了する前に許可されるエラーの最大数。</span><span class="sxs-lookup"><span data-stu-id="103b9-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="103b9-110">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="103b9-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="103b9-111">[in]検証に使用するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="103b9-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="103b9-112">[in]ファイル バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="103b9-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="103b9-113">[in]検証に使用するファイルのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="103b9-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="103b9-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="103b9-114">Return Value</span></span>  
  
|<span data-ttu-id="103b9-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="103b9-115">HRESULT</span></span>|<span data-ttu-id="103b9-116">説明</span><span class="sxs-lookup"><span data-stu-id="103b9-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="103b9-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="103b9-117">S_OK</span></span>|<span data-ttu-id="103b9-118">`Validate`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="103b9-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="103b9-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="103b9-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="103b9-120">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="103b9-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="103b9-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="103b9-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="103b9-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="103b9-122">The call timed out.</span></span>|  
|<span data-ttu-id="103b9-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="103b9-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="103b9-124">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="103b9-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="103b9-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="103b9-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="103b9-126">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="103b9-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="103b9-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="103b9-127">E_FAIL</span></span>|<span data-ttu-id="103b9-128">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="103b9-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="103b9-129">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="103b9-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="103b9-130">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="103b9-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="103b9-131">要件</span><span class="sxs-lookup"><span data-stu-id="103b9-131">Requirements</span></span>  
 <span data-ttu-id="103b9-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="103b9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="103b9-133">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="103b9-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="103b9-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="103b9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="103b9-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="103b9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103b9-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="103b9-136">See Also</span></span>  
 [<span data-ttu-id="103b9-137">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="103b9-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)