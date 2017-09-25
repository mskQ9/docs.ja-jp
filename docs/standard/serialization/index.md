---
title: ".NET でのシリアル化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 4aaef3337c9ee2464925ed4dc31c075a4e68a9dc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/18/2017

---
# <a name="serialization-in-net"></a>.NET でのシリアル化
シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。 シリアル化を補完するプロセスとして、ストリームをオブジェクトに変換する逆シリアル化があります。 これらのプロセスを組み合わせて使用することで、データを簡単に格納および転送できます。  
  
.NET 機能では、次の 2 つのシリアル化テクノロジを採用しています。  
  
-   バイナリ シリアル化は、型そのものを正確に維持するため、アプリケーションを次回起動するまでの間、オブジェクトの状態を維持するのに役立ちます。 たとえば、クリップボードを出力先としてオブジェクトをシリアル化することによって、そのオブジェクトを異なるアプリケーション間で共有できます。 オブジェクトをシリアル化して、ストリーム、ディスク、メモリ、ネットワーク上などに出力できます。 リモート処理では、シリアル化を使用して、コンピューター間やアプリケーション ドメイン間でオブジェクトを "値渡し" します。  
  
-   XML シリアル化では、パブリック プロパティとパブリック フィールドのみがシリアル化され、型そのものは維持されません。 これは、データを使用するアプリケーションに制限を加えずに、データを提供または処理する場合に有効です。 XML はオープン標準であるため、Web 経由でデータを共有する場合には有用な選択肢となります。 SOAP も同様のオープン標準であるため、有用な選択肢です。  
  
## <a name="in-this-section"></a>このセクションの内容  
[シリアル化に関する「方法」トピック](../../../docs/standard/serialization/serialization-how-to-topics.md)  
このセクションに含まれている、方法を説明するトピックへのリンクの一覧を示します。
  
[バイナリ シリアル化](../../../docs/standard/serialization/binary-serialization.md)  
共通言語ランタイムに付属しているバイナル シリアル化機構について説明します。

[XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
共通言語ランタイムに付属している XML シリアル化および SOAP シリアル化機構について説明します。

[シリアル化ツール](../../../docs/standard/serialization/serialization-tools.md)  
これらのツールは、シリアル化コードの開発に役立ちます。

[シリアル化のサンプル](../../../docs/standard/serialization/serialization-samples.md)  
サンプルでは、シリアル化の方法を示します。

## <a name="reference"></a>参照
<xref:System.Runtime.Serialization>オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。
  
<xref:System.Xml.Serialization>  
オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用できるクラスが含まれています。