---
title: -reference (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 552fbcf920be609de83708a995a87761f6080220
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005271"
---
# <a name="-reference-visual-basic"></a>-reference (Visual Basic)
コンパイラは、指定したアセンブリ内の型情報を、現在コンパイルしているプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-reference:fileList  
```

または

```console
-r:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`fileList`|必須。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。|  
  
## <a name="remarks"></a>コメント  
 インポートするファイルには、アセンブリメタデータが含まれている必要があります。 アセンブリの外部で参照できるのはパブリック型だけです。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。  
  
 別のアセンブリ (アセンブリ B) を参照するアセンブリ (アセンブリ A) を参照する場合は、次の場合にアセンブリ B を参照する必要があります。  
  
- アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。  
  
- アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。  
  
 アセンブリ参照が1つ以上存在するディレクトリを指定するには、 [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を使用します。  
  
 コンパイラがアセンブリ (モジュールではない) の型を認識するには、型を強制的に解決する必要があります。 これを行う方法の1つの例は、型のインスタンスを定義することです。 コンパイラのアセンブリの型名を解決するために、他の方法を使用できます。 たとえば、アセンブリ内の型から継承する場合、型名はコンパイラに認識されます。  
  
 Vbc.exe ファイルは、一般的に使用される .NET Framework アセンブリを参照します。既定では、このファイルが使用されます。 コンパイラで Vbc.exe を使用しない場合は、`-noconfig` を使用します。  
  
 `-reference` の省略形は `/r` です。  
  
## <a name="example"></a>例  
 次のコマンドは、ソースファイル `Input.vb` および参照アセンブリを `Metad1.dll` と `Metad2.dll` からコンパイルして、`Out.exe` を生成します。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
