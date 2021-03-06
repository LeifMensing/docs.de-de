---
title: "Gewusst wie: Verfügbarmachen eines Vertrags für SOAP- und Webclients"
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
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f13ba797b0c0e5c8b0d1eef271baf62f920f199
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Gewusst wie: Verfügbarmachen eines Vertrags für SOAP- und Webclients
Standardmäßig macht [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Endpunkte nur für SOAP-Clients verfügbar. In [Vorgehensweise: Erstellen einer grundlegenden WCF-Web-HTTP-Diensts](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), ein Endpunkt für nicht-SOAP-Clients verfügbar gemacht wird. Manchmal möchten Sie jedoch einen Vertrag für beide Wege verfügbar machen, als Webendpunkt und als SOAP-Endpunkt. In diesem Thema wird ein Beispiel für diesen Vorgang gezeigt.  
  
### <a name="to-define-the-service-contract"></a>So definieren Sie den Dienstvertrag  
  
1.  Definieren Sie einen Dienstvertrag mit einer Schnittstelle, die mit den Attributen <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> und <xref:System.ServiceModel.Web.WebGetAttribute> gekennzeichnet ist, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Standardmäßig ordnet <xref:System.ServiceModel.Web.WebInvokeAttribute> dem Vorgang POST-Aufrufe zu. Sie können jedoch die Methode, die dem Vorgang zugeordnet werden soll, mit einem "method="-Parameter angeben. <xref:System.ServiceModel.Web.WebGetAttribute> besitzt keinen "method="-Parameter und ordnet dem Dienstvorgang nur GET-Aufrufe zu.  
  
2.  Implementieren Sie den Dienstvertrag, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>So hosten Sie den Dienst  
  
1.  Erstellen Sie ein <xref:System.ServiceModel.ServiceHost>-Element, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Fügen Sie einen <xref:System.ServiceModel.Description.ServiceEndpoint> mit <xref:System.ServiceModel.BasicHttpBinding> für den SOAP-Endpunkt hinzu, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Fügen Sie einen <xref:System.ServiceModel.Description.ServiceEndpoint> mit <xref:System.ServiceModel.WebHttpBinding> für einen Nicht-SOAP-Endpunkt hinzu und fügen Sie das <xref:System.ServiceModel.Description.WebHttpBehavior> dem Endpunkt hinzu, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Rufen Sie `Open()` für eine <xref:System.ServiceModel.ServiceHost>-Instanz hinzu, um den Diensthost zu öffnen, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>So rufen Sie Dienstvorgänge auf, die GET in Internet Explorer zugeordnet werden  
  
1.  Öffnen Sie Internet Explorer, und geben "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`", und drücken Sie die EINGABETASTE. Die URL enthält die Basisadresse des Diensts ("http://localhost:8000/"), die relative Adresse des Endpunkts (""), den aufzurufenden Dienstvorgang ("EchoWithGet") und ein Fragezeichen, gefolgt von einer Liste der benannten Parameter, die durch ein kaufmännisches Und (&) getrennt sind.  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>So rufen Sie Dienstvorgänge auf dem Webendpunkt im Code auf  
  
1.  Erstellen Sie eine Instanz von <xref:System.ServiceModel.Web.WebChannelFactory%601> in einem `using`-Block, wie im folgenden Code veranschaulicht.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` wird am Ende des `using`-Blocks automatisch für den Kanal aufgerufen.  
  
1.  Erstellen Sie den Kanal, und rufen Sie den Dienst auf, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>So rufen Sie Dienstvorgänge an dem SOAP-Endpunkt auf  
  
1.  Erstellen Sie eine Instanz von <xref:System.ServiceModel.ChannelFactory> in einem `using`-Block, wie im folgenden Code veranschaulicht.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Erstellen Sie den Kanal, und rufen Sie den Dienst auf, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>So schließen Sie den Diensthost  
  
1.  Schließen Sie den Diensthost, wie im folgenden Code gezeigt.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Beispiel  
 Unten folgt die vollständige Codeauflistung für dieses Thema.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Verweisen Sie beim Kompilieren der Datei Service.cs auf System.ServiceModel.dll und System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [WCF-Web-HTTP-Programmiermodell](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
