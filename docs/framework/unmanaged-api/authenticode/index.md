---
title: Authenticode (アンマネージ API リファレンス)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2c0163d03a19a7bc00ae705fd633ef4f0880082
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776558"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (アンマネージ API リファレンス)
Authenticode XrML ライセンスの作成および検証モジュールをサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [_AxlGetIssuerPublicKeyHash 関数](axlgetissuerpublickeyhash-function.md)  
 指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。  
  
 [_AxlPublicKeyBlobToPublicKeyToken 関数](axlpublickeyblobtopublickeytoken-function.md)  
 CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。  
  
 [_AxlRSAKeyValueToPublicKeyToken 関数](axlrsakeyvaluetopublickeytoken-function.md)  
 Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。  
  
 [CertFreeAuthenticodeSignerInfo 関数](certfreeauthenticodesignerinfo-function.md)  
 AXL_AUTHENTICODE_SIGNER_INFO 構造に割り当てられているリソースを解放します。  
  
 [CertFreeAuthenticodeTimestamperInfo 関数](certfreeauthenticodetimestamperinfo-function.md)  
 AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造に割り当てられているリソースを開放します。  
  
 [CertTimestampAuthenticodeLicense 関数](certtimestampauthenticodelicense-function.md)  
 CertCreateAuthenticodeLicense で作成された Authenticode XrML ライセンスにタイム スタンプを付けます。  
  
 [CertVerifyAuthenticodeLicense 関数](certverifyauthenticodelicense-function.md)  
 Authenticode XrML ライセンスの有効性を検証します。  
  
 [AXL_AUTHENTICODE_SIGNER_INFO 構造体](axl-authenticode-signer-info-structure.md)  
 Authenticode の署名者情報を定義します。  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体](axl-authenticode-timestamper-info-structure.md)  
 Authenticode のタイム スタンパー情報を定義します。  
  
## <a name="see-also"></a>関連項目

- [アンマネージ API リファレンス](../index.md)
