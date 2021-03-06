---
title: Información general sobre cuadros de diálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 110e42fea8d5586e471ae36ead46bed304cf9f48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-boxes-overview"></a>Información general sobre cuadros de diálogo
Aplicaciones independientes tienen normalmente una ventana principal que tanto muestra los datos principales en el que la aplicación funciona y expone la funcionalidad necesaria para procesar los datos a través de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mecanismos como barras de menús, barras de herramientas y barras de estado. Una aplicación no trivial también puede mostrar ventanas adicionales para realizar lo siguiente:  
  
-   Mostrar información específica a los usuarios.  
  
-   Recopilar información de los usuarios.  
  
-   Mostrar y recopilar información.  
  
 Estos tipos de ventanas se conocen como *cuadros de diálogo*, y hay dos tipos: modales y no modales.  
  
 A *modal* cuadro de diálogo se muestra una función cuando la función necesita datos adicionales de un usuario para continuar. Como la función depende del cuadro de diálogo modal para recopilar datos, el cuadro de diálogo modal también impide que un usuario active otras ventanas de la aplicación mientras permanece abierto. En la mayoría de los casos, un cuadro de diálogo modal permite a los usuarios señalar cuando haya terminado con el cuadro de diálogo modal presionando un **Aceptar** o **cancelar** botón. Al presionar la **Aceptar** botón indica que un usuario ha entrado en datos y desea que la función que se va a continuar con el procesamiento con esos datos. Al presionar la **cancelar** botón indica que un usuario desea detener la ejecución de la función. Los ejemplos más comunes de cuadros de diálogo modales se muestran para abrir, guardar e imprimir datos.  
  
 A *no modales* cuadro de diálogo, por otro lado, no impide que un usuario active otras ventanas mientras está abierto. Por ejemplo, si un usuario quiere buscar las repeticiones de una palabra determinada en un documento, a menudo una ventana principal abrirá un cuadro de diálogo para solicitar al usuario la palabra que está buscando. En cambio, como buscar una palabra no impide que un usuario edite el documento, el cuadro de diálogo no necesita ser modal. Un cuadro de diálogo no modal proporciona al menos un **cerrar** botón para cerrar el cuadro de diálogo y puede proporcionar botones adicionales para ejecutar funciones específicas, como un **Buscar siguiente** botón para buscar la siguiente de word que coincide con los criterios de búsqueda de una búsqueda de palabras.  
  
 Windows Presentation Foundation (WPF) le permite crear varios tipos de cuadros de diálogo, incluidos los cuadros de mensaje, cuadros de diálogo comunes y cuadros de diálogo personalizados. Este tema describe cada uno y el [Dialog Box Sample](http://go.microsoft.com/fwlink/?LinkID=159984) proporciona ejemplos de búsqueda de coincidencias.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Cuadros de mensaje  
 A *cuadro de mensaje* es un cuadro de diálogo que puede utilizarse para mostrar información textual y para permitir a los usuarios tomar decisiones con botones. En la siguiente figura se muestra un cuadro de mensaje que muestra información de texto, realiza una pregunta y proporciona tres botones al usuario para responderla.  
  
 ![Cuadro de diálogo Procesador de textos](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Para crear un cuadro de mensaje, utilice la <xref:System.Windows.MessageBox> clase. <xref:System.Windows.MessageBox> le permite configurar el texto de cuadro de mensaje, título, icono y botones, mediante código similar al siguiente.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Para mostrar un cuadro de mensaje, se llama a la `static` <xref:System.Windows.MessageBox.Show%2A> método, como se muestra en el código siguiente.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Cuando el código que muestra un cuadro de mensaje necesita detectar y procesar la decisión del usuario (qué botón se ha presionado), el código puede inspeccionar el resultado del cuadro de mensaje, como se muestra en el código siguiente.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Para obtener más información sobre el uso de cuadros de mensaje, consulte <xref:System.Windows.MessageBox>, [MessageBox Sample](http://go.microsoft.com/fwlink/?LinkID=160023), y [Dialog Box Sample](http://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Aunque <xref:System.Windows.MessageBox> puede ofrecer una experiencia de usuario del cuadro de diálogo simple, la ventaja de usar <xref:System.Windows.MessageBox> que es el único tipo de ventana que se puede mostrar las aplicaciones que se ejecutan en un recinto de seguridad de confianza parcial (vea [seguridad](../../../../docs/framework/wpf/security-wpf.md)), como [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 La mayoría de los cuadros de diálogo muestran y recopilan datos más complejos que el resultado de un cuadro de mensaje, incluidos texto, selección (casillas), selección mutuamente exclusiva (botón de selección) y selección de listas (cuadros de lista, cuadros combinados, cuadros de lista desplegable). En estos casos, Windows Presentation Foundation (WPF) proporciona varios cuadros de diálogo comunes y le permite crear sus propios cuadros de diálogo, aunque el uso de uno de ellos se limita a aplicaciones que se ejecutan con plena confianza.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Cuadros de diálogo comunes  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementa una variedad de cuadros de diálogo reutilizables que son comunes a todas las aplicaciones, incluidos los cuadros de diálogo para abrir y guardar archivos, e imprimir. Como estos cuadros de diálogo se implementan mediante el sistema operativo, pueden compartirse entre todas las aplicaciones que se ejecutan en el sistema operativo, que ayuda a la coherencia de la experiencia de usuario; cuando los usuarios están familiarizados con el uso de un cuadro de diálogo proporcionado por el sistema operativo en una aplicación, no necesitan obtener información sobre cómo usar ese cuadro de diálogo en otras aplicaciones. Dado que estos cuadros de diálogo están disponibles para todas las aplicaciones y dado que ayudan a proporcionar una experiencia de usuario coherente, se conocen como *cuadros de diálogo comunes*.  
  
 Windows Presentation Foundation (WPF) encapsula el archivo abierto, guarde el archivo y cuadros de diálogo comunes de impresión y los expone como clases administradas para su uso en las aplicaciones independientes. En este tema se proporciona una breve introducción de cada uno.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Cuadro de diálogo Abrir archivo  
 El cuadro de diálogo Abrir archivo, que se muestra en la siguiente figura, se usa por la función de apertura de archivos para recuperar el nombre de un archivo que se va a abrir.  
  
 ![Cuadro de diálogo Abrir](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 El cuadro de diálogo Abrir archivo común se implementa como el <xref:Microsoft.Win32.OpenFileDialog> clase y se encuentra en la <xref:Microsoft.Win32> espacio de nombres. En el siguiente código se muestra cómo crear, configurar y mostrar uno, y cómo procesar el resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Para obtener más información sobre el cuadro de diálogo Abrir archivo, consulte <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> puede usarse para recuperar de manera segura los nombres de archivo por aplicaciones que se ejecutan con confianza parcial (vea [seguridad](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Cuadro de diálogo Guardar archivo  
 El cuadro de diálogo Guardar archivo, que se muestra en la siguiente figura, se usa por la función de guardado de archivos para recuperar el nombre de un archivo que se va a guardar.  
  
 ![Cuadro de diálogo Guardar como](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Common Guardar cuadro de diálogo de archivo se implementa como el <xref:Microsoft.Win32.SaveFileDialog> clase y se encuentra en la <xref:Microsoft.Win32> espacio de nombres. En el siguiente código se muestra cómo crear, configurar y mostrar uno, y cómo procesar el resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Para obtener más información sobre la operación de guardar archivo de cuadro de diálogo, consulte <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Cuadro de diálogo Imprimir  
 El cuadro de diálogo Imprimir, que se muestra en la siguiente figura, se usa por la función de impresión para elegir y configurar la impresora con la que el usuario quiere imprimir los datos.  
  
 ![Cuadro de diálogo Imprimir](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 El cuadro de diálogo de impresión común se implementa como el <xref:System.Windows.Controls.PrintDialog> clase y se encuentra en la <xref:System.Windows.Controls> espacio de nombres. En el siguiente código se muestra cómo crear, configurar y mostrar uno.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Para obtener más información sobre el cuadro de diálogo de impresión, consulte <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Para una explicación detallada de la impresión en [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [resumen de impresión](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Cuadros de diálogo personalizados  
 Aunque los cuadros de diálogo comunes son útiles, y deben usarse cuando sea posible, no admiten los requisitos de los cuadros de diálogo específicos de dominio. En estos casos, necesita crear sus propios cuadros de diálogo. Como veremos, un cuadro de diálogo es una ventana con comportamientos especiales. <xref:System.Windows.Window> implementa esos comportamientos y, por lo tanto, utilice <xref:System.Windows.Window> para crear cuadros de diálogo modales y no modales personalizados.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Crear un cuadro de diálogo modal personalizado  
 Este tema muestra cómo usar <xref:System.Windows.Window> para crear una implementación de cuadro de diálogo modal típico, utilizando el `Margins` cuadro de diálogo como ejemplo (vea [Dialog Box Sample](http://go.microsoft.com/fwlink/?LinkID=159984)). El `Margins` cuadro de diálogo se muestra en la ilustración siguiente.  
  
 ![Cuadro de diálogo Márgenes](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configurar un cuadro de diálogo modal  
 La interfaz de usuario de un cuadro de diálogo típico incluye lo siguiente:  
  
-   Los distintos controles que se necesitan para recopilar los datos deseados.  
  
-   Mostrar un **Aceptar** botón que los usuarios, haga clic en para cerrar el cuadro de diálogo, vuelva a la función y continuar con el procesamiento.  
  
-   Mostrar un **cancelar** botón que los usuarios hacen clic para cerrar el cuadro de diálogo y detener la función de procesamiento posterior.  
  
-   Mostrar un **cerrar** botón en la barra de título.  
  
-   Mostrar un icono.  
  
-   Mostrar **minimizar**, **maximizar**, y **restaurar** botones.  
  
-   Mostrar un **System** menú para minimizar, maximizar, restaurar y cerrar el cuadro de diálogo.  
  
-   Apertura encima y en el centro de la ventana que ha abierto el cuadro de diálogo.  
  
-   Los cuadros de diálogo deben ser redimensionables donde sea posible, para evitar que el cuadro de diálogo sea demasiado pequeño y para proporcionar al usuario un tamaño predeterminado útil, necesita establecer las dimensiones mínimas y predeterminadas respectivamente.  
  
-   Al presionar la tecla ESC debe configurarse como un método abreviado de teclado que provoca la **cancelar** botón presionado. Esto se logra estableciendo la <xref:System.Windows.Controls.Button.IsCancel%2A> propiedad de la **cancelar** botón a `true`.  
  
-   Al presionar la tecla ENTRAR (o retorno) debe configurarse como un método abreviado de teclado que provoca la **Aceptar** botón presionado. Esto se logra estableciendo la <xref:System.Windows.Controls.Button.IsDefault%2A> propiedad de la **Aceptar** botón `true`.  
  
 El siguiente código muestra esta configuración.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 La experiencia de usuario de un cuadro de diálogo también se extiende a la barra de menús de la ventana que abre el cuadro de diálogo. Cuando un elemento de menú ejecuta una función que requiere interacción del usuario mediante un cuadro de diálogo antes de que la función pueda continuar, el elemento de menú de la función tendrá puntos suspensivos en su encabezado, como se muestra aquí.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Cuando un elemento de menú ejecuta una función que muestra un cuadro de diálogo que no necesita interacción del usuario, como un cuadro de diálogo Acerca de, no se necesitan los puntos suspensivos.  
  
#### <a name="opening-a-modal-dialog-box"></a>Abrir un cuadro de diálogo modal  
 Un cuadro de diálogo se muestra normalmente como el resultado de un usuario que selecciona un elemento de menú para realizar una función específica de dominio, como establecer los márgenes de un documento en un procesador de textos. Mostrar una ventana como un cuadro de diálogo es similar a mostrar una ventana normal, aunque necesita una configuración específica de cuadro de diálogo adicional. El proceso completo de crear instancias, configurar y abrir un cuadro de diálogo se muestra en el código siguiente.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Aquí, el código está pasando información predeterminada (los márgenes actuales) al cuadro de diálogo. También está estableciendo la <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> propiedad con una referencia a la ventana que se muestra el cuadro de diálogo. En general, siempre debe establecerse el propietario de un cuadro de diálogo para proporcionar comportamientos relacionados con el estado de ventana que son comunes a todos los cuadros de diálogo (vea [Introducción a WPF Windows](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) para obtener más información).  
  
> [!NOTE]
>  Debe proporcionar un propietario para admitir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automatización para los cuadros de diálogo (vea [información general sobre la automatización de interfaz de usuario](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 Después de configura el cuadro de diálogo, se mostrará modalmente llamando a la <xref:System.Windows.Window.ShowDialog%2A> método.  
  
#### <a name="validating-user-provided-data"></a>Validar los datos proporcionados por el usuario  
 Cuando un cuadro de diálogo se abre y el usuario proporciona los datos necesarios, un cuadro de diálogo es responsable de garantizar que los datos proporcionados sean válidos por los motivos siguientes:  
  
-   Desde una perspectiva de seguridad, se deben validar todas las entradas.  
  
-   Desde una perspectiva específica de dominio, la validación de datos impide que los datos incorrectos se procesen por el código, que puede provocar excepciones potencialmente.  
  
-   Desde una perspectiva de experiencia de usuario, un cuadro de diálogo puede ayudar a los usuarios a mostrarles qué datos de los que han especificado no son válidos.  
  
-   Desde una perspectiva de rendimiento, la validación de datos en una aplicación de varios niveles puede reducir el número de recorridos de ida y vuelta entre los niveles de aplicación y cliente, especialmente cuando la aplicación está formada por servicios Web o bases de datos basadas en servidor.  
  
 Para validar un control enlazado en [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], debe definir una regla de validación y asociarlo con el enlace. Una regla de validación es una clase personalizada que deriva de <xref:System.Windows.Controls.ValidationRule>. En el ejemplo siguiente se muestra una regla de validación, `MarginValidationRule`, que comprueba que un valor enlazado es un <xref:System.Double> y está dentro del intervalo especificado.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 En este código, se implementa la lógica de validación de una regla de validación invalidando el <xref:System.Windows.Controls.ValidationRule.Validate%2A> método, que valida los datos y devuelve un apropiado <xref:System.Windows.Controls.ValidationResult>.  
  
 Para asociar la regla de validación con el control enlazado, use el siguiente marcado.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Una vez que está asociada, la regla de validación [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] lo aplicará automáticamente cuando se escriben datos en el control enlazado. Cuando un control contiene datos no válidos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mostrará un borde rojo alrededor del control no válido, tal como se muestra en la ilustración siguiente.  
  
 ![Margen izquierdo no válido](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] no restringe un usuario al control no válido hasta que haya especificado los datos válidos. Este es un buen comportamiento para un cuadro de diálogo; un usuario debe poder navegar libremente por los controles de un cuadro de diálogo sean los datos válidos o no. Sin embargo, esto significa que un usuario puede escribir datos no válidos y presione la **Aceptar** botón. Por este motivo, el código también debe validar todos los controles en un cuadro de diálogo cuadro cuando el **Aceptar** se presiona el botón controlando el <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Este código enumera todos los objetos de dependencia en una ventana y, si alguna no son válido (tal como lo devuelve <xref:System.Windows.Controls.Validation.GetHasError%2A>, el control no válido obtiene el foco, el `IsValid` método `false`, y la ventana se considera no válida.  
  
 Una vez que un cuadro de diálogo es válido, puede cerrarse y devolverse de manera segura. Como parte del proceso de retorno, necesita devolver un resultado a la función de llamada.  
  
#### <a name="setting-the-modal-dialog-result"></a>Establecer el resultado del cuadro de diálogo modal  
 Abrir un cuadro de diálogo mediante <xref:System.Windows.Window.ShowDialog%2A> es fundamentalmente como llamar a un método: el código que abre el cuadro de diálogo mediante <xref:System.Windows.Window.ShowDialog%2A> espera hasta que <xref:System.Windows.Window.ShowDialog%2A> devuelve. Cuando <xref:System.Windows.Window.ShowDialog%2A> devuelve, el código que lo llamó necesita decidir si continuar procesando o detener el procesamiento, dependiendo de si el usuario presionó la **Aceptar** botón o **cancelar** botón. Para facilitar esta decisión, el cuadro de diálogo debe devolver la elección del usuario como un <xref:System.Boolean> valor que se devuelve desde el <xref:System.Windows.Window.ShowDialog%2A> método.  
  
 Cuando el **Aceptar** se hace clic en el botón, <xref:System.Windows.Window.ShowDialog%2A> debe devolver `true`. Esto se logra estableciendo la <xref:System.Windows.Window.DialogResult%2A> propiedad del cuadro de diálogo cuadro cuando el **Aceptar** se hace clic en el botón.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Tenga en cuenta esa configuración el <xref:System.Windows.Window.DialogResult%2A> propiedad también hace que la ventana para cerrar automáticamente, lo que elimina la necesidad de llamar explícitamente a <xref:System.Windows.Window.Close%2A>.  
  
 Cuando el **cancelar** se hace clic en el botón, <xref:System.Windows.Window.ShowDialog%2A> debe devolver `false`, que requiere la configuración de la <xref:System.Windows.Window.DialogResult%2A> propiedad.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Cuando un botón <xref:System.Windows.Controls.Button.IsCancel%2A> propiedad está establecida en `true` y el usuario presiona cualquiera el **cancelar** botón o la tecla ESC, <xref:System.Windows.Window.DialogResult%2A> se establece automáticamente en `false`. El siguiente marcado tiene el mismo efecto que el código anterior, sin necesidad de controlar la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Devuelve automáticamente un cuadro de diálogo `false` cuando un usuario presiona la **cerrar** situado en la barra de título o elige el **cerrar** elemento de menú de la **System** menú.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Procesar los datos devueltos de un cuadro de diálogo modal  
 Cuando <xref:System.Windows.Window.DialogResult%2A> está establecido en un cuadro de diálogo, la función que lo abrió puede obtener el resultado del cuadro de diálogo inspeccionando el <xref:System.Windows.Window.DialogResult%2A> propiedad cuando <xref:System.Windows.Window.ShowDialog%2A> devuelve.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Si el resultado del diálogo es `true`, la función que utiliza como una indicación para recuperar y procesar los datos proporcionados por el usuario.  
  
> [!NOTE]
>  Después de <xref:System.Windows.Window.ShowDialog%2A> ha devuelto, no se puede volver a abrir un cuadro de diálogo. En su lugar, necesita crear una instancia nueva.  
  
 Si el resultado del diálogo es `false`, la función debe finalizar el procesamiento correctamente.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Crear un cuadro de diálogo no modal personalizado  
 Un cuadro de diálogo no modal, como el cuadro de diálogo Buscar que se muestra en la figura siguiente, tiene el mismo aspecto fundamental que el cuadro de diálogo modal.  
  
 ![Cuadro de diálogo Buscar](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 En cambio, el comportamiento es un poco diferente, como se describe en las secciones siguientes.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Abrir un cuadro de diálogo no modal  
 Se abre un cuadro de diálogo no modal mediante una llamada a la <xref:System.Windows.Window.Show%2A> método.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 A diferencia de <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> devuelve inmediatamente. Por consiguiente, la ventana de llamada no puede indicar cuándo se cierra el cuadro de diálogo no modal y, por lo tanto, no sabe cuándo comprobar el resultado de un cuadro de diálogo u obtener los datos de este para un procesamiento posterior. En su lugar, el cuadro de diálogo necesita crear una manera alternativa de devolver los datos a la ventana de llamada para su procesamiento.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Procesar los datos devueltos de un cuadro de diálogo no modal  
 En este ejemplo, el `FindDialogBox` puede devolver uno o más resultados de búsqueda a la ventana principal, según el texto que se va a buscar sin ninguna frecuencia concreta. Al igual que un cuadro de diálogo modal, un cuadro de diálogo no modal puede devolver resultados mediante propiedades. En cambio, la ventana que tiene el cuadro de diálogo necesita saber cuándo comprobar esas propiedades. Una manera de habilitar esto es que el cuadro de diálogo implemente un evento que se genera cuando se detecta texto. `FindDialogBox` implementa el `TextFoundEvent` para este propósito, que primero requiere un delegado.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Mediante el `TextFoundEventHandler` delegar, `FindDialogBox` implementa el `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 Por lo tanto, `Find` puede generar el evento cuando se encuentra un resultado de búsqueda.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Después, la ventana propietaria necesita registrar y controlar este evento.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Cerrar un cuadro de diálogo no modal  
 Dado que <xref:System.Windows.Window.DialogResult%2A> no es necesario se establece, se puede cerrar un cuadro de diálogo no modal mediante sistema proporcionan mecanismos, incluidos los siguientes:  
  
-   Al hacer clic en el **cerrar** botón en la barra de título.  
  
-   Presionar ALT+F4.  
  
-   Elegir **cerrar** desde el **System** menú.  
  
 Como alternativa, puede llamar su código <xref:System.Windows.Window.Close%2A> cuando el **cerrar** se hace clic en el botón.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el control Popup](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Ejemplo de cuadro de diálogo](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [ColorPicker Custom Control Sample](http://go.microsoft.com/fwlink/?LinkID=159977) (Ejemplo de control personalizado de selector de colores)
