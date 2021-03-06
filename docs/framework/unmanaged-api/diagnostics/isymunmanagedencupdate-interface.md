---
title: ISymUnmanagedENCUpdate-Schnittstelle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f68d000824779fcffb90ec031b86b50e8c80eccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate-Schnittstelle
Bietet Funktionen für das Feature bearbeiten und fortfahren.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetLocalVariableCount-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Ruft die Anzahl der lokalen Variablen ab.|  
|[GetLocalVariables-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Ruft die lokalen Variablen ab.|  
|[InitializeForEnc-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Ermöglicht das Methodengrenzen vor dem ersten Aufruf berechnet werden soll die [ISymUnmanagedENCUpdate:: Updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) Methode.|  
|[UpdateMethodLines-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Ermöglicht das Aktualisieren der Zeile für eine Methode, die nicht kompiliert wurde, aber, deren Zeilen verschoben wurden. Eine Delta für jede Anweisung ist zulässig.|  
|[UpdateSymbolStore2-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Kann ein Compiler Auslassen von Funktionen, die aus dem Programm Programmdatenbankdatei (PDB)-Stream nicht geändert wurden, vorausgesetzt, dass die Zeileninformationen die Anforderungen erfüllt. Die richtige Zeileninformationen kann mit den alten PDB-Zeileninformationen und einem Delta für alle Zeilen in der Funktion bestimmt werden.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Siehe auch  
 [Diagnosesymbolspeicher-Schnittstellen](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
