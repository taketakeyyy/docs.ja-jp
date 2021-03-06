---
title: '方法: Windows フォーム上のコントロールのサイズを変更する'
ms.date: 03/30/2017
f1_keywords:
- Size.Height
- Size.Width
helpviewer_keywords:
- controls [Windows Forms], resizing
- size [Windows Forms], controls
- Windows Forms controls, size
ms.assetid: d2dba441-a8c0-4705-b8e8-2e5d86d6e7ec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e659bf02ea079afc10561e1d83f7ab7cef29a2e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987047"
---
# <a name="how-to-resize-controls-on-windows-forms"></a>方法: Windows フォームのコントロールのサイズを変更する

個々のコントロールのサイズを変更したり、コントロール<xref:System.Windows.Forms.Button>や<xref:System.Windows.Forms.GroupBox>コントロールなど、同じ種類または異なる種類の複数のコントロールのサイズを変更したりできます。

## <a name="to-resize-a-control"></a>コントロールのサイズを変更するには

Visual Studio で、サイズを変更するコントロールを選択し、8つのサイズ変更ハンドルのいずれかをドラッグします。

> [!NOTE]
> コントロールを選択し、 **shift**キーを押しながら**方向**キーを押すと、コントロールのサイズが一度に1ピクセルずつ変更されます。 **Shift**キーまたは**Ctrl**キーを押しながら**下方向**キーまたは**右方向**キーを押すと、コントロールのサイズが大きくなります。

## <a name="to-resize-multiple-controls-on-a-form"></a>フォーム上の複数のコントロールのサイズを変更するには

1. Visual Studio で、 **Ctrl**キーまたは**Shift**キーを押しながら、サイズを変更するコントロールを選択します。 選択した最初のコントロールのサイズは、他のコントロールに使用されます。

2. **[書式]** メニューの **[同じサイズに揃える]** をクリックし、4つのオプションのいずれかを選択します。 最初の3つのコマンドは、最初に選択されたコントロールに合わせてコントロールのサイズを変更します。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
- [方法: デザイナーを使用して Windows フォームのサイズを変更する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))
