---
title: "Übersicht über die Benutzeroberflächenautomatisierungs-Anbieter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dc5cb5749bbfe06fd3a1bbe3537b28c7bbfa295d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-providers-overview"></a>Übersicht über die Benutzeroberflächenautomatisierungs-Anbieter
> [!NOTE]
>  Diese Dokumentation ist für .NET Framework-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Klassen verwenden möchten, die im <xref:System.Windows.Automation>-Namespace definiert sind. Aktuelle Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]finden Sie auf der Seite zur [Windows-Automatisierungs-API: UI-Automatisierung](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Benutzeroberflächenautomatisierungs-Anbieter ermöglichen Steuerelementen die Kommunikation mit Clientanwendungen für die Automatisierung der Benutzeroberfläche. Im Allgemeinen wird jedes Steuerelement oder anderes eindeutiges Element auf einer [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] von einem Anbieter dargestellt. Der Anbieter macht Informationen zum Element verfügbar und implementiert optional Steuerelementmuster, die es der Clientanwendung ermöglichen, mit dem Steuerelement zu interagieren.  
  
 Clientanwendungen müssen normalerweise nicht direkt mit Anbietern arbeiten. Die meisten Standardsteuerelemente in Anwendungen, die das [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]-, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]- oder [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] -Framework verwenden, werden automatisch für das [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -System verfügbar gemacht. Anwendungen, die benutzerdefinierte Steuerelemente implementieren, können auch [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Anbieter für diese Steuerelemente implementieren, und die Clientanwendungen müssen keine besonderen Schritte ausführen, um Zugriff auf diese zu erlangen.  
  
 Dieses Thema bietet einen Überblick darüber, wie Steuerelemententwickler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Anbieter implementieren, insbesondere für Steuerelemente in [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] - und [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] -Fenstern.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Anbietertypen  
 Benutzeroberflächenautomatisierungs-Anbieter werden in zwei Kategorien unterteilt: clientseitige und serverseitige Anbieter.  
  
### <a name="client-side-providers"></a>Clientseitige Anbieter  
 Clientseitige Anbieter werden von Benutzeroberflächenautomatisierungs-Clients für die Kommunikation mit einer Anwendung implementiert, die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nicht oder nicht vollständig unterstützt. Clientseitige Anbieter kommunizieren mit dem Server in der Regel durch Senden und Empfangen von [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] -Nachrichten über Prozessgrenzen hinweg.  
  
 Da Benutzeroberflächenautomatisierungs-Anbieter für Steuerelemente in [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]-, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]- oder [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] -Anwendungen im Rahmen des Betriebssystems bereitgestellt werden und Clientanwendungen selten eigene Anbieter implementieren müssen, werden sie in dieser Übersicht nicht weiter behandelt.  
  
### <a name="server-side-providers"></a>Serverseitiger Anbieter  
 Serverseitige Anbieter werden von benutzerdefinierten Steuerelementen oder durch Anwendungen implementiert, die auf einem anderen Benutzeroberflächenframework als [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]oder [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]basieren.  
  
 Serverseitige Anbieter kommunizieren mit Clientanwendungen über Prozessgrenzen hinweg, indem sie Schnittstellen für das [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Kernsystem verfügbar machen, das wiederum Anforderungen von Clients bereitstellt.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Konzepte für Benutzeroberflächenautomatisierungs-Anbieter  
 Dieser Abschnitt bietet kurze Erläuterungen zu einer Auswahl von Schlüsselkonzepten, die Sie kennen müssen, um Benutzeroberflächenautomatisierungs-Anbieter implementieren zu können.  
  
### <a name="elements"></a>Elements  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Elemente sind Bestandteile der [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , die für Benutzeroberflächenautomatisierungs-Clients angezeigt werden. Zu den entsprechenden Beispielen zählen Anwendungsfenster, Bereiche, Schaltflächen, QuickInfos, Listenfelder und Listenelemente.  
  
### <a name="navigation"></a>Navigation  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Elemente werden für Clients als [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur verfügbar gemacht. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] erstellt die Struktur durch Navigieren von einem Element zu einem anderen. Die Navigation wird von den Anbietern für jedes Element aktiviert, von denen jedes möglicherweise auf ein übergeordnetes, gleichgeordnetes oder untergeordnetes Element verweist.  
  
 Weitere Informationen zur Clientansicht der [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur finden Sie unter [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Ansichten  
 Ein Client kann die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur in drei hauptsächlichen Ansichten anzeigen, wie in der folgenden Tabelle dargestellt.  
  
|||  
|-|-|  
|Rohdatenansicht|Enthält alle Elemente.|  
|Steuerelementansicht|Enthält Elemente, die Steuerelemente sind.|  
|Inhaltsansicht|Enthält Elemente mit Inhalten.|  
  
 Weitere Informationen zu Clientansichten der [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur finden Sie unter [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Für die Definition eines Elements als Inhaltselement oder Steuerelement ist die Anbieterimplementierung zuständig. Steuerelemente können auch Inhaltselemente sein, aber alle Inhaltselemente sind auch Steuerelemente.  
  
### <a name="frameworks"></a>Frameworks  
 Ein Framework ist eine Komponente, die untergeordneten Steuerelemente, Treffertests und das Rendering in einem Bereich des Bildschirms verwaltet. Ein [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] -Fenster, das häufig als HWND bezeichnet wird, kann als Framework dienen, das mehrere [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Elemente enthält, z. B. eine Menüleiste, eine Statusleiste und Schaltflächen.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] -Containersteuerelemente, z. B. Listenfelder und Strukturansichten, werden als Frameworks betrachtet, da sie ihren eigenen Code zum Rendern der untergeordneten Elemente und zum Ausführen der zugehörigen Treffertests enthalten. Im Gegensatz dazu ist ein [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] -Listenfeld kein Framework, da Rendering und Treffertests vom enthaltenen [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] -Fenster übernommen werden.  
  
 Die [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] in einer Anwendung kann aus verschiedenen Frameworks bestehen. Beispielsweise kann ein HWND-Anwendungsfenster [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] enthalten, das wiederum eine Komponente enthält, z. B. ein Kombinationsfeld in einem HWND.  
  
### <a name="fragments"></a>Fragmente  
 Ein Fragment ist eine vollständige Unterstruktur von Elementen eines bestimmten Frameworks. Das Element im Stammknoten der Unterstruktur wird als Fragmentstamm bezeichnet. Ein Fragmentstamm besitzt kein übergeordnetes Element, wird aber innerhalb eines anderen Frameworks gehostet, in der Regel in einem [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] -Fenster (HWND).  
  
### <a name="hosts"></a>Hosts  
 Der Stammknoten jedes Fragments muss in einem Element gehostet werden, in der Regel in einem [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] -Fenster (HWND). Die Ausnahme stellt der Desktop dar, der in keinem anderen Element gehostet wird. Der Host eines benutzerdefinierten Steuerelements ist das HWND des Steuerelements selbst, nicht das Anwendungsfenster oder ein anderes Fenster, das möglicherweise Gruppen von Steuerelementen der obersten Ebene enthält.  
  
 Der Host eines Fragments spielt bei der Bereitstellung von [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Diensten eine wichtige Rolle. Er ermöglicht die Navigation zum Fragmentstamm und stellt einige Standardeigenschaften bereit, damit diese nicht vom benutzerdefinierten Anbieter implementiert werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Side UI Automation Provider Implementation](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)(Implementierung eines serverseitigen Benutzeroberflächenautomatisierungs-Anbieter)
