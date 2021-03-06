---
title: '方法: [継承ピッカー] ダイアログ ボックスを使用してフォームを継承する'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 6fdd1e72e4256db30d9fb6a3b560c3d538435c79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931877"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker"></a>方法: 継承ピッカーを使用してフォームを継承する

フォームまたは他のオブジェクトを継承する最も簡単な方法は、 **[継承ピッカー]** ダイアログ ボックスを使用することです。 これを使用して、その他のソリューションで作成済みのコードまたはユーザー インターフェイス (UI) を利用できます。

> [!NOTE]
> **[継承ピッカー]** ダイアログ ボックスを使用してフォームを継承するには、そのフォームを含むプロジェクトが、実行可能ファイルまたは DLL に組み込まれている必要があります。 プロジェクトをビルドするには、 **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。

## <a name="create-a-windows-form-by-using-the-inheritance-picker"></a>継承ピッカーを使用して Windows フォームを作成する

1. Visual Studio の **[プロジェクト]** メニューで、 **[Windows フォームの追加]** を選択します。

   **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2. **継承されたフォーム**テンプレートを選択して、**名前**ボックスで名前を付けます。 **[追加]** ボタンをクリックして続行します。

   **[継承ピッカー]** ダイアログ ボックスが開きます。 現在のプロジェクトに既にフォームが含まれている場合は、 **[継承ピッカー]** ダイアログ ボックスに表示されます。

3. 別のアセンブリのフォームから継承する場合は、 **[参照]** ボタンをクリックします。

4. **[継承元コンポーネントを含むファイルの選択]** ダイアログ ボックスで、必要なフォームまたはモジュールを含むプロジェクトに移動します。

5. 選択する .exe ファイルまたは .dll ファイルの名前をクリックしてそれを選択し、 **[開く]** ボタンをクリックします。

   これにより、 **[継承ピッカー]** ダイアログ ボックスに戻り、ここで、配置されているプロジェクトと共にコンポーネントが一覧表示されます。

6. コンポーネントを選択します。

   **ソリューション エクスプローラー**で、コンポーネントがプロジェクトに追加されます。 UI がある場合は、継承されたフォームの一部であるコントロールにはグリフ (![Visual Basic の継承シンボルのスクリーン ショット](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)) のマークが付き、選択すると、コントロールがスーパークラスのフォーム上で持っているセキュリティのレベルを示す罫線も表示されます。 様々なセキュリティ レベルに対応する動作を、次の表に示します。

    |コントロールのセキュリティ レベル|継承したフォームを使用したデザイナーとコード エディターの間で使用できる相互作用|
    |-------------------------------|--------------------------------------------------------------------------------|
    |パブリック|サイズ変更ハンドルがある標準の罫線 : コントロールのサイズが変更され、移動される可能性があります。 コントロールは、宣言するクラスにより内部的にアクセスでき、他のクラスにより外部的にアクセスできます。|
    |プロテクト|サイズ変更ハンドルがある標準の罫線 : コントロールのサイズが変更され、移動される可能性があります。 宣言するクラス、および親クラスから継承したクラスにより内部的にアクセスできますが、外部クラスによってアクセスすることはできません。|
    |保護された内部 (Visual Basic の保護されたフレンド)|サイズ変更ハンドルがある標準の罫線 : コントロールのサイズが変更され、移動される可能性があります。 宣言するクラス、親クラスから継承したクラス、およびそれを含むアセンブリのその他のメンバーにより、内部的にアクセスできます。|
    |内部 (Visual Basic のフレンド)|**[プロパティ]** ウィンドウに表示されるプロパティで、フォームに表示される、サイズ変更ハンドルのない標準の罫線。 ただし、コントロールのすべての側面が読み取り専用と見なされます。 コントロールを移動またはサイズ変更したり、プロパティを変更したりできません。 グループ ボックスと同様に、コントロールがその他のコントロールのコンテナーである場合は、これらのコントロールがパブリックでも、新しいコントロールを追加することはできず、既存のコントロールを削除することもできません。 コントロールは、それを含むアセンブリの他のメンバーによってのみアクセスできます。|
    |プライベート|**[プロパティ]** ウィンドウに表示されるプロパティで、フォームに表示される、サイズ変更ハンドルのない標準の罫線。 ただし、コントロールのすべての側面が読み取り専用と見なされます。 コントロールを移動またはサイズ変更したり、プロパティを変更したりできません。 グループ ボックスと同様に、コントロールがその他のコントロールのコンテナーである場合は、これらのコントロールがパブリックでも、新しいコントロールを追加することはできず、既存のコントロールを削除することもできません。 コントロールは、宣言したクラスによってのみアクセスできます。|

     基本フォームの外観を変更する方法については、「[基本フォームの外観を変更した場合の影響](effects-of-modifying-base-form-appearance.md)」を参照してください。

    > [!NOTE]
    > 継承されたコントロールとコンポーネントを、Windows フォーム上の標準的なコントロールとコンポーネントに結合する場合、z オーダーとの競合が発生する可能性があります。 これを修正するには、 **[書式]** メニュー内でクリックして、 **[順序]** をポイントし、 **[最前面へ移動]** または **[最背面へ移動]** をクリックして z オーダーを変更します。 コントロールの z オーダーに関する詳細については[方法:Windows フォーム上にオブジェクトを階層化する](../controls/how-to-layer-objects-on-windows-forms.md)を参照してください。

## <a name="see-also"></a>関連項目

- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [基本フォームの外観を変更した場合の影響](effects-of-modifying-base-form-appearance.md)
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
