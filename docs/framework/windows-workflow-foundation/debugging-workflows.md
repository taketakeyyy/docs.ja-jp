---
title: デバッグのワークフロー
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 3947e61161b0e2108fa48fbc7e33fb7601645a1b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291488"
---
# <a name="debugging-workflows"></a>デバッグのワークフロー

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。 ワークフローは、デザイナー、XAML、およびコードでデバッグできます。

## <a name="debugging-in-the-workflow-designer"></a>ワークフロー デザイナーでのデバッグ

ワークフローデザイナーのアクティビティにブレークポイントを設定するには、アクティビティを強調表示し、 <kbd>F9</kbd>キーを押すか、アクティビティのコンテキストメニューを使用します。 ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。 次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。 詳細については、「[ワークフローデザイナーを使用したワークフローのデバッグ](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)」を参照してください。

## <a name="debugging-in-xaml"></a>XAML でのデバッグ

デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。 XAML での実行ポイントを表示するには、ワークフローの実行が一時停止されているときに、ワークフローデザイナーで **[Xaml ビュー]** を選択します。 デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。 詳細については、「[方法 :ワークフローデザイナー @ no__t-0 を使用して XAML をデバッグします。

## <a name="debugging-in-code"></a>コードでのデバッグ

ブレークポイントを設定するには、コードペインの左余白をクリックするか、カーソルを設定する行にカーソルを合わせて<kbd>F9</kbd>キーを押します。

## <a name="attaching-to-a-workflow-process"></a>ワークフロー プロセスへのアタッチ

ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。 そのため、ワークフロー作成者は、Internet Information Services (IIS) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。

## <a name="remote-debugging"></a>Remote Debugging

Windows Workflow Foundation (WF) リモートデバッグは、他の Visual Studio コンポーネントのリモートデバッグと同じように機能します。 リモートデバッグの使用方法の詳細については、@no__t を参照してください。リモートデバッグ @ no__t を有効にします。

> [!NOTE]
> ワークフローアプリケーションが x86 アーキテクチャを対象としていて、64ビットオペレーティングシステムを実行しているコンピューターでホストされている場合、リモートコンピューターに Visual Studio がインストールされていない場合、またはワークフローアプリケーションのターゲットがに変更されている場合を除き、リモートデバッグは機能しません。**任意の CPU**。

## <a name="extending-the-workflow-debugging-service"></a>ワークフロー デバッグ サービスの拡張

ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。 詳細については、「<xref:System.Activities.Presentation.Debug.DebuggerService>」の記事を参照してください。
