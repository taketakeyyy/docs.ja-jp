---
title: 自動実装するプロパティ - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 44f3beb9de8c9d339c42db26bb9c510998abc7d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597141"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>自動実装するプロパティ (C# プログラミング ガイド)
C# 3.0 以降では、自動実装プロパティを使用することで、プロパティ アクセサーに追加のロジックが必要ない場合は、プロパティをより簡潔に宣言できます。 これにより、クライアント コードでオブジェクトを作成することも可能になります。 次の例に示すようにプロパティを宣言する場合、コンパイラによって、プロパティの `get` および `set` アクセサーを介してのみアクセスできる、プライベートの匿名バッキング フィールドが作成されます。  
  
## <a name="example"></a>例  
 次の例に、自動実装プロパティを持つ簡単なクラスを示します。  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 C# 6 以降では、フィールドと同様に自動実装プロパティを初期化することができます。  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 前の例に示したクラスは、変更可能です。 クライアント コードは、オブジェクト内の値を作成後に変更できます。 データだけでなく、重要な動作 (メソッド) も含まれる複雑なクラスでは、多くの場合、パブリック プロパティが必要です。 ただし、値 (データ) のセットをカプセル化しているだけで、動作をほとんど、またはまったく含まない小さなクラスや構造体の場合は、set アクセサーを [private](../../language-reference/keywords/private.md) (コンシューマーからは変更できない) として宣言するか、または get アクセサー (コンストラクターを除くすべての場所で変更できない) のみを宣言することで、オブジェクトを変更不可能にする必要があります。  詳細については、「[方法 :自動実装するプロパティを使用して簡易クラスを実装する](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [プロパティ](./properties.md)
- [修飾子](../../language-reference/keywords/modifiers.md)
