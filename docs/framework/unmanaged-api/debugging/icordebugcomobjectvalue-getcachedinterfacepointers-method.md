---
title: ICorDebugComObjectValue::GetCachedInterfacePointers-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfacePointers
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers-Methode
Ruft den unformatierten Schnittstellenzeiger, der auf den aktuellen Runtime callable Wrapper (RCW) zwischengespeichert.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bIInspectableOnly`  
 [in] Ein Wert, der angibt, ob die Methode nur zurückliefert [!INCLUDE[wrt](../../../../includes/wrt-md.md)] Schnittstellen (`IInspectable` Schnittstellen) oder alle COM-Schnittstellen, die von den Runtime callable Wrapper (RCW) zwischengespeichert werden.  
  
 `celt`  
 [in] Die Anzahl der Objekte, deren Adressen sind abgerufen werden sollen.  
  
 `pceltFetched`  
 [out] Ein Zeiger auf die Anzahl der `CORDB_ADDRESS` Rückgabewerte, die tatsächlich `ptrs`.  
  
 `ptrs`  
 Ein Zeiger auf die Startadresse eines Arrays von `CORDB_ADDRESS` zwischengespeicherte Benutzeroberflächenobjekte Werte, die die Adressen enthalten.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ICorDebugComObjectValue-Schnittstelle](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [Debuggen von Schnittstellen](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
