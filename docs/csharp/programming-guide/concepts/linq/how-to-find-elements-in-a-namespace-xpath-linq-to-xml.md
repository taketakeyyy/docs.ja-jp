---
title: '方法: 名前空間内の要素を検索する (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: d85426cf7a7073c35b51157e59687e2b3bcdcf8a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253680"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>方法: 名前空間内の要素を検索する (XPath-LINQ to XML) (C#)

XPath 式を使用すると、特定の名前空間内のノードを検索できます。 XPath 式では、名前空間を指定する名前空間プレフィックスを使用します。 名前空間プレフィックスを含む XPath 式を解析するには、<xref:System.Xml.IXmlNamespaceResolver> を実装する XPath メソッドにオブジェクトを渡す必要があります。 この例では <xref:System.Xml.XmlNamespaceManager> を使用します。

XPath 式を次に示します。

`./aw:*`

## <a name="example"></a>例

次の例では、2 つの名前空間を含む XML ツリーを読み込みます。 <xref:System.Xml.XmlReader> を使用して XML ドキュメントを読み込ます。 次に、<xref:System.Xml.XmlNameTable> から <xref:System.Xml.XmlReader> を取得し、<xref:System.Xml.XmlNamespaceManager> から <xref:System.Xml.XmlNameTable> を取得します。 要素を選択する際には <xref:System.Xml.XmlNamespaceManager> を使用します。

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

この例を実行すると、次の出力が生成されます。

```output
Results are identical
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">
    <aw:ShippingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:ShippingAddress>
    <aw:BillingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:BillingAddress>
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>
    <aw:Item PartNum="LIT-01">
      <aw:ProductID>Litware Networking Card</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>20.99</aw:Price>
    </aw:Item>
    <aw:Item PartNum="LIT-25">
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>199.99</aw:Price>
    </aw:Item>
  </aw:PurchaseOrder>
```
