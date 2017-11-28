---
title: "IMetaDataAssemblyImport::GetExportedTypeProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps メソッド
指定したメタデータ シグネチャを持つエクスポートされた型のプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mdct`  
 [in]`mdExportedType`エクスポートされた型を表すメタデータ トークン。  
  
 `szName`  
 [out]エクスポートされた型の名前。  
  
 `cchName`  
 [in]ワイド文字単位のサイズの`szName`します。  
  
 `pchName`  
 [out]実際に返されるワイド文字の数`szName`  
  
 `ptkImplementation`  
 [out]`mdFile`、 `mdAssemblyRef`、または`mdExportedType`含まれているか、エクスポートされた型のプロパティにアクセスできるようにするメタデータ トークン。  
  
 `ptkTypeDef`  
 [out]ポインター、`mdTypeDef`ファイル内の型を表すトークンです。  
  
 `pdwExportedTypeFlags`  
 [out]エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。 1 つまたは複数フラグ値を指定できます[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)値。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)