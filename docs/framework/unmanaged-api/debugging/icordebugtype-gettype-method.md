---
title: ICorDebugType::GetType-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07f9974d0178a1a7502a97d54d7103ee795425f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType-Methode
Ruft einen CorElementType-Wert, den systemeigenen Typ der common Language Runtime (CLR) beschreibt <xref:System.Type> ICorDebugType dargestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ty`  
 [out] Ein Zeiger auf einen Wert von der `CorElementType` -Enumeration, die die CLR gibt <xref:System.Type> , die von diesem `ICorDebugType` darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Wert der `ty` ELEMENT_TYPE_CLASS oder ELEMENT_TYPE_VALUETYPE, ist die [ICorDebugType:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) Methode kann aufgerufen werden, um den nicht instanziierten Typ für einen generischen Typ abzurufen, rufen Sie Sie andernfalls nicht `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
