---
title: ICorDebugCode3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4efcf6d477ab006e179e283ca4ce7b62c27018a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960763"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 インターフェイス
"" のコード "と" ICorDebugCode2 "を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReturnValueLiveOffSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
