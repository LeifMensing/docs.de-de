---
title: EnumerateCLRs-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs-Funktion
Stellt einen Mechanismus für das Auflisten der CLRs in einem Prozess bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `debuggeePID`  
 [in] Die Prozess-ID des Prozesses aus dem geladene CLRs aufgezählt werden.  
  
 `ppHandleArrayOut`  
 [out] Ein Zeiger auf ein Array mit Ereignishandles, die zum Fortsetzen eines CLR-Starts verwendet werden. Die Gültigkeit der einzelnen Handle im Array ist nicht garantiert. Wenn das Handle gültig ist, wird es als Ereignis zur Startfortsetzung für die entsprechende Common Language Runtime im gleichen Index von `ppStringArrayOut` verwendet.  
  
 `ppStringArrayOut`  
 [out] Ein Zeiger auf ein Array von Zeichenfolgen, die vollständige Pfade zu CLRs angeben, die in den Prozess geladen werden.  
  
 `pdwArrayLengthOut`  
 [out] Ein Zeiger auf ein DWORD, das die Länge des gleichlangen `ppHandleArrayOut` und `pdwArrayLengthOut` enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK  
 Die Anzahl der CLRs im Prozess wurde erfolgreich ermittelt, und das entsprechende Handle und die Pfadarrays wurden ordnungsgemäß aufgefüllt.  
  
 E_INVALIDARG  
 Entweder ist `ppHandleArrayOut` oder `ppStringArrayOut` Null, oder `pdwArrayLengthOut` ist NULL.  
  
 E_OUTOFMEMORY  
 Die Funktion kann nicht genug Speicher für die Handle- und Pfadarrays reservieren.  
  
 E_FAIL (oder andere E_-Rückgabecodes)  
 Geladene CLRs können nicht aufgezählt werden.  
  
## <a name="remarks"></a>Hinweise  
 Für einen Zielprozess, der durch `debuggeePID` identifiziert wird, gibt die Funktion ein Array von Pfaden, `ppStringArrayOut`, an im Prozess geladene CLRs, ein Array von Ereignishandles, `ppHandleArrayOut`, das möglicherweise ein Ereignis zur Startfortsetzung für die CLR in demselben Index enthält, und die Größe der Arrays zurück, `pdwArrayLengthOut`, die die Anzahl der geladenen CLRs angibt.  
  
 Unter dem Windows-Betriebssystem wird `debuggeePID` einem Betriebssystem-Prozessbezeichner zugeordnet.  
  
 Der Arbeitsspeicher für `ppHandleArrayOut` und `ppStringArrayOut` wird von dieser Funktion zugeordnet. Um den belegten Arbeitsspeicher freizugeben, rufen Sie [CloseCLREnumeration-Funktion](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Diese Funktion kann mit beiden auf null festgelegten Arrayparametern aufgerufen werden, um die Anzahl der CLRs im Zielprozess zurückzugeben. Aus dieser Anzahl kann ein Aufrufer die Größe des Puffers ableiten, der erstellt wird: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** dbgshim.h  
  
 **Bibliothek:** dbgshim.dll  
  
 **.NET Framework-Versionen:** 3.5 SP1
