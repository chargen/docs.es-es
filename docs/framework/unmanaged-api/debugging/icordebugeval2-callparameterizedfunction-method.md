---
title: ICorDebugEval2::CallParameterizedFunction (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction (Método)
Configura una llamada a la instancia de ICorDebugFunction especificado, que se puede anidar dentro de una clase cuyo constructor toma <xref:System.Type> parámetros usados, ni puede propio <xref:System.Type> parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFunction`  
 [in] Un puntero a un `ICorDebugFunction` objeto que representa la función que se llamará.  
  
 `nTypeArgs`  
 [in] El número de argumentos que la función toma.  
  
 `ppTypeArgs`  
 [in] Una matriz de punteros, cada uno de los cuales señala a un objeto ICorDebugType que representa un argumento de función.  
  
 `nArgs`  
 [in] El número de valores pasados en la función.  
  
 `ppArgs`  
 [in] Una matriz de punteros, cada uno de los cuales señala a un objeto ICorDebugValue que representa un valor pasado en un argumento de función.  
  
## <a name="remarks"></a>Comentarios  
 `CallParameterizedFunction` es similar a [ICorDebugEval:: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) salvo que la función puede estar dentro de una clase con parámetros de tipo, puede tomar por sí misma parámetros de tipo, o ambos. Los argumentos de tipo se deberían proporcionar primero para la clase y, a continuación, para la función.  
  
 Si la función está en un dominio de aplicación diferente, se producirá una transición. Sin embargo, todos los argumentos de tipo y el valor deben estar en el dominio de aplicación de destino.  
  
 Evaluación de la función puede realizarse solo en escenarios limitados. Si `CallParameterizedFunction` o `ICorDebugEval::CallFunction` se produce un error, el HRESULT devuelto indicará el motivo más general posible error.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
