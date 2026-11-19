# Matriz de Trazabilidad — SauceDemo

| | |
|---|---|
| **Versión** | 1.0 |
| **Fecha** | 19/11/2026 |
| **Autor** | Yair Uriel García González |

Relaciona cada requisito con los casos que lo cubren y con los defectos encontrados. Sirve para demostrar la **cobertura** y detectar requisitos sin pruebas. Los casos están en [`casos-prueba.md`](casos-prueba.md).

## Matriz

| Requisito | Descripción | Casos de prueba | Ejecuciones adicionales (`problem_user`) | Estado de ejecución | Bugs asociados |
|---|---|---|---|---|---|
| REQ-001 | El usuario puede iniciar sesión con credenciales válidas y recibe un error con credenciales inválidas o bloqueadas. | TC-LGN-001, TC-LGN-002, TC-LGN-003, TC-LGN-004, TC-LGN-005, TC-LGN-006 | — | Pendiente | — |
| REQ-002 | El inventario muestra los productos con imagen, nombre y precio correctos. | TC-INV-001 | TC-INV-001 | Pendiente | — |
| REQ-003 | El usuario puede ordenar los productos por nombre y por precio. | TC-INV-002, TC-INV-003 | TC-INV-002 | Pendiente | — |
| REQ-004 | El usuario puede agregar y quitar productos del carrito. | TC-CAR-001, TC-CAR-002 | TC-CAR-001, TC-CAR-002 | Pendiente | — |
| REQ-005 | El usuario puede completar una compra con datos válidos. | TC-CHK-001 | TC-CHK-001 | Pendiente | — |
| REQ-006 | El checkout valida los campos obligatorios. | TC-CHK-002, TC-CHK-003, TC-CHK-004 | TC-CHK-002 | Pendiente | — |

**Estado de ejecución por requisito:** *Passed* (todos sus casos pasaron), *Failed* (al menos un caso falló), *Blocked* (algún caso no pudo ejecutarse) o *Pendiente* (sin ejecutar).

## Casos por requisito

| Requisito | Casos base | Ejecuciones adicionales |
|---|:---:|:---:|
| REQ-001 | 6 | 0 |
| REQ-002 | 1 | 1 |
| REQ-003 | 2 | 1 |
| REQ-004 | 2 | 2 |
| REQ-005 | 1 | 1 |
| REQ-006 | 3 | 1 |
| **Total** | **15** | **6** |

## Resumen de cobertura

| Métrica | Valor |
|---|---|
| Requisitos totales | 6 |
| Requisitos con al menos un caso | 6 |
| **% de cobertura de requisitos** | **100%** |
| Requisitos sin casos (gap) | 0 |
| Casos base ejecutados | 0 de 15 |
| Ejecuciones adicionales realizadas | 0 de 6 |

> **Nota:** la cobertura de requisitos mide que cada requisito tenga al menos un caso, no la profundidad de las pruebas. REQ-002 y REQ-005 tienen un solo caso base, y por eso se repiten con `problem_user`.

## Cómo actualizarla

1. Al ejecutar cada caso en [`casos-prueba.md`](casos-prueba.md), completa su estado.
2. Cambia el **Estado de ejecución** del requisito según la regla de arriba.
3. Anota los IDs de los bugs (`BUG-XXX-NNN`) en **Bugs asociados**.
4. Actualiza el resumen de cobertura al terminar el ciclo.