---
title: IHostSyncManager::SetCLRSyncManager (Método)
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef7866d912951972ec9c66efccca671c3787da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a>IHostSyncManager::SetCLRSyncManager (Método)
Establece el [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instancia asociada con el actual [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instancia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pManager`  
 [in] Un puntero a un `ICLRSyncManager` instancia proporcionada por common language runtime (CLR).  
  
## <a name="return-value"></a>Valor devuelto  
  
|HRESULT|Descripción|  
|-------------|-----------------|  
|S_OK|`SetCLRSyncManager` se devolvió correctamente.|  
|HOST_E_CLRNOTAVAILABLE|El CLR no se han cargado en un proceso o el CLR está en un estado en el que no se puede ejecutar código administrado o procesar la llamada correctamente.|  
|HOST_E_TIMEOUT|La llamada agotó el tiempo de espera.|  
|HOST_E_NOT_OWNER|El llamador no posee el bloqueo.|  
|HOST_E_ABANDONED|Se canceló un evento mientras un subproceso bloqueado o fibra esperó en él.|  
|E_FAIL|Se ha producido un error catastrófico desconocido. Cuando un método devuelve E_FAIL, CLR ya no es utilizable dentro del proceso. Las llamadas posteriores a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentarios  
 Para facilitar la comunicación entre el host y CLR, las interfaces de hospedaje generalmente vienen en parejas. Un miembro del par es implementado por el host y el CLR implementa el otro miembro. Como una implementación del host, el `IHostSyncManager` interfaz se corresponde con el `ICLRSyncManager` interfaz implementada por CLR. CLR llama `SetCLRSyncManager` para proporcionar un `ICLRSyncManager` instancia para el host se asocie con el actual `IHostSyncManager` instancia.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE.h  
  
 **Biblioteca:** incluye como recurso en MSCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICLRSyncManager (interfaz)](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager (interfaz)](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
