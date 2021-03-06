---
title: 'Exemplarische Vorgehensweise: Datenfluss in einer Windows Forms-Anwendung verwenden'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Exemplarische Vorgehensweise: Datenfluss in einer Windows Forms-Anwendung verwenden
Dieses Dokument veranschaulicht, wie ein Netzwerk von Datenflussblöcken erstellt wird, die eine Bildverarbeitung in einer Windows Forms-Anwendung durchführen.  
  
 In diesem Beispiel werden Bilddateien aus dem angegebenen Ordner geladen, es wird ein zusammengesetztes Bild erstellt und das Ergebnis wird angezeigt. Im Beispiel wird das Datenflussmodell verwendet, um Bilder durch das Netzwerk zu leiten. Im Datenflussmodell kommunizieren unabhängige Komponenten eines Programms durch Senden von Nachrichten miteinander. Wenn eine Komponente eine Nachricht empfängt, führt sie eine Aktion aus und übergibt dann das Ergebnis an eine andere Komponente. Dies ist vergleichbar mit dem Ablaufsteuerungsmodell, in dem eine Anwendung Steuerungsstrukturen wie bedingte Anweisungen, Schleifen usw.verwendet, um die Reihenfolge der Vorgänge in einem Programm zu steuern.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Lesen Sie das Thema [Datenfluss](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md), bevor Sie mit dieser exemplarischen Vorgehensweise beginnen.  
  
> [!TIP]
>  Die TPL-Datenflussbibliothek (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>-Namespace) ist nicht in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] enthalten. Öffnen Sie zum Installieren des <xref:System.Threading.Tasks.Dataflow>-Namespace das Projekt in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wählen Sie im Menü "Projekt" die Option **NuGet-Pakete verwalten** aus, und suchen Sie online nach dem `Microsoft.Tpl.Dataflow` -Paket.  
 
  
## <a name="sections"></a>Abschnitte  
 Diese exemplarische Vorgehensweise enthält folgende Abschnitte:  
  
-   [Erstellen der Windows Forms-Anwendung](#winforms)  
  
-   [Erstellen des Datenflussnetzwerks](#network)  
  
-   [Verbinden des Datenflussnetzwerks mit der Benutzeroberfläche](#ui)  
  
-   [Vollständiges Beispiel](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Erstellen der Windows Forms-Anwendung  
 In diesem Abschnitt wird beschrieben, wie Sie die grundlegende Windows Forms-Anwendung erstellen und Steuerelemente zum Hauptformular hinzufügen.  
  
#### <a name="to-create-the-windows-forms-application"></a>Erstellen der Windows Forms-Anwendung  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ein [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]- oder Visual Basic-Projekt **Windows Forms-Anwendung**. In diesem Dokument hat das Projekt den Namen `CompositeImages`.  
  
2.  Im Formular-Designer für das Hauptformular "Form1.cs" ("Form1.vb" [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), Hinzufügen einer <xref:System.Windows.Forms.ToolStrip> Steuerelement.  
  
3.  Hinzufügen einer <xref:System.Windows.Forms.ToolStripButton> die Steuerung an die <xref:System.Windows.Forms.ToolStrip> Steuerelement. Festlegen der <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Eigenschaft <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> und die <xref:System.Windows.Forms.ToolStripItem.Text%2A> Eigenschaft, um **Ordner auswählen**.  
  
4.  Fügen Sie eine zweite <xref:System.Windows.Forms.ToolStripButton> die Steuerung an die <xref:System.Windows.Forms.ToolStrip> Steuerelement. Festlegen der <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Eigenschaft, um <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, die <xref:System.Windows.Forms.ToolStripItem.Text%2A> Eigenschaft, um **"Abbrechen"**, und die <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> Eigenschaft `False`.  
  
5.  Hinzufügen einer <xref:System.Windows.Forms.PictureBox> -Objekt, das Hauptformular. Legen Sie die <xref:System.Windows.Forms.Control.Dock%2A>-Eigenschaft auf <xref:System.Windows.Forms.DockStyle.Fill> fest.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Erstellen des Datenflussnetzwerks  
 Dieser Abschnitt beschreibt das Erstellen eines Datenflussnetzwerks, das Bildverarbeitung durchführt.  
  
#### <a name="to-create-the-dataflow-network"></a>Erstellen des Datenflussnetzwerks  
  
1.  Fügen Sie Ihrem Projekt einen Verweis auf „System.Threading.Tasks.Dataflow.dll“ hinzu.  
  
2.  Stellen Sie sicher, dass „Form1.cs“ („Form1.vb“ für [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) die folgenden `using`-Anweisungen (`Using` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) enthält:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Fügen Sie der `Form1`-Klasse die folgenden Datenmember hinzu:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Fügen Sie der `Form1`-Klasse die folgende `CreateImageProcessingNetwork`-Methode hinzu: Diese Methode erstellt das Bildverarbeitungsnetzwerk.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implementieren Sie die `LoadBitmaps`-Methode.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implementieren Sie die `CreateCompositeBitmap`-Methode.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  Die C#-Version von der `CreateCompositeBitmap` Methode werden Zeiger verwendet, ermöglichen die effiziente Verarbeitung von der <xref:System.Drawing.Bitmap?displayProperty=nameWithType> Objekte. Aus diesem Grund müssen Sie die Option **Unsicheren Code zulassen** in Ihrem Projekt aktivieren, um das [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md)-Schlüsselwort zu verwenden. Weitere Informationen zum Aktivieren von unsicheren Codes in einem [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] Projekt, finden Sie unter [Seite "Build", Projekt-Designer (c#)] https://msdn.microsoft.com/library/kb4wyys2).  
  
 In der folgenden Tabelle werden die Member des Netzwerks beschrieben.  
  
|Member|Typ|Beschreibung|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Akzeptiert einen Ordnerpfad als Eingabe und erzeugt eine Auflistung von <xref:System.Drawing.Bitmap> Objekte als Ausgabe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Nimmt eine Auflistung von <xref:System.Drawing.Bitmap> -Objekten als Eingabe und eine kombinierte Bitmap als Ausgabe erzeugt.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zeigt die zusammengesetzte Bitmap im Formular an.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zeigt ein Bild an, um anzugeben, dass der Vorgang abgebrochen wird, und ermöglicht es dem Benutzer, einen anderen Ordner auszuwählen.|  
  
 Um die Datenflussblöcke zu einem Netzwerk zu verbinden, in diesem Beispiel verwendet die <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Methode. Die <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Methode enthält eine überladene Version, die akzeptiert ein <xref:System.Predicate%601> Objekt, das bestimmt, ob der Zielblock akzeptiert oder eine Nachricht ablehnt. Dieser Filtermechanismus aktiviert Nachrichtenblöcke so, dass sie nur bestimmte Werte empfangen. In diesem Beispiel kann das Netzwerk auf zwei Arten verzweigen. Die Hauptverzweigung lädt die Bilder vom Datenträger, erstellt das zusammengesetzte Bild und zeigt das Bild auf dem Formular an. Die alternative Verzweigung bricht den aktuellen Vorgang ab. Die <xref:System.Predicate%601> Objekte ermöglichen die Datenflussblöcke entlang der main-Verzweigung in die andere Verzweigung ändern, indem bestimmte Nachrichten ablehnen. Wenn der Benutzer beispielsweise den Vorgang abbricht, erzeugt der Datenflussblock `createCompositeBitmap` `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) als Ausgabe. Der Datenflussblock `displayCompositeBitmap` lehnt `null`-Eingabewerte ab, und daher wird die Nachricht `operationCancelled` bereitgestellt. Der Datenflussblock `operationCancelled` akzeptiert alle Nachrichten und zeigt daher ein Bild an, um anzugeben, dass der Vorgang abgebrochen wird.  
  
 Die folgende Abbildung zeigt das Bildverarbeitungsnetzwerk.  
  
 ![Bildverarbeitungsnetzwerk](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Da sich die `displayCompositeBitmap`- und `operationCancelled`-Datenflussblöcke auf die Benutzeroberfläche auswirken, ist es wichtig, dass diese Aktionen im Benutzeroberflächenthread erfolgen. Geben Sie dazu während der Erstellung dieser Objekte ein <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> Objekt mit dem <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> -Eigenschaftensatz auf <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Die <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>-Methode erstellt ein <xref:System.Threading.Tasks.TaskScheduler>-Objekt, das Arbeiten im aktuellen Synchronisierungskontext durchführt. Da die `CreateImageProcessingNetwork`-Methode vom Handler der Schaltfläche **Ordner auswählen** aufgerufen wird, die im Benutzeroberflächenthread ausgeführt wird, werden die Aktionen für den `displayCompositeBitmap`- und den `operationCancelled`-Datenflussblock ebenfalls im Benutzeroberflächenthread ausgeführt.  
  
 In diesem Beispiel wird mithilfe einer freigegebenen Abbruchtokens anstatt durch die Einstellung der <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Eigenschaft da die <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Eigenschaft dauerhaft Dataflow-Ausführung melden Block abgebrochen. Dank eines Abbruchtokens kann dieses Beispiel das gleiche Datenflussnetzwerk mehrmals wiederverwenden, und zwar selbst dann, wenn der Benutzer einen oder mehrere Vorgänge abbricht. Ein Beispiel, verwendet <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> finden Sie in der Ausführung einen Datenflussblock Abbrechen, um [wie: Abbrechen einer Dataflow-Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Verbinden des Datenflussnetzwerks mit der Benutzeroberfläche  
 In diesem Abschnitt wird beschrieben, wie Sie das Datenflussnetzwerk mit der Benutzeroberfläche verbinden. Die Erstellung des zusammengesetzten Bildes und der Abbruch des Vorgangs werden über die Schaltflächen **Ordner auswählen** und **Abbrechen** initiiert. Wenn der Benutzer eine dieser Schaltflächen auswählt, wird die entsprechende Aktion auf asynchrone Weise initiiert.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Verbinden des Datenflussnetzwerks mit der Benutzeroberfläche  
  
1.  Erstellen Sie auf dem Formulardesigner für das Hauptformular einen Ereignishandler für das <xref:System.Windows.Forms.ToolStripItem.Click> -Ereignis für die **wählen Sie Ordner** Schaltfläche.  
  
2.  Implementieren der <xref:System.Windows.Forms.ToolStripItem.Click> -Ereignis für die **wählen Sie Ordner** Schaltfläche.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  Erstellen Sie auf dem Formulardesigner für das Hauptformular einen Ereignishandler für das <xref:System.Windows.Forms.ToolStripItem.Click> -Ereignis für die **"Abbrechen"** Schaltfläche.  
  
4.  Implementieren der <xref:System.Windows.Forms.ToolStripItem.Click> -Ereignis für die **"Abbrechen"** Schaltfläche.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Vollständiges Beispiel  
 Das folgende Beispiel enthält den vollständigen Code für diese exemplarische Vorgehensweise.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Die folgende Abbildung zeigt die normale Ausgabe für den gemeinsamen Ordner „\Sample Pictures\“.  
  
 ![Windows Forms-Anwendung](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Dataflow (Datenfluss)](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
