---
title: 'Vorgehensweise: Deaktivieren sicherer Sitzungen auf einer WSFederationHttpBinding'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5fc5ddd1b84bf723901e449bf1bfda6a31ad1cea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Vorgehensweise: Deaktivieren sicherer Sitzungen auf einer WSFederationHttpBinding
Für einige Dienste sind möglicherweise verbundene Anmeldeinformationen notwendig, sichere Sitzungen werden jedoch nicht unterstützt. In diesem Fall müssen Sie die Funktion für sichere Sitzungen deaktivieren. Im Gegensatz zu den <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, wird die <xref:System.ServiceModel.WSFederationHttpBinding> Klasse bietet keine Möglichkeit, sichere Sitzungen deaktivieren bei der Kommunikation mit einem Dienst. Sie müssen vielmehr eine benutzerdefinierte Bindung erstellen, die die Einstellungen der sicheren Sitzung durch einen Bootstrap ersetzen.  
  
 In diesem Thema wird veranschaulicht, wie Sie das Bindungselement, das sich in einer <xref:System.ServiceModel.WSFederationHttpBinding> befindet, ändern können, um eine benutzerdefinierte Bindung zu erstellen. Das Ergebnis entspricht <xref:System.ServiceModel.WSFederationHttpBinding> mit Ausnahme der Tatsache, dass keine sicheren Sitzungen verwendet werden.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>So erstellen Sie eine benutzerdefinierte Verbundbindung ohne sichere Sitzung  
  
1.  Erstellen Sie eine Instanz der <xref:System.ServiceModel.WSFederationHttpBinding>-Klasse, sei es imperativ im Code oder durch das Laden einer Instanz aus der Konfigurationsdatei.  
  
2.  Klonen Sie <xref:System.ServiceModel.WSFederationHttpBinding> in <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Suchen Sie <xref:System.ServiceModel.Channels.SecurityBindingElement> in <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Suchen Sie <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Ersetzen Sie das ursprüngliche <xref:System.ServiceModel.Channels.SecurityBindingElement> durch das Bootstrap-Sicherheitsbindungselement aus <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Beispielcode wird eine benutzerdefinierte Verbundbindung ohne sichere Sitzung erstellt.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
  
-   Um das Codebeispiel zu kompilieren, erstellen Sie ein Projekt, das auf die System.ServiceModel.dll-Assembly verweist.  
  
## <a name="see-also"></a>Siehe auch  
 [Bindungen und Sicherheit](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
