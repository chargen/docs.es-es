---
title: 'Cómo: Analizar entradas manuscritas con sugerencias de análisis'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
ms.openlocfilehash: 74f8b3df5767888e8bca0d9f67e9c47630353fb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a>Cómo: Analizar entradas manuscritas con sugerencias de análisis
Un [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) proporciona una sugerencia para el [la clase System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) a la que está asociado.  La sugerencia se aplica al área especificado por el [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) propiedad de la [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) y proporciona contexto adicional para el analizador de tinta para mejorar la precisión del reconocimiento. El [la clase System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) aplica esta información contextual al analizar la entrada manuscrita obtenido desde dentro del área de la sugerencia.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo es una aplicación que usa varios [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objetos en un formulario que acepta datos proporcionados por tinta. La aplicación utiliza el [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) propiedad para proporcionar información de contexto para cada entrada en el formulario.  La aplicación utiliza el análisis en segundo plano para analizar la entrada manuscrita y borra el formato de todas las entradas manuscritas cinco segundos después de que el usuario detiene la adición de tinta.  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
