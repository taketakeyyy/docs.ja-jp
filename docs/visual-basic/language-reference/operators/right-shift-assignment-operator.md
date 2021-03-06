---
title: '>>= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 08d4e251a96ca387a709319e752351db6825d9e8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701356"
---
# <a name="-operator-visual-basic"></a>> > = 演算子 (Visual Basic)
変数またはプロパティの値に対して算術右シフトを実行し、その結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 整数型の変数またはプロパティ (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、または `ULong`)。  
  
 `amount`  
 必須。 @No__t-0 に変換されたデータ型の数値式。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 演算子の左側の要素は、単純なスカラー変数、プロパティ、または配列の要素にすることができます。 変数またはプロパティを[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)にすることはできません。  
  
 @No__t 0 演算子は、まず変数またはプロパティの値に対して算術右シフトを実行します。 次に、演算子は、その操作の結果を変数またはプロパティに戻します。  
  
 算術シフトは循環していません。つまり、結果の一方の端からシフトされたビットはもう一方の端には再入されません。 算術右シフトでは、右端のビット位置を超えてシフトされたビットは破棄され、左端のビットは左側に空いているビット位置に反映されます。 つまり、`variableorproperty` に負の値がある場合、空いている位置は1に設定されます。 @No__t-0 が正の場合、またはそのデータ型が符号なしの型の場合、空いた位置は0に設定されます。  
  
## <a name="overloading"></a>オーバーロード  
 [> > 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)は*オーバーロード*できます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 @No__t-0 演算子のオーバーロードは、`>>=` 演算子の動作に影響します。 コードで `>>` をオーバーロードするクラスまたは構造体に @no__t 0 を使用している場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`>>=` 演算子を使用して、`Integer` 変数のビットパターンを指定した量だけ右にシフトし、その結果を変数に代入します。  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- [>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
