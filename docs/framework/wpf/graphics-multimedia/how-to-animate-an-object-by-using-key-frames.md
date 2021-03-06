---
title: 'Gewusst wie: Animieren eines Objekts mithilfe von Keyframes'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f513cda540b3337f1510ee0c46419a12023bcb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Gewusst wie: Animieren eines Objekts mithilfe von Keyframes
In diesem Beispiel wird gezeigt, wie ein Objekt animiert wird in diesem Beispiel wird die <xref:System.Windows.Controls.Page.Background%2A> Eigenschaft von einem <xref:System.Windows.Controls.Page> mithilfe von Keyframes.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> Klasse zu animierende Farbe ändert, für die <xref:System.Windows.Controls.Page.Background%2A> Eigenschaft ein <xref:System.Windows.Controls.Page> Steuerelement. Die Animation Beispiel ändert sich zu einem anderen Hintergrundpinsel in regelmäßigen Abständen. Diese Animation verwendet die <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> Klasse, um drei verschiedene Keyframes zu erstellen. Die Animation verwendet Keyframes auf folgende Weise:  
  
1.  Eine Animation am Ende der ersten Sekunde eine Instanz von der <xref:System.Windows.Media.LinearGradientBrush> Klasse. In diesem Abschnitt des Beispiels gilt die Farbe des Hintergrunds ein lineares Farbverlaufs, damit die Farbe in Orange ändert sich in Rot über gelb wechselt.  
  
2.  Eine Animation am Ende der nächsten Sekunde eine Instanz von der <xref:System.Windows.Media.RadialGradientBrush> Klasse. In diesem Abschnitt des Beispiels wird die Farbe des Hintergrunds radialen Farbverlaufs betrifft, so, dass die Farbe von Weiß in Schwarz Blau übergeht.  
  
3.  Eine Animation am Ende der dritten Sekunde eine Instanz von der <xref:System.Windows.Media.DrawingBrush> Klasse. In diesem Abschnitt des Beispiels wird ein Schachbrettmuster im Hintergrund.  
  
4.  Die Animation wird erneut gestartet und auf unbestimmte Zeit wiederholt.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>ist die einzige Art des Keyframes, die mit der <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> Klasse. Keyframes wie <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> erstellen dabei plötzliche Änderungen in Werten, d. h., ändert sich die Farbe in diesem Beispiel plötzlich auftreten.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Das vollständige Beispiel finden Sie unter [Beispiel für eine KeyFrame-Animation](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Übersicht über Keyframe-Animationen](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Key-Frame How-to Topics (Themen zur Vorgehensweise zu Keyframes)](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
