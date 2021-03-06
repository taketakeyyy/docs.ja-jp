---
title: 'チュートリアル: Windows Communication Foundation サービスコントラクトの定義'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928872"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>チュートリアル: Windows Communication Foundation サービスコントラクトの定義

このチュートリアルでは、基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な5つのタスクについて説明します。 チュートリアルの概要については、 [「チュートリアル:Windows Communication Foundation アプリケーション](getting-started-tutorial.md)の概要」をご覧ください。

WCF サービスを作成する場合、最初のタスクとして、サービスコントラクトを定義します。 サービス コントラクトは、サービスがサポートする操作を指定します。 操作は Web サービス メソッドと見なすことができます。 サービスコントラクトを作成するには、 C#ビジュアルまたは VISUAL BASIC (VB) インターフェイスを定義します。 インターフェイスには、次の特性があります。

- インターフェイスの各メソッドは、特定のサービス操作に対応しています。 
- インターフェイスごとに、 <xref:System.ServiceModel.ServiceContractAttribute>属性を適用する必要があります。
- 各操作/メソッドに対して、 <xref:System.ServiceModel.OperationContractAttribute>属性を適用する必要があります。 

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
>
> - **WCF サービスライブラリ**プロジェクトを作成します。
> - サービスコントラクトインターフェイスを定義します。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>WCF サービスライブラリプロジェクトを作成し、サービスコントラクトインターフェイスを定義する

1. Visual Studio を管理者として開きます。 これを行うには、 **[スタート]** メニューで Visual Studio プログラムを選択し、ショートカットメニューの [**管理者として実行** **] を** > クリックします。

2. **WCF サービスライブラリ**プロジェクトを作成します。

   1. **[ファイル]** メニューで、 **[新規作成]** 、 >  **[プロジェクト]** の順に作成します。

   2. **[新しいプロジェクト]** ダイアログボックスの左側で、 **[ C#ビジュアル]** または **[Visual Basic]** を展開し、 **[WCF]** カテゴリを選択します。 Visual Studio によって、ウィンドウの中央のセクションにプロジェクトテンプレートの一覧が表示されます。 **[WCF サービスライブラリ]** を選択します。

      > [!NOTE]
      > [ **WCF**プロジェクトテンプレート] カテゴリが表示されない場合は、Visual Studio の**Windows Communication Foundation**コンポーネントのインストールが必要になることがあります。 **[新しいプロジェクト]** ダイアログボックスで、左側の **[Visual Studio インストーラーを開く]** リンクを選択します。 **[個々のコンポーネント]** タブを選択し、 **[開発アクティビティ]** カテゴリの下の **[Windows Communication Foundation]** を見つけて選択します。 **[変更]** を選択して、コンポーネントのインストールを開始します。

   3. ウィンドウの下部にある **[名前]** に「 *Getting、lib* 」と入力し、**ソリューション名**に「 *getting始め*」と入力します。 

   4. **[OK]** を選択します。

      Visual Studio によってプロジェクトが作成されます。プロジェクトには次の3つのファイルがあります。*IService1.cs* (または、Visual Basic プロジェクトの場合は*IService1* )、 *Service1.cs* (または Service1 プロジェクトの Visual Basic 場合は )、および*app.config*。Visual Studio では、これらのファイルを次のように定義します。 
      - *IService1*ファイルには、サービスコントラクトの既定の定義が含まれています。 
      - *Service1*ファイルには、サービスコントラクトの既定の実装が含まれています。 
      - *App.config*ファイルには、VISUAL Studio WCF サービスホストツールを使用して既定のサービスを読み込むために必要な構成情報が含まれています。 WCF サービスホストツールの詳細については、「 [Wcf サービスホスト (wcfsvchost.exe)](wcf-service-host-wcfsvchost-exe.md)」を参照してください。

      > [!NOTE]
      > Visual Basic 開発者向け環境設定を使用して Visual Studio をインストールした場合は、ソリューションが非表示になることがあります。 この場合は、 **[ツール]** メニューの **[オプション]** を選択し、 **[オプション]** ウィンドウで [**プロジェクトおよびソリューション** > ] **[全般]** を選択します。 **[常にソリューションを表示]** を選択します。 また、[**作成時に新しいプロジェクトを保存**する] が選択されていることを確認します。

3. **ソリューションエクスプローラー**から、 **IService1.cs**または**IService1**ファイルを開き、そのコードを次のコードに置き換えます。

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     このコントラクトは、オンライン電卓を定義します。 インターフェイスが<xref:System.ServiceModel.ServiceContractAttribute>属性でマークされていることに`ServiceContract`注意してください (簡略化されています)。 `ICalculator` この属性は、コントラクト名を明確に区別する名前空間を定義します。 このコードでは、各電卓操作<xref:System.ServiceModel.OperationContractAttribute>を属性でマーク`OperationContract`しています (簡略化されています)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
>
> - WCF サービスライブラリプロジェクトを作成します。
> - サービスコントラクトインターフェイスを定義します。

次のチュートリアルに進み、WCF サービスコントラクトを実装する方法を学習してください。

> [!div class="nextstepaction"]
> [チュートリアル: WCF サービスコントラクトを実装する](how-to-implement-a-wcf-contract.md)
