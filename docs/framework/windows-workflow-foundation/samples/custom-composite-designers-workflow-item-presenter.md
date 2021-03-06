---
title: カスタム複合デザイナー - Workflow Item Presenter
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038370"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>カスタム複合デザイナー - Workflow Item Presenter
<xref:System.Activities.Presentation.WorkflowItemPresenter>は、任意のアクティビティを配置できる "ドロップゾーン" の作成を可能にする WF デザイナープログラミングモデルのキーの種類です。 このサンプルでは、このような "ドロップゾーン" を格納するアクティビティデザイナーを構築する方法を示します。

 このサンプルでは、次のことを示します。

## <a name="demonstrates"></a>使用例

- <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用したカスタム アクティビティ デザイナーの作成

- メタデータ ストアを使用したカスタム デザイナーの登録。

- 宣言および命令による再ホストされたツールボックスのプログラミング。

## <a name="sample-details"></a>サンプルの詳細
 このサンプルのコードを次に示します。

- カスタム アクティビティ デザイナーは `SimpleNativeActivity` クラス用に作成されます。

- <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成します。

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 `ModelItem.Body` にバインドする WPF のデータ バインドの使用に注意してください。 `ModelItem`は、デザイナーが<xref:System.Activities.Presentation.ActivityDesigner>使用されている基になるオブジェクト (この場合は**simplenativeactivity)** ) を参照するのプロパティです。

#### <a name="to-setup-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. Visual Studio 2010 でソリューションを開きます。

2. F5 キーを押してアプリケーションをコンパイルし、実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [ワークフロー デザイナーを使用したアプリケーションの開発](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
