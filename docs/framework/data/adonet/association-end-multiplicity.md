---
title: アソシエーション End の多重度
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786947"
---
# <a name="association-end-multiplicity"></a>アソシエーション End の多重度
*アソシエーション end の多重度*は、[アソシエーション](association-type.md)の1つの end に存在できる[エンティティ型](entity-type.md)のインスタンスの数を定義します。  
  
 アソシエーション End の多重度には、次のいずれかの値を指定できます。  
  
- 1つ (1):アソシエーション end に1つのエンティティ型インスタンスが存在することを示します。  
  
- 0または 1 (0 ..1):アソシエーション end に0個または1個のエンティティ型インスタンスが存在することを示します。  
  
- many (\*):アソシエーション end に0個以上のエンティティ型インスタンスが存在することを示します。  
  
 アソシエーションは、多くの場合、そのアソシエーション End の多重度により特徴付けられます。 たとえば、アソシエーションの end に多重度 1 (1) と多く (\*) がある場合、アソシエーションは一対多のアソシエーションと呼ばれます。 次の例で、`PublishedBy` アソシエーションは一対多のアソシエーションです (出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されます)。 `WrittenBy` アソシエーションは多対多のアソシエーションです (書籍の著者が複数の場合があり、著者は複数の書籍を執筆することができます)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 `Publisher` End の多重度は 1 (1) で、 `Book` end の多重度は多数 (\*) です。  
  
 ![3種類のエンティティを持つモデルの例](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework は、概念スキーマ定義言語 ([CSDL](./ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
