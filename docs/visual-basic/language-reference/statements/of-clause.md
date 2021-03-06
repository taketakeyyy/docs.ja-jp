---
title: Of 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784151"
---
# <a name="of-clause-visual-basic"></a>Of 句 (Visual Basic)
`Of` 句を紹介します。これは *ジェネリック* クラス、構造体、インターフェイス、デリゲート、またはプロシージャ上で型パラメーターを識別します。ジェネリック型については、「[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)」を参照してください。

## <a name="using-the-of-keyword">Of キーワードの使用</a>
 次のコード例では、2 つの型パラメーターを受け取るクラスのアウトラインを定義するために `Of` キーワードを使用しています。`keyType` パラメーターは <xref:System.IComparable> インターフェイスによって制限されているため、使用するコードは <xref:System.IComparable> を実装する型引数を与えなければなりません。これは、`add` プロシージャが <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> メソッドを呼び出すことができるようにするために必要です。制約の詳細については、「[型リスト](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。

```
Public Class Dictionary(Of entryType, keyType As IComparable)
    Public Sub add(ByVal e As entryType, ByVal k As keyType)
        Dim dk As keyType
        If k.CompareTo(dk) = 0 Then
        End If
    End Sub
    Public Function find(ByVal k As keyType) As entryType
    End Function
End Class
```

 上記のクラス定義を完了すると、そこから様々な `dictionary` クラスを構築することができます。`entryType` と `keyType` に与える型が、そのクラスが持つエントリーの型と、互いのエントリーと関連するキーの型を決定します。制約により、`keyType` には <xref:System.IComparable> を実装する型を与えなければなりません。

 次のコード例は、`String` エントリーを持ち、`Integer` キーを互いに関連づけるオブジェクトを作成します。`Integer` は <xref:System.IComparable> を実装し、それゆえに `keyType` の制約を満たします。

```
Dim d As New dictionary(Of String, Integer)
```

 キーワード `Of` は次のコンテキストで使用できます。

 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)

 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)

 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)

 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)

 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)

 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>関連項目

- <xref:System.IComparable>
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
