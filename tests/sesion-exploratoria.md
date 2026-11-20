# Sesión de Pruebas Exploratorias — SauceDemo

| | |
|---|---|
| **ID de sesión** | EXP-CHK-001 |
| **Fecha** | 20/11/2026 |
| **Tester** | Yair Uriel García González |
| **Entorno / Build** | https://www.saucedemo.com · Google Chrome v158.0.8127.37 · [sistema operativo] |
| **Usuarios utilizados** | `error_user` (principal) y `standard_user` (comparación) |
| **Duración (timebox)** | 10 min |

---

## 1. Charter (misión)

> Explorar el flujo de compra con `error_user` para descubrir fallos al agregar productos o finalizar la compra.

## 2. Alcance y fuera de alcance

- **Dentro:** agregar productos, carrito y finalizar una compra. Se registraron como desvíos los hallazgos de ordenamiento y de cierre de sesión que surgieron durante el flujo.
- **Fuera:** validación de login y de campos obligatorios, que se cubren con los casos formales de [`casos-prueba.md`](casos-prueba.md).

## 3. Heurísticas o ideas de prueba

- [ ] Valores límite y datos inválidos *(no explorado en esta sesión)*
- [x] Distintos roles y permisos *(se comparó `error_user` con `standard_user`)*
- [x] Interrumpir el flujo *(se cerró sesión con productos en el carrito)*
- [ ] Distintos dispositivos / navegadores *(fuera de alcance: solo Chrome de escritorio)*
- [ ] Conexión lenta o caída de red *(fuera de alcance: requiere herramientas de limitación de red)*
- [ ] Concurrencia *(fuera de alcance: SauceDemo es un entorno de práctica)*

## 4. Notas de la sesión

| Hora | Observación | Tipo | Referencia |
|---|---|---|---|
| 11:30 | El botón **Remove** no quita el producto desde `/inventory.html`. | Bug | BUG-INV-001 |
| 11:30 | No se pueden agregar al carrito 3 de los 6 productos: *Camiseta Sauce Labs Boltombres, Chaqueta polar Sauce Labs y Camiseta (Roja)*. | Bug | BUG-INV-002 |
| 11:32 | Al elegir cualquier orden distinto de **Name (A to Z)** aparece el mensaje de error *"Sorting is broken! This error has been reported to Backtrace"*. | Bug | BUG-INV-003 |
| 11:33 | Se llega a `/checkout-step-one.html` con el carrito vacío. *(Verificar con `standard_user`)* | Bug | BUG-CAR-001 |
| 11:35 | Al cerrar sesión e iniciar con otro usuario, los productos del carrito anterior se mantienen. *(Verificar con `standard_user`)* | Bug | BUG-CAR-002 |
| 11:37 | En `/checkout-step-one.html` no se puede escribir en el campo **Last Name**. | Bug | BUG-CHK-001 |
| 11:39 | El botón **Finish** no realiza ninguna acción con `error_user`. | Bug | BUG-CHK-002 |
| 11:40 | **Desvío:** como Finish falla con `error_user`, se cambió a `standard_user` para comprobar si permite finalizar una compra con el carrito vacío. El sistema lo permite. | Bug | BUG-CAR-003 |

## 5. Resultados

| Métrica | Valor |
|---|---|
| Bugs encontrados | 8 |
| Reproducibles con `standard_user` | [por confirmar: al menos BUG-CAR-003] |
| Preguntas abiertas | 0 |
| Ideas de nuevos casos | 2 (checkout con carrito vacío y estado del carrito entre sesiones) |

**Bugs reportados:** BUG-INV-001, BUG-INV-002, BUG-INV-003, BUG-CAR-001, BUG-CAR-002, BUG-CAR-003, BUG-CHK-001 y BUG-CHK-002.

## 6. Siguientes pasos

- [ ] Convertir los hallazgos en casos formales ([`casos-prueba.md`](casos-prueba.md))
- [x] Reportar los bugs como Issues del proyecto
- [ ] Nueva sesión exploratoria: no se programa, SauceDemo es un entorno de práctica