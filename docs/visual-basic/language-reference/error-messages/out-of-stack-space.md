---
title: "Nicht genügend Stapelspeicher (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a>Nicht genügend Stapelspeicher (Visual Basic)
Der Stapel ist ein Arbeitsbereich des Arbeitsspeichers, der vergrößert bzw. verkleinert sich dynamisch mit den Anforderungen an das ausgeführte Programm. Seine Grenzen wurden überschritten.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, dass die Prozeduren nicht zu tief geschachtelt sind.  
  
2.  Stellen Sie sicher, dass rekursive Prozeduren ordnungsgemäß beendet.  
  
3.  Wenn lokale Variablen mehr Speicherplatz als die verfügbare erforderlich ist, versuchen Sie, einige Variablen auf Modulebene deklariert werden. Sie können alle Variablen in der Prozedur auch statische deklarieren, abgrenzen, indem Sie die `Property`, `Sub`, oder `Function` Schlüsselwort mit `Static`. Oder Sie können die `Static` Anweisung, um einzelne statische Variablen innerhalb von Prozeduren deklarieren.  
  
4.  Definieren Sie einige Zeichenfolgen fester Länge als Zeichenfolgen mit variabler Länge, wie Zeichenfolgen mit fester Länge mehr Stapelspeicher als Zeichenfolgen variabler Länge verwendet. Sie können auch die Zeichenfolge auf Modulebene definieren, in denen es keine Stapelspeicher erfordert.  
  
5.  Überprüfen Sie die Anzahl der geschachtelten `DoEvents` Funktionsaufrufe mithilfe der `Calls` im Dialogfeld anzeigen, welche Prozeduren auf dem Stapel aktiv sind.  
  
6.  Stellen Sie sicher, dass Sie nicht "Ereigniskette" verursacht haben, durch das Auslösen eines Ereignisses, das eine Ereignisprozedur bereits auf dem Stapel aufgerufen. Eine Ereigniskette ist ein nicht abgeschlossenes rekursiven Prozeduraufruf ähnelt, jedoch ist weniger offensichtlich, da der Aufruf erfolgt [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statt eines expliziten Aufrufs im Code. Verwenden der `Calls` im Dialogfeld anzeigen, welche Prozeduren auf dem Stapel aktiv sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster "Arbeitsspeicher"](/visualstudio/debugger/memory-windows)
