---
title: ICorDebugValue::GetType (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc0dd03abc1adb8eeea76a1053fb4d58de4ecf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType (Método)
Obtiene el tipo primitivo de este objeto de "ICorDebugValue".  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pType`  
 [out] Un puntero a un valor de la enumeración "CorElementType" que indica el tipo del valor.  
  
## <a name="remarks"></a>Comentarios  
 Si el objeto es un tipo complejo de tiempo de ejecución, se puede examinar ese tipo a través de las subclases adecuadas de la `ICorDebugValue` interfaz. Por ejemplo, "ICorDebugObjectValue", que se hereda de `ICorDebugValue`, representa un tipo complejo.  
  
 El `GetType` y [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) cada uno de métodos devuelve información sobre el tipo de un valor. Ambos son reemplazados por los con elementos genéricos [ICorDebugValue2:: GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 
