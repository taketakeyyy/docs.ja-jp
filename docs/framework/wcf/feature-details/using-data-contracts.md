---
title: データ コントラクトの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 3fd22cc0842c51b331905369915bd055235680c4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592192"
---
# <a name="using-data-contracts"></a>データ コントラクトの使用
*データ コントラクト* は、サービスとクライアントの間の正式な取り決めであり、交換されるデータが抽象的に記述されています。 つまり、クライアントとサービスが通信するために必要なのは同じデータ コントラクトだけで、同じ型を共有する必要はありません。 データ コントラクトは、パラメーターまたは戻り値の型ごとに、交換するためにシリアル化する (XML に変換する) 必要があるデータを正確に定義します。  
  
## <a name="data-contract-basics"></a>データ コントラクトの基本  
 Windows Communication Foundation (WCF) は、(変換して、XML から) データを逆シリアル化およびシリアル化する、既定では、データ コントラクト シリアライザーと呼ばれるシリアル化エンジンを使用します。 すべて .NET Framework のプリミティブ型、整数や文字列などと特定の種類などのプリミティブとして扱われます<xref:System.DateTime>と<xref:System.Xml.XmlElement>、準備なしでシリアル化できるし、既定のデータ コントラクトを持つと見なされます。 多くの .NET Framework 型は、既存のデータ コントラクトを持ちます。 シリアル化できるすべての型の一覧については、「 [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)」を参照してください。  
  
 新しい複合型を作成したら、シリアル化できるように、データ コントラクトを定義する必要があります。 既定では、 <xref:System.Runtime.Serialization.DataContractSerializer> はデータ コントラクトを推測し、公開されている型をすべてシリアル化します。 その型の読み書き可能なパブリック プロパティおよびパブリック フィールドは、すべてシリアル化されます。 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>を使用することにより、メンバーがシリアル化されないようにすることができます。 また、 <xref:System.Runtime.Serialization.DataContractAttribute> 属性および <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を使用して、データ コントラクトを明示的に作成することもできます。 これを行うには、通常、その型に <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用します。 この属性は、クラス、構造体、および列挙体に適用できます。 次に、データ コントラクト型の各メンバーに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用して、それが *データ メンバー*であること、つまり、シリアル化する必要があることを示す必要があります。 詳細については、次を参照してください。[シリアル化できる型](../../../../docs/framework/wcf/feature-details/serializable-types.md)します。  
  
### <a name="example"></a>例  
 <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性が明示的に適用されたサービス コントラクト (インターフェイス) の例を次に示します。 この例は、プリミティブ型はデータ コントラクトを必要としないのに対し、複合型は必要とすることを示しています。  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 次の例では、 `MyTypes.PurchaseOrder` 型のデータ コントラクトが作成され、 <xref:System.Runtime.Serialization.DataContractAttribute> と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がクラスとそのメンバーに適用されるかを示します。  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>メモ  
 以下に、データ コントラクトを作成する際に考慮する必要がある項目を示します。  
  
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 属性は、マークされていない型で使用した場合にのみ受け入れられます。 これには、 <xref:System.Runtime.Serialization.DataContractAttribute>、 <xref:System.SerializableAttribute>、 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>、 <xref:System.Runtime.Serialization.EnumMemberAttribute> のいずれかの属性でマークされていない型、または他の方法 ( <xref:System.Xml.Serialization.IXmlSerializable>など) でシリアル化可能としてマークされた型が含まれます。  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute> 属性は、フィールドおよびプロパティに適用できます。  
  
- メンバーのアクセシビリティ レベル (内部、プライベート、保護、またはパブリック) は、データ コントラクトに影響しません。  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が静的メンバーに適用されている場合は無視されます。  
  
- シリアル化中には、プロパティのデータ メンバーがシリアル化対象のプロパティの値を取得できるように、プロパティ取得コードが呼び出されます。  
  
- 逆シリアル化中には、まず初期化されていないオブジェクトが、その型のコンストラクターを呼び出さずに作成されます。 次に、すべてのデータ メンバーが逆シリアル化されます。  
  
- 逆シリアル化中には、プロパティのデータ メンバーが、プロパティを逆シリアル化されている値に設定できるように、プロパティ設定コードが呼び出されます。  
  
- データ コントラクトが有効であるためには、すべてのデータ メンバーをシリアル化できる必要があります。 シリアル化できるすべての型の一覧については、「 [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)」を参照してください。  
  
     ジェネリック型は、非ジェネリック型とまったく同じように処理されます。 ジェネリック パラメーターに対する特別な要件はありません。 たとえば、次の型について考えます。  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 この型は、ジェネリック型パラメーター (`T`) に使用される型をシリアル化できるかどうかに関係なくシリアル化できます。 すべてのデータ メンバーをシリアル化できる必要があるため、次の型をシリアル化できるのは、ジェネリック型パラメーターもシリアル化できる場合だけです。次のコード例を参照してください。  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 データ コントラクトを定義する WCF サービスのコード サンプル全体については、「 [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) 」のサンプルを参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [データ コントラクト名](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [データ コントラクトの等価性](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [データ メンバーの順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [既知のデータ コントラクト型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [データ コントラクトのバージョン管理](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [バージョン トレラントなシリアル化コールバック](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [データ メンバーの既定値](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)
- [データ コントラクト シリアライザーでサポートされる型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [方法: クラスまたは構造体に基本的なデータ コントラクトを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
