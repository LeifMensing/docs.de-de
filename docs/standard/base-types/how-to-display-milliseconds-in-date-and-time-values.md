---
title: 'Gewusst wie: Anzeigen der Millisekunden in Datums- und Uhrzeitwerten'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Gewusst wie: Anzeigen der Millisekunden in Datums- und Uhrzeitwerten
Bei den Standardformatierungsmethoden für Datum und Uhrzeit, wie <xref:System.DateTime.ToString?displayProperty=nameWithType>, werden die Stunden, Minuten und Sekunden eines Uhrzeitwerts berücksichtigt, deren Millisekundenkomponente jedoch nicht. In diesem Thema wird erläutert, wie die Millisekundenkomponente für Datum und Uhrzeit in eine formatierte Datums- und Uhrzeitzeichenfolge eingefügt wird.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>So zeigen Sie die Millisekundenkomponente eines DateTime-Werts an  
  
1.  Wenn Sie mit der Zeichenfolgendarstellung eines Datums arbeiten, konvertieren Sie sie mithilfe der statischen <xref:System.DateTime>-Methode oder <xref:System.DateTimeOffset>-Methode in einen <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>-Wert oder einen <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>-Wert.  
  
2.  Um die Zeichenfolgendarstellung einer Millisekundenkomponente für die Uhrzeit zu extrahieren, rufen Sie die <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>-Methode oder <xref:System.DateTimeOffset.ToString%2A>-Methode des Datums- oder Uhrzeitwerts auf und übergeben das benutzerdefinierte Formatmuster `fff` oder `FFF` alleine oder zusammen mit anderen benutzerdefinierten Formatbezeichnern als `format`-Parameter.  
  
## <a name="example"></a>Beispiel  
 Im Beispiel wird die Millisekundenkomponente von <xref:System.DateTime> und ein <xref:System.DateTimeOffset>-Wert für die Konsole angezeigt, und zwar sowohl alleine als auch als Bestandteil einer längeren Datums- und Uhrzeitzeichenfolge.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Das `fff`-Formatmuster schließt alle nachfolgenden Nullen (0) in den Millisekundenwert ein. Diese werden vom `FFF`-Formatmuster unterdrückt. Der Unterschied wird im folgenden Beispiel veranschaulicht.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Ein Problem beim Festlegen eines vollständigen benutzerdefinierten Formatbezeichners, der die Millisekundenkomponente für Datum und Uhrzeit umfasst, besteht darin, dass ein hartcodiertes Format festgelegt wird, das möglicherweise nicht der Anordnung der Uhrzeitelemente in der aktuellen Kultur der Anwendung entspricht. Die bessere Alternative besteht darin, eines der Anzeigemuster für Datum und Uhrzeit abzurufen, die durch das <xref:System.Globalization.DateTimeFormatInfo>-Objekt der aktuellen Kultur definiert sind, und es so zu bearbeiten, dass die Millisekunden berücksichtigt werden. Diese Herangehensweise wird im Beispiel ebenfalls verdeutlicht. Dabei wird das vollständige Datums- und Uhrzeitmuster der aktuellen Kultur aus der <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType>-Eigenschaft abgerufen und das benutzerdefinierte Muster `.ffff` nach dem Sekundenmuster eingefügt. Beachten Sie, dass im Beispiel ein regulärer Ausdruck verwendet wird, um diesen Vorgang in einem einzelnen Methodenaufruf auszuführen.  
  
 Sie können auch einen benutzerdefinierten Formatbezeichner verwenden, um einen anderen Sekundenbruchteil als Millisekunden anzuzeigen. Durch den benutzerdefinierten Formatbezeichner `f` oder `F` werden beispielsweise Zehntelsekunden, durch den benutzerdefinierten Formatbezeichner `ff` oder `FF` Hundertstelsekunden und durch den benutzerdefinierten Formatbezeichner `ffff` oder `FFFF` Zehntausendstelsekunden angezeigt. Bruchteile einer Millisekunde werden abgeschnitten und nicht in der zurückgegebenen Zeichenfolge gerundet. Diese Formatbezeichner werden im folgenden Beispiel verwendet.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Es besteht die Möglichkeit, sehr kleine Sekundenbruchteile wie Zehntausendstelsekunden oder Hunderttausendstelsekunden anzuzeigen. Diese Werte sind jedoch möglicherweise nicht sinnvoll. Die Genauigkeit der Datums- und Uhrzeitwerte hängt von der Auflösung der Systemuhr ab. Unter Windows NT 3.5 und höher und in [!INCLUDE[windowsver](../../../includes/windowsver-md.md)]-Betriebssystemen beträgt die Auflösung der Uhr etwa 10-15 Millisekunden.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Kompilieren Sie den Code über csc.exe oder vb.exe in der Befehlszeile. Um den Code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zu kompilieren, fügen Sie ihn in eine Projektvorlage für eine Konsolenanwendung ein.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
