---
title: "静的に解決された型パラメーター (F#)"
description: "F# で使用する方法について静的に解決される型パラメーターは、実行時ではなく、コンパイル時に実際の型に置き換えられています。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 14c629d6223584113af47636495be61decca02ad
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="statically-resolved-type-parameters"></a>静的に解決される型パラメーター

A*静的に解決される型パラメーター*実行時ではなく、コンパイル時に実際の型に置き換えられる型パラメーターです。 これらの前にはキャレット (^) 記号が付きます。


## <a name="syntax"></a>構文

```
ˆtype-parameter
```

## <a name="remarks"></a>コメント
F# 言語には、異なる 2 種類の型パラメーターがあります。 1 つ目の種類は、標準のジェネリック型パラメーターです。 これらは、`'T` や `'U` のようにアポストロフィ (') で示されます。 これらは、他の .NET Framework 言語のジェネリック型パラメーターと同じです。 もう 1 つの種類は、静的に解決される型パラメーターであり、`^T` や `^U` のようにキャレット記号で示されます。

静的に解決される型パラメーターは、主にメンバー制約で使用する場合に役立ちます。これは、型引数を使用するために特定のメンバーが必要であることを指定できる制約です。 この種の制約を、標準のジェネリック型パラメーターを使用して作成する方法はありません。

2 種類の型パラメーターの類似点と相違点の概要を次の表に示します。

|機能|ジェネリック|静的に解決される|
|-------|-------|-------------------|
|構文|`'T`, `'U`|`^T`, `^U`|
|解決時期|実行時|コンパイル時|
|メンバー制約|メンバー制約では使用できません。|メンバー制約で使用できます。|
|コード生成|標準のジェネリック型パラメーターを持つ型 (またはメソッド) では、単一のジェネリック型またはジェネリック メソッドが生成されます。|各型で必要とされる、型およびメソッドの複数のインスタンス化が生成されます。|
|型での使用|型で使用できます。|型では使用できません。|
|インライン関数での使用|いいえ。 標準のジェネリック型パラメーターではインライン関数をパラメーター化できません。|はい。 静的に解決される型パラメーターは、インライン以外の関数またはメソッドでは使用できません。|

多数の F# コア ライブラリ関数 (特に演算子) には、静的に解決される型パラメーターがあります。 これらの関数および演算子はインラインであり、数値の計算に効率的なコードが生成されます。

演算子を使用するインライン メソッドおよび関数、または静的に解決される型パラメーターを持つ他の関数を使用するインライン メソッドおよび関数では、それらのメソッドおよび関数自体でも静的に解決される型パラメーターを使用できます。 多くの場合、型推論では、それらのインライン関数が静的に解決される型パラメーターを持つと推論されます。 静的に解決される型パラメーターを持つと推論される演算子の定義を次の例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

解決された `(+@)` の型は、`(+)` および `(*)` の使用に基づいており、これらの両方では型推論によって、静的に解決される型パラメーターによるメンバー制約が推論されます。 F# インタープリターに表示される解決された型は、次のとおりです。

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

出力は次のとおりです。

```
2
1.500000
```

4.1 以降では F# で、静的に解決される型のパラメーター シグネチャ内の具体的な型名も指定できます。  言語の以前のバージョンでは、型名は実際には、コンパイラによって推論できませんでしたが、シグネチャでは実際には指定できません。  F# 4.1、時点で静的に解決される型のパラメーター シグネチャで具体的な型名を指定することも可能性があります。 次に例を示します。

```fsharp
type CFunctor() = 
      static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
      static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

      // default implementation of replace
      static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

      // call overridden replace if present
      static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
      ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>参照
[ジェネリック](index.md)

[型推論](../type-inference.md)

[自動ジェネリック化](automatic-generalization.md)

[制約](constraints.md)

[インライン関数](../functions/inline-functions.md)
