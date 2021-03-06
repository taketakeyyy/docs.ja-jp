---
title: GetPropertyQualifierSet 関数 (アンマネージ API リファレンス)
description: GetPropertyQualifierSet 関数は、プロパティに設定されている修飾子を取得します。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7bce241d10051e4c6be94cdfa40de23773fb0bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798473"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet 関数

特定のプロパティで設定された修飾子が取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`wszMethod`\
からプロパティ名。 `wszProperty`は有効`LPCWSTR`なを指している必要があります。

`ppQualSet`\
入出力プロパティの修飾子へのアクセスを許可するインターフェイスポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 エラーが発生した場合、新しいオブジェクトは返されず、ポインターはを`null`指すように設定されます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドは存在しません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが`null`です。 |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | 関数は、システムプロパティの修飾子を取得しようとします。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)メソッドの呼び出しをラップします。

この関数の呼び出しは、現在のオブジェクトが CIM クラス定義である場合にのみサポートされます。 CIM インスタンスを指す[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)ポインターでは、メソッド操作は使用できません。

各メソッドは独自の修飾子を持つことができるため、 [IWbemQualifierSet ポインター](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)によって呼び出し元はこれらの修飾子を追加、編集、または削除できます。

システムプロパティに修飾子がないため、システムプロパティ`WBEM_E_SYSTEM_PROPERTY`の[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)ポインターを取得しようとすると、関数はを返します。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
