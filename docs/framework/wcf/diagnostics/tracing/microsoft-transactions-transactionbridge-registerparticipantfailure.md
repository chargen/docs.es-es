---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
El servicio de protocolo WS-AT no pudo registrar a un participante para un protocolo de control.  
  
## <a name="description"></a>Descripción  
 Se realiza el seguimiento si MSDTC detecta una solicitud de registro no válida. Esto puede deberse a varias solicitudes de registro de realización y errores internos.  
  
## <a name="troubleshooting"></a>Solución de problemas  
 No intente registrarse para la realización más de una vez.  Asimismo, inspeccione la cadena de estado dentro del mensaje de seguimiento para determinar si existe cualquier elemento al que se le puede realizar alguna acción.  
  
## <a name="see-also"></a>Vea también  
 [Traza](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uso del seguimiento para solucionar problemas de su aplicación](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administración y diagnóstico](../../../../../docs/framework/wcf/diagnostics/index.md)
