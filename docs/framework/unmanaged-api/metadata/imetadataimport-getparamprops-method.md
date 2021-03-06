---
title: IMetaDataImport::GetParamProps-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps-Methode
Ruft Metadatenwerte für den Parameter ab, auf den durch das angegebene ParamDef-Token verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `tk`  
 [in] Ein ParamDef-Token, die Metadaten für die zurückzugebenden Parameters darstellt.  
  
 `pmd`  
 [out] Ein Zeiger auf ein MethodDef-Token, das die Methode, die den Parameter akzeptiert darstellt.  
  
 `pulSequence`  
 [out] Die Ordnungsposition des Parameters in der Argumentliste der Methode.  
  
 `szName`  
 [out] Ein Puffer, der den Namen des Parameters enthält.  
  
 `cchName`  
 [in] Die angeforderte Größe in Breitzeichen `szName`.  
  
 `pchName`  
 [out] Die zurückgegebene Größe in Breitzeichen `szName`.  
  
 `pdwAttr`  
 [out] Ein Zeiger auf Attributflags, die dem Parameter zugeordnet.  
  
 `pdwCPlusTypeFlag`  
 [out] Ein Zeiger auf ein Flag, das angibt, die der Parameter ist ein <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Ein Zeiger auf eine Konstante Zeichenfolge, die durch den Parameter zurückgegeben.  
  
 `pcchValue`  
 [out] Die Größe des `ppValue` in Breitzeichen oder 0 (null), wenn `ppValue` errichtet keine Zeichenfolge.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Bibliothek:** als Ressource in MsCorEE.dll enthalten  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [IMetaDataImport-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
