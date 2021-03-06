---
title: "CorNativeType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeType
helpviewer_keywords: CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6be442dd74f6a71494e140b76357be1bc9e1b747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cornativetype-enumeration"></a>CorNativeType 列挙型
ネイティブのアンマネージ型を記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|互換性のために残されています。|  
|`NATIVE_TYPE_VOID`|互換性のために残されています。|  
|`NATIVE_TYPE_BOOLEAN`|0 でなく、FALSE、TRUE がここでは、4 バイト ブール値は 0 です。|  
|`NATIVE_TYPE_I1`|8 ビット符号付き整数値。|  
|`NATIVE_TYPE_U1`|符号なし 8 ビット整数値。|  
|`NATIVE_TYPE_I2`|16 ビット符号付き整数値。|  
|`NATIVE_TYPE_U2`|符号なし 16 ビット整数値。|  
|`NATIVE_TYPE_I4`|符号付き 32 ビット整数値。|  
|`NATIVE_TYPE_U4`|32 ビットの符号なし整数値。|  
|`NATIVE_TYPE_I8`|64 ビット符号付き整数値。|  
|`NATIVE_TYPE_U8`|64 ビットの符号なし整数値。|  
|`NATIVE_TYPE_R4`|4 バイト浮動小数点数値。|  
|`NATIVE_TYPE_R8`|8 バイト浮動小数点数値です。|  
|`NATIVE_TYPE_SYSCHAR`|互換性のために残されています。|  
|`NATIVE_TYPE_VARIANT`|互換性のために残されています。|  
|`NATIVE_TYPE_CURRENCY`|マネージに対応する数値の COM 型<xref:System.Decimal>型です。|  
|`NATIVE_TYPE_PTR`|互換性のために残されています。|  
|`NATIVE_TYPE_DECIMAL`|互換性のために残されています。|  
|`NATIVE_TYPE_DATE`|互換性のために残されています。|  
|`NATIVE_TYPE_BSTR`|COM 相互運用。|  
|`NATIVE_TYPE_LPSTR`|LPSTR、文字列値です。|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR、文字列値です。|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR、文字列値です。|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|固定のシステム定義の文字列値。|  
|`NATIVE_TYPE_OBJECTREF`|互換性のために残されています。|  
|`NATIVE_TYPE_IUNKNOWN`|COM 相互運用。|  
|`NATIVE_TYPE_IDISPATCH`|COM 相互運用。|  
|`NATIVE_TYPE_STRUCT`|ネイティブ構造体の値です。|  
|`NATIVE_TYPE_INTF`|COM 相互運用。|  
|`NATIVE_TYPE_SAFEARRAY`|COM 相互運用。|  
|`NATIVE_TYPE_FIXEDARRAY`|固定長配列値です。|  
|`NATIVE_TYPE_INT`|ネイティブの 16 ビット符号付き整数値。|  
|`NATIVE_TYPE_UINT`|ネイティブの 16 ビット符号なし整数値。|  
|`NATIVE_TYPE_NESTEDSTRUCT`|互換性のために残されています。<br /><br /> NATIVE_TYPE_STRUCT を使用します。|  
|`NATIVE_TYPE_BYVALSTR`|COM 相互運用。|  
|`NATIVE_TYPE_ANSIBSTR`|COM 相互運用。|  
|`NATIVE_TYPE_TBSTR`|COM 相互運用。<br /><br /> プラットフォームによっては、BSTR、ANSIBSTR またはを選択します。|  
|`NATIVE_TYPE_VARIANTBOOL`|2 バイト ブール値、ここで true の場合は、-1、FALSE は 0。|  
|`NATIVE_TYPE_FUNC`|関数ポインター。|  
|`NATIVE_TYPE_ASANY`|ネイティブ型への参照。|  
|`NATIVE_TYPE_ARRAY`|指定されていない型のメンバーを含む配列への参照。|  
|`NATIVE_TYPE_LPSTRUCT`|構造体への 32 ビット整数ポインター。|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|カスタム マーシャラーのネイティブ型です。<br /><br /> 次の形式の文字列でこの後にする必要があります:「ネイティブ型の名前/0Custom マーシャラーは、0/名前/0Optional cookie をタイプ」または"{ネイティブ種類を表す GUID}/0Custom マーシャラー型の名前/0Optional cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM 相互運用。<br /><br /> ELEMENT_TYPE_I4 では、この型は、VT_HRESULT にマップされます。|  
|`NATIVE_TYPE_IINSPECTABLE`|ネイティブ`IInspectable`型です。|  
|`NATIVE_TYPE_HSTRING`|ネイティブ`HString`です。|  
|`NATIVE_TYPE_MAX`|値が無効です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
