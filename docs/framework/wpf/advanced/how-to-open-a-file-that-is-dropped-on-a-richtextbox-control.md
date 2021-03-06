---
title: "Gewusst wie: Öffnen einer Datei, die auf einem RichTextBox-Steuerelement abgelegt ist"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dfb5f0f442b18159c18a6e5345f6757674fbb90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Gewusst wie: Öffnen einer Datei, die auf einem RichTextBox-Steuerelement abgelegt ist
In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, und <xref:System.Windows.Documents.FlowDocument> steuert den gesamten über integrierte Drag-and-Drop-Funktionalität verfügen. Die integrierte Funktion ermöglicht die Drag & Drop von Text innerhalb und zwischen den Steuerelementen. Es wird jedoch nicht aktiviert das Öffnen einer Datei durch das Löschen der Datei auf das Steuerelement. Diese Steuerelemente werden auch die Drag & Drop-Ereignisse als behandelt markiert. Standardmäßig können nicht Sie daher Ihren eigenen--Ereignishandler, um die Funktionalität zum Öffnen von abgelegten Dateien hinzufügen.  
  
 Verwenden Sie zum Hinzufügen zusätzlichen Schritt für Drag & Drop-Ereignisse in diesen Steuerelementen die <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> Methode, um die Ereignishandler für die Drag & Drop-Ereignisse hinzuzufügen. Legen Sie die `handledEventsToo` Parameter `true` fest, damit der angegebene Handler für ein Routingereignis aufgerufen werden, die bereits von einem anderen Element auf der Ereignisroute als behandelt markiert wurde.  
  
> [!TIP]
>  Sie können die integrierte Drag-and-Drop-Funktionalität der ersetzen <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, und <xref:System.Windows.Documents.FlowDocument> durch die Preview-Versionen der Drag & Drop-Ereignisse behandeln, und markieren die Vorschauereignisse als behandelt. Allerdings wird die integrierte Drag-and-Drop-Funktionalität deaktiviert, es wird nicht empfohlen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie das hinzuzufügende Handler für das <xref:System.Windows.DragDrop.DragOver> und <xref:System.Windows.DragDrop.Drop> Ereignisse auf einem <xref:System.Windows.Controls.RichTextBox>. Dieses Beispiel verwendet die <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> -Methode und legt die `handledEventsToo` Parameter `true` so, dass, obwohl die Ereignishandler aufgerufen werden die <xref:System.Windows.Controls.RichTextBox> diese Ereignisse als behandelt markiert. Der Code in den Ereignishandlern fügt Funktionen, um eine Textdatei öffnen, die auf abgelegt wird die <xref:System.Windows.Controls.RichTextBox>.  
  
 Ziehen Sie zum Testen dieses Beispiels eine Textdatei oder eine rich-Text-Format (RTF)-Datei von Windows-Explorer, um die <xref:System.Windows.Controls.RichTextBox>. Die Datei wird geöffnet, der <xref:System.Windows.Controls.RichTextBox>. Wenn Sie die UMSCHALT-vor dem Ablegen Taste der Datei, die Datei wird als nur-Text geöffnet werden.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
