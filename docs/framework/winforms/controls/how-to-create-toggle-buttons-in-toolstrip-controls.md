---
title: "Gewusst wie: Erstellen von Umschaltflächen in ToolStrip-Steuerelementen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Gewusst wie: Erstellen von Umschaltflächen in ToolStrip-Steuerelementen
Wenn ein Benutzer eine Umschaltfläche klickt, vertieft angezeigt, die abgesenkt beibehalten, bis der Benutzer erneut auf die Schaltfläche klickt.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>So erstellen eine ToolStripButton  
  
-   Verwenden Sie Code wie im folgenden Codebeispiel wird ein. Mit diesem Code wird davon ausgegangen, dass das Formular enthält ein <xref:System.Windows.Forms.ToolStrip> -Steuerelement, und dass seine <xref:System.Windows.Forms.ToolStrip.Items%2A> Auflistung enthält ein <xref:System.Windows.Forms.ToolStripButton> aufgerufen `toolStripButton1`. Außerdem wird angenommen, dass Sie einen Ereignishandler aufgerufen haben `toolStripButton1_CheckedChanged`.  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.ToolStripButton>  
 [Übersicht über das ToolStrip-Steuerelement](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
