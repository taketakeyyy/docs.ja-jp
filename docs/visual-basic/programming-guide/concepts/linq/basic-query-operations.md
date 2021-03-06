---
title: 基本的なクエリ操作 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 12f10f30dd767f3435044f2bbebe0eb865c29d0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939373"
---
# <a name="basic-query-operations-visual-basic"></a>基本的なクエリ操作 (Visual Basic)
このトピックでは、Visual Basic の[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]式と、クエリで実行する一般的な操作の一部について簡単に説明します。 詳細については、次のトピックを参照してください。  
  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [クエリ](../../../../visual-basic/language-reference/queries/index.md)  
  
 [チュートリアル: Visual Basic でのクエリの作成](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>データソースの指定 (から)  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリでは、最初の手順として、クエリを実行するデータソースを指定します。 そのため、 `From`クエリの句は常に最初になります。 クエリ演算子ソースの種類に基づいて、結果を選択して整形します。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 句では、データ`customers`ソース、、 `cust`および*範囲変数*を指定します。 `From` 範囲変数はループ反復変数に似ていますが、クエリ式では実際のイテレーションは発生しません。 クエリが実行されると、多くの場合`For Each` 、ループを使用して、範囲変数はの`customers`連続する各要素への参照として機能します。 `cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。 明示的な型指定なしで記述されたクエリの例については、「[クエリ操作での型の関係 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)」を参照してください。  
  
 Visual Basic で`From`句を使用する方法の詳細については、「 [from 句](../../../../visual-basic/language-reference/queries/from-clause.md)」を参照してください。  
  
## <a name="filtering-data-where"></a>データのフィルター処理 (Where)  
 最も一般的なクエリ操作では、ブール式の形式でフィルターが適用されている可能性があります。 次に、式が true になっている要素のみが返されます。 `Where`句は、フィルター処理を実行するために使用されます。 フィルターでは、結果のシーケンスに含めるデータソース内の要素を指定します。 次の例では、ロンドンに住所を持つ顧客のみが含まれています。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 やなど`And`の論理演算子を使用する`Or`と、 `Where`句でフィルター式を組み合わせることができます。 たとえば、名前が Devon であるロンドンからの顧客のみを返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 ロンドンまたはパリの顧客を返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Visual Basic で`Where`句を使用する方法の詳細については、「 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)」を参照してください。  
  
## <a name="ordering-data-order-by"></a>データの並べ替え (Order By)  
 多くの場合、返されたデータを特定の順序に並べ替えると便利です。 `Order By`句により、返されたシーケンス内の要素が、指定されたフィールドで並べ替えられます。 たとえば、次のクエリでは、 `Name`プロパティに基づいて結果が並べ替えられます。 は`Name`文字列であるため、返されるデータはアルファベット順 (a から Z) に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 結果を逆の順序 (Z から A) で並び替えるには、`Order By...Descending` 句を使用します。 と`Ascending` が`Descending`どちらも`Ascending`指定されていない場合、既定値はです。  
  
 Visual Basic で`Order By`句を使用する方法の詳細については、「 [order by 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
## <a name="selecting-data-select"></a>データの選択 (Select)  
 句`Select`は、返される要素のフォームとコンテンツを指定します。 たとえば、結果を、完全`Customer`なオブジェクト、1つのプロパティ、プロパティのサブセット、さまざまなデータソースからのプロパティの組み合わせ、または計算に基づいた新しい結果型のいずれ`Customer`で構成するかを指定できます。 `Select` 句でソース要素のコピー以外のものを生成する場合、その操作は*投影*と呼ばれます。  
  
 完全な`Customer`オブジェクトで構成されるコレクションを取得するには、範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 インスタンスが多数のフィールドを持つ大きなオブジェクトで、取得するすべてのが名前である場合は、次の例に`cust.Name`示すようにを選択できます。 `Customer` ローカル型の推論では、結果の型がオブジェクトの`Customer`コレクションから文字列のコレクションに変更されることが認識されます。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 データソースから複数のフィールドを選択するには、次の2つの選択肢があります。  
  
- `Select`句で、結果に含めるフィールドを指定します。 コンパイラは、これらのフィールドをプロパティとして持つ匿名型を定義します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例で返される要素は匿名型のインスタンスなので、コード内の他の場所で型を名前で参照することはできません。 コンパイラによって指定された型の名前に、通常の Visual Basic コードでは無効な文字が含まれています。 次の例では、の`londonCusts4`クエリによって返されるコレクション内の要素は匿名型のインスタンスです。  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     \- または -  
  
- 結果に含める特定のフィールドを含む名前付きの型を定義し、 `Select`句でその型のインスタンスを作成および初期化します。 このオプションは、返されるコレクションの外部で個々の結果を使用する必要がある場合、またはメソッドの呼び出しでパラメーターとして渡す必要がある場合にのみ使用します。 次の例`londonCusts5`のの型は IEnumerable (namephone) です。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Visual Basic で`Select`句を使用する方法の詳細については、「 [Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)」を参照してください。  
  
## <a name="joining-data-join-and-group-join"></a>データの結合 (結合とグループ結合)  
 `From`句で複数のデータソースを組み合わせるには、いくつかの方法があります。 たとえば、次のコードでは、2つのデータソースを使用し、両方のプロパティを結果に暗黙的に結合しています。 このクエリでは、姓が母音で始まる学生を選択します。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> 次の方法で[作成された学生の一覧を使用して、このコードを実行できます。項目](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)の一覧を作成します。  
  
 キーワードは、 `INNER JOIN` SQL のに相当します。 `Join` 2つのコレクションの要素間でのキー値の一致に基づいて、2つのコレクションを結合します。 このクエリでは、キー値が一致するコレクション要素のすべてまたは一部が返されます。 たとえば、次のコードでは、前の暗黙的な結合のアクションが複製されます。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`は、SQL のの場合`LEFT JOIN`と同様に、コレクションを1つの階層コレクションに結合します。 詳細については、「 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)と[Group join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)」を参照してください。  
  
## <a name="grouping-data-group-by"></a>データのグループ化 (Group By)  
 句を`Group By`追加すると、要素の1つまたは複数のフィールドに従って、クエリ結果の要素をグループ化できます。 たとえば、次のコードでは、学生をクラス年別にグループ化しています。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 次の方法で[作成された学生の一覧を使用してこのコードを実行する場合:項目](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)の一覧を作成すると、 `For Each`ステートメントからの出力は次のようになります。  
  
 比新任  
  
 Tucker、Michael  
  
 お金  
  
 Debra、  
  
 Tucker、Lance  
  
 比シニア  
  
 Omelchenko、Svetlana  
  
 Osada、Michiko  
  
 Fakhouri、Fadi  
  
 Feng  
  
 Adams、マネージャー  
  
 比Freshman  
  
 Sven  
  
 Cesar、  
  
 次のコードに示すバリエーションでは、クラス年を順に並べ替え、各年の各学生を姓で並べ替えます。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 の詳細`Group By`については、「 [group by 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
