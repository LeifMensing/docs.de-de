---
title: "Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Größenänderung von Windows Forms"
  - "Windows Forms, Größenänderung"
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Windows Forms
Sie können die Größe eines Windows Forms auf verschiedene Weise angeben.  Sie können die Höhe und Breite des Formulars programmgesteuert ändern, indem Sie einen neuen Wert für die <xref:System.Windows.Forms.Form.Size%2A>\-Eigenschaft festlegen oder die <xref:System.Windows.Forms.Control.Height%2A>\- oder die <xref:System.Windows.Forms.Control.Width%2A>\-Eigenschaft einzeln anpassen.  Wenn Sie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] verwenden, können Sie die Größe mit dem Windows Forms\-Designer ändern.  Weitere Informationen finden Sie unter [Gewusst wie: Ändern der Größe von Windows Forms mithilfe des Designers](http://msdn.microsoft.com/library/37k2zkwx%20\(v=vs.110\)).  
  
### So ändern Sie die Größe eines Formulars programmgesteuert  
  
-   Sie können die Größe eines Formulars zur Laufzeit definieren, indem Sie die <xref:System.Windows.Forms.Form.Size%2A>\-Eigenschaft des Formulars festlegen.  
  
     Im folgenden Codebeispiel wird die Formulargröße auf 100 x 100 Pixel festgelegt.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### So ändern Sie Breite und Höhe des Formulars programmgesteuert  
  
-   Nachdem <xref:System.Windows.Forms.Form.Size%2A> definiert ist, ändern Sie entweder die Formularhöhe oder \-breite über die <xref:System.Windows.Forms.Control.Width%2A>\- oder die <xref:System.Windows.Forms.Control.Height%2A>\-Eigenschaft.  
  
     Im folgenden Codebeispiel wird die Breite des Formulars ab dem linken Formularrand auf 300 Pixel festgelegt, während die Höhe konstant bleibt.  
  
    ```vb  
    Form1.Width = 300  
  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     \- oder \-  
  
     Ändern Sie <xref:System.Drawing.Size.Width%2A> oder <xref:System.Drawing.Size.Height%2A>, indem Sie die <xref:System.Windows.Forms.Form.Size%2A>\-Eigenschaft festlegen.  
  
     Wie Sie jedoch dem folgenden Codebeispiel entnehmen können, ist diese Vorgehensweise komplizierter als das Festlegen der <xref:System.Windows.Forms.Control.Width%2A>\- oder der <xref:System.Windows.Forms.Control.Height%2A>\-Eigenschaft.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### So ändern Sie Formulargröße programmgesteuert in Schritten  
  
-   Um das Formular zu vergrößern, legen Sie die <xref:System.Drawing.Size.Width%2A>\- und die <xref:System.Drawing.Size.Height%2A>\-Eigenschaft fest.  
  
     Im folgenden Codebeispiel wird das Formular mit einer Breite angezeigt, die um 200 Pixel größer ist als die aktuelle Einstellung.  
  
    ```vb  
    Form1.Width += 200  
  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  Sie sollten immer die <xref:System.Drawing.Size.Height%2A>\- oder die <xref:System.Drawing.Size.Width%2A>\-Eigenschaft verwenden, um ein Maß eines Formulars zu ändern, es sei denn, Sie legen das Höhen\- und das Breitenmaß gleichzeitig fest, indem Sie die <xref:System.Windows.Forms.Form.Size%2A>\-Eigenschaft auf eine neue <xref:System.Drawing.Size>\-Struktur festlegen.  Die <xref:System.Windows.Forms.Form.Size%2A>\-Eigenschaft gibt eine <xref:System.Drawing.Size>\-Struktur zurück, die ein Werttyp ist.  Sie können der Eigenschaft eines Werttyps keinen neuen Wert zuweisen.  Daher kann das folgende Codebeispiel nicht kompiliert werden.  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## Siehe auch  
 [Erste Schritte mit Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)   
 [Erweitern von Windows Forms\-Anwendungen](../../../docs/framework/winforms/advanced/index.md)