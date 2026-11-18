# Plan de Pruebas — SauceDemo (Login, Inventario, Carrito y Checkout)

| | |
|---|---|
| **Versión** | 1.0 |
| **Fecha** | 18/11/2026 |
| **Autor** | Yair Uriel García González |

---

## 1. Objetivo

Validar el login, el inventario, el carrito y el checkout de SauceDemo y detectar defectos según el tipo de usuario.

## 2. Alcance

**Incluye:**

- Los 4 módulos: login, inventario, carrito y checkout.
- Los 6 usuarios de prueba que ofrece el sitio.
- Ordenamiento de productos y validación de campos del checkout.

**No incluye:**

- Pagos reales.
- Pruebas de carga o medición formal de rendimiento (con `performance_glitch_user` solo se observa el retraso).
- Pruebas en otros navegadores o en dispositivos móviles.

## 3. Requisitos bajo prueba

Como no existe un documento oficial de requisitos, se definieron los siguientes a partir del comportamiento esperado de una tienda en línea:

| ID | Requisito |
|---|---|
| REQ-001 | El usuario puede iniciar sesión con credenciales válidas y recibe un error con credenciales inválidas o bloqueadas. |
| REQ-002 | El inventario muestra los productos con imagen, nombre y precio correctos. |
| REQ-003 | El usuario puede ordenar los productos por nombre y por precio. |
| REQ-004 | El usuario puede agregar y quitar productos del carrito. |
| REQ-005 | El usuario puede completar una compra con datos válidos. |
| REQ-006 | El checkout valida los campos obligatorios. |

## 4. Tipos de prueba

Definiciones en el [glosario de qa-templates](https://github.com/YaUriGarcia/qa-templates/blob/main/docs/glosario.md).

- [x] **Smoke** — ejecución manual de los flujos básicos (login y carga del inventario)
- [x] **Functional** — ejecución manual de los casos de prueba
- [x] **Exploratory / Manual** — sesión exploratoria con `error_user` y `visual_user`

**No aplican:** Unit, Integration, API, Performance, Security, Accessibility, Compatibility, UAT y Regression (primer ciclo de ejecución).

## 5. Estrategia de ejecución

1. Ejecutar los 10 casos con `standard_user` para establecer el comportamiento base.
2. Repetir los casos clave con `problem_user` y comparar las diferencias.
3. Realizar una sesión exploratoria corta con `error_user` o `visual_user`.
4. Reportar cada defecto como un Issue de GitHub con evidencia.

## 6. Entorno

| Elemento | Detalle |
|---|---|
| **Aplicación** | SauceDemo (demo público) |
| **URL** | https://www.saucedemo.com |
| **Navegador** | Google Chrome v158.0.8127.37 |
| **Sistema operativo** | Windows 11 |
| **Propósito** | Ejecución de las pruebas manuales |

## 7. Datos y herramientas

- **Datos de prueba:** usuarios `standard_user`, `locked_out_user`, `problem_user`, `performance_glitch_user`, `error_user` y `visual_user`, todos con la contraseña pública `secret_sauce`.
- **CI/CD:** no aplica (pruebas manuales).
- **Gestión de casos y defectos:** archivos Markdown de este repositorio y GitHub Issues.

## 8. Criterios de entrada

- [x] El sitio está disponible y accesible
- [x] Casos de prueba redactados
- [x] Usuarios de prueba disponibles

## 9. Criterios de salida

- [ ] 100% de los casos de prioridad Alta ejecutados
- [ ] Todos los casos tienen un estado (Passed, Failed o Blocked)
- [ ] Cada fallo está documentado como Issue con evidencia
- [ ] Reporte de ejecución con recomendación de release

## 10. Riesgos

| Riesgo | Mitigación |
|---|---|
| El sitio demo puede cambiar o dejar de estar disponible durante la ejecución | Documentar la fecha de ejecución y tomar capturas como evidencia |
| No hay requisitos oficiales, y los definidos son una interpretación | Declararlo en este plan y basar cada caso en un requisito explícito |
| Algunos usuarios tienen fallos intencionales que pueden confundirse con errores de ejecución | Comparar siempre contra el comportamiento de `standard_user` |
| Se prueba solo en Chrome | Indicarlo en el alcance y en el reporte como cobertura no cubierta |

## 11. Entregables

- [Casos de prueba](../tests/casos-prueba.md)
- [Matriz de trazabilidad](../tests/matriz-trazabilidad.md)
- [Reporte de ejecución](../reportes/reporte-ejecucion.md)
- [Checklist de release](../docs/checklist-release.md)
- Defectos en los [Issues](../../../issues) del repositorio